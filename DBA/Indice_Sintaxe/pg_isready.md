---
tags:
  - dba
  - postgres
  - diagnostico
---

# pg_isready

Utilitário para verificar o status de conexão de um servidor PostgreSQL. Retorna um código de saída indicando se o servidor está aceitando conexões.

## Códigos de Retorno

| Código | Significado |
| :--- | :--- |
| `0` | O servidor está aceitando conexões. |
| `1` | O servidor está rejeitando conexões (ex: inicializando). |
| `2` | Nenhuma resposta do servidor. |
| `3` | Tentativa inválida (erro de parâmetros). |

## Exemplos

```bash
# Verificação simples no localhost
pg_isready

# Verificar servidor remoto com timeout
pg_isready -h 10.0.0.5 -p 5432 -t 5
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_ctl]]
