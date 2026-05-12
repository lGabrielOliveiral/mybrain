---
tags:
  - dba
  - postgres
  - wal
  - replicacao
---

# pg_receivewal

Faz o stream (fluxo de dados) contínuo dos arquivos WAL (Write-Ahead Logs) do servidor primário para o disco local. Muito usado para criar soluções de Point-in-Time Recovery (PITR) e para servidores standby em arquiteturas sem archive configurado de forma síncrona.

## Exemplo

```bash
pg_receivewal -D /mnt/backups/wal_archive -h localhost -U replicator
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_basebackup]]
