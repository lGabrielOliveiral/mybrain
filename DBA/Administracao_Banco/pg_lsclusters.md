---
tags:
  - dba
  - postgres
  - ubuntu
  - cluster
---

# pg_lsclusters

Um utilitário exclusivo de distribuições baseadas em Debian/Ubuntu (pacote `postgresql-common`). Ele fornece uma visualização consolidada de todos os clusters PostgreSQL instalados e configurados na máquina, mostrando suas versões, portas, status atual, dono do processo e o diretório de dados.

## Exemplo

```bash
pg_lsclusters
```

**Saída Hipotética:**
```text
Ver Cluster Port Status Owner    Data directory              Log file
14  main    5432 online postgres /var/lib/postgresql/14/main /var/log/postgresql/postgresql-14-main.log
15  test    5433 down   postgres /var/lib/postgresql/15/test /var/log/postgresql/postgresql-15-test.log
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_ctlcluster]]
