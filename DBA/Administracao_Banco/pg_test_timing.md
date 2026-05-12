---
tags:
  - dba
  - postgres
  - diagnostico
---

# pg_test_timing

Utilitário de diagnóstico que mede o overhead de tempo do sistema. Fundamental para determinar quão custoso será o uso contínuo de timestamps, como ao rodar consultas com `EXPLAIN ANALYZE` ou ativar o log de duração (`log_min_duration_statement`).

## 🎯 Casos de Uso

1. **Avaliar impacto de logs de duração:** Antes de ativar o `log_min_duration_statement` em produção, é recomendável rodar esta ferramenta para garantir que a simples medição do tempo não vai estrangular a CPU.
2. **Diagnosticar lentidão em `EXPLAIN ANALYZE`:** Se uma consulta roda rápido, mas fica lenta ao adicionar o `ANALYZE` (que mede o tempo linha a linha da execução), a causa provável é um relógio de sistema (clock source) muito lento.
3. **Validação de infraestrutura virtual/nuvem:** Máquinas virtuais ou containers podem sofrer com fontes de relógio ineficientes. O utilitário ajuda a atestar a qualidade da virtualização.

## 💻 Exemplos e Saídas Hipotéticas

### 1. Teste em um Servidor Rápido (Bom Cenário)

Execução padrão, onde o relógio de hardware (ex: contador TSC no Linux) é altamente eficiente. A esmagadora maioria das medições fica abaixo de 1 microssegundo.

**Comando:**
```bash
pg_test_timing
```

**Saída Hipotética:**
```text
Testing timing overhead for 3 seconds.
Per loop time including overhead: 35.96 ns
Histogram of timing durations:
  < us   % of total      count
     1     98.43215   82123145
     2      1.54210    1286542
     4      0.02511      20950
     8      0.00062        517
    16      0.00002         15
```
**Interpretação:** Mais de 98% das requisições de tempo levaram menos de 1 microssegundo (us) e o tempo médio por iteração foi de cerca de 36 nanosegundos (ns). O overhead de timing neste servidor é imperceptível, então é super seguro ligar logs ou rodar testes complexos.

### 2. Teste em um Servidor Lento (Cenário Problemático)

Ocorre frequentemente em máquinas virtuais mal configuradas ou distros antigas que não possuem acesso direto a contadores de hardware de alta resolução.

**Comando:**
```bash
pg_test_timing
```

**Saída Hipotética:**
```text
Testing timing overhead for 3 seconds.
Per loop time including overhead: 1250.40 ns
Histogram of timing durations:
  < us   % of total      count
     1      0.00000          0
     2     60.15000    1443150
     4     35.25000     845700
     8      4.50000     107955
    16      0.08000       1919
    32      0.02000        479
```
**Interpretação:** O tempo médio de acesso saltou para 1250 nanosegundos (1.2 us). Absolutamente nenhuma iteração completou em menos de 1 us. Em um servidor sob carga processando transações com logs ativos, esse atraso acumulado em milhões de leituras de tempo pode deixar o banco todo devagar.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_test_fsync]]
