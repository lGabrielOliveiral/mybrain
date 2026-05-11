---
tags:
  - dba
  - postgres
  - performance
  - benchmarking
---

# pgbench

Ferramenta de benchmarking para executar testes de performance no PostgreSQL. Realiza milhares de transações simulando múltiplos clientes.

## Fluxo de Uso

1. **Inicialização**: Cria as tabelas de teste (`pgbench_accounts`, etc).
   ```bash
   pgbench -i -s 10 meu_banco
   ```
   *Note: `-s` é o scale factor (1 = ~16MB).*

2. **Execução**: Roda o teste.
   ```bash
   pgbench -c 10 -j 2 -t 1000 meu_banco
   ```

## Opções Principais

| Opção | Descrição |
| :--- | :--- |
| `-c` | Número de clientes simultâneos. |
| `-j` | Número de threads de execução. |
| `-t` | Número de transações por cliente. |
| `-T` | Tempo de duração do teste em segundos. |
| `-S` | Executa apenas SELECTs (read-only). |

---
*Relacionado:* [[Ferramentas PG Binaries]]
