---
tags:
  - dba
  - postgres
  - wal
  - manutencao
---

# pg_archivecleanup

Ferramenta desenvolvida para ser usada no arquivo `recovery.conf` (ou definições de `restore_command`) de um servidor standby para excluir arquivos WAL antigos e que já foram aplicados. Ajuda a evitar que o diretório de arquivamento cresça infinitamente.

## Exemplo

```bash
pg_archivecleanup /mnt/backups/wal_archive 000000010000000A000000EE
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
