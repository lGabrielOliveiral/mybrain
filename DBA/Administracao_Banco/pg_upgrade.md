---
tags:
  - dba
  - postgres
  - manutencao
---

# pg_upgrade

Ferramenta essencial para atualizar um cluster de banco de dados PostgreSQL de uma versão principal (major version) para outra, evitando a necessidade de um dump/restore tradicional que pode demorar muito tempo.

## Exemplo

```bash
pg_upgrade -b /usr/pgsql-14/bin -B /usr/pgsql-15/bin -d /var/lib/pgsql/14/data -D /var/lib/pgsql/15/data
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
