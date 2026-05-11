---
tags:
  - dba
  - postgres
  - backup
  - replicacao
---

# pg_basebackup

Utilitário para realizar backups físicos (base backups) de um cluster PostgreSQL em execução. É a ferramenta fundamental para configurar réplicas (Standby) e para Point-In-Time Recovery (PITR).

## Sintaxe Básica

```bash
pg_basebackup [opcoes] -D diretorio_destino
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-D /caminho` | Diretório onde o backup será salvo. |
| `-Fp` / `-Ft` | Formato: plain (diretório) ou tar (arquivo compactado). |
| `-X stream` | Inclui os arquivos WAL necessários no backup (recomendado). |
| `-P` | Exibe o progresso do backup. |
| `-R` | Cria o arquivo `standby.signal` e `postgresql.auto.conf` para replicação. |
| `-S slot` | Usa um replication slot específico. |
| `-z` | Compacta a saída (gzip) - use com `-Ft`. |
| `-r rate` | Limita a taxa de transferência (ex: `10M` para 10MB/s). |

## Exemplos

```bash
# Backup simples para iniciar uma réplica
pg_basebackup -h master_ip -D /var/lib/postgresql/data -U replication_user -P -R -X stream

# Backup em formato TAR compactado
pg_basebackup -D /backups/data_backup -Ft -z -X fetch
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_dump]]
