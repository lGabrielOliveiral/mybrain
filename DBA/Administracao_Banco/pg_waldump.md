---
tags:
  - dba
  - postgres
  - diagnostico
  - wal
---

# pg_waldump

Ferramenta que converte e exibe o conteúdo binário dos arquivos de Write-Ahead Log (WAL) do PostgreSQL em um formato legível por humanos. É excelente para diagnosticar o que o banco estava executando internamente, investigando corrupções ou lentidão de transações.

## Exemplo

```bash
pg_waldump /var/lib/pgsql/data/pg_wal/000000010000000000000001
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
