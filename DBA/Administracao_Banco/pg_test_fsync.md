---
tags:
  - dba
  - postgres
  - performance
---

# pg_test_fsync

Ferramenta para testar qual método de sincronização de disco (`fsync`) é o mais rápido no seu sistema operacional e hardware.

## Utilidade
Ajuda o DBA a escolher o valor ideal para o parâmetro `wal_sync_method` no `postgresql.conf`.

## Exemplo de Uso

```bash
pg_test_fsync -f arquivo_teste -s 5
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
