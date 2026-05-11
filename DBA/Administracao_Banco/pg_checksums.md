---
tags:
  - dba
  - postgres
  - internos
---

# pg_checksums

Utilitário para ativar, desativar ou verificar checksums de dados em um cluster PostgreSQL desativado.

## O que são Checksums?
Mecanismo para detectar corrupção de dados no disco. Se um bloco é alterado fora do Postgres, o checksum falhará ao ler.

## Comandos

```bash
# Verificar integridade
pg_checksums -D /data/dir --check

# Ativar checksums (requer cluster desligado)
pg_checksums -D /data/dir --enable
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
