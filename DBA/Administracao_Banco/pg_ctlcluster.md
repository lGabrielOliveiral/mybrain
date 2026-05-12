---
tags:
  - dba
  - postgres
  - ubuntu
  - controle
---

# pg_ctlcluster

Utilitário exclusivo do `postgresql-common` (Debian/Ubuntu) que funciona como um "wrapper" muito mais fácil e seguro para o `pg_ctl` padrão. Ele interage com o `systemd` e permite iniciar, parar, reiniciar ou recarregar um cluster específico, mesmo se houver várias versões do PostgreSQL rodando no mesmo servidor.

## Exemplos

```bash
# Formato: pg_ctlcluster <versão> <nome_do_cluster> <ação>
pg_ctlcluster 14 main status
pg_ctlcluster 14 main start
pg_ctlcluster 15 test restart
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_lsclusters]] | [[pg_ctl]]
