---
tags:
  - dba
  - postgres
  - backup
  - shell
---

# pg_dumpall

Utilitario de linha de comando para gerar backup completo de todo o cluster PostgreSQL. Diferente do [[pg_dump]], exporta todos os bancos de dados, roles, tablespaces e permissoes em um unico script SQL.

## Sintaxe Basica

```bash
pg_dumpall [opcoes]
```

## Diferencas em Relacao ao pg_dump

| Aspecto | pg_dump | pg_dumpall |
| :--- | :--- | :--- |
| Escopo | Um unico banco de dados | Todo o cluster |
| Formato de saida | Plain, custom, directory, tar | Somente plain (SQL) |
| Exporta roles/tablespaces | Nao | Sim |
| Restauracao | `psql` ou [[pg_restore]] | Somente `psql` |

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-U usuario` | Define o usuario de conexao (deve ser superuser). |
| `-h host` | Define o host do servidor. |
| `-p porta` | Define a porta de conexao. |
| `--globals-only` | Exporta apenas roles e tablespaces, sem bancos de dados. |
| `--roles-only` | Exporta apenas as roles (usuarios e grupos). |
| `--tablespaces-only` | Exporta apenas as tablespaces. |
| `--schema-only` | Exporta apenas a estrutura (DDL), sem dados. |
| `--no-role-passwords` | Nao exporta senhas das roles. |
| `--clean` | Inclui comandos DROP antes de CREATE. |
| `-v` | Modo verbose. |

## Exemplos

```bash
# Backup completo do cluster
pg_dumpall -U postgres > full_backup.sql

# Backup apenas das roles (usuarios)
pg_dumpall -U postgres --roles-only > roles.sql

# Backup apenas dos globals (roles + tablespaces)
pg_dumpall -U postgres --globals-only > globals.sql

# Restaurar o backup completo
psql -U postgres -f full_backup.sql
```

> [!warning] Atencao
> O `pg_dumpall` gera saida apenas em formato SQL puro. Para backups grandes, considere usar [[pg_dump]] individualmente por banco em formato custom, combinado com `pg_dumpall --globals-only` para as roles.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_dump]] | [[pg_restore]]
