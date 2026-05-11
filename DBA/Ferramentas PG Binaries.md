---
tags:
  - dba
  - postgres
  - shell
  - tools
---

# 🛠️ Utilitários de Terminal (PG Binaries)

Estes comandos são executados diretamente no prompt de comando (shell) do sistema operacional, e não dentro do SQL.

## 📦 Backup e Restauração

| Comando | Função | Exemplo de Uso |
| :--- | :--- | :--- |
| `pg_dump` | Backup de um único banco de dados. | `pg_dump -U user -d dbname > backup.sql` |
| `pg_dumpall` | Backup de todo o cluster (todos os bancos e usuários). | `pg_dumpall -U postgres > full_backup.sql` |
| `pg_restore` | Restaura backups feitos em formato custom/tar. | `pg_restore -d dbname backup.dump` |

## 🧹 Manutenção e Administração

| Comando | Função | Exemplo de Uso |
| :--- | :--- | :--- |
| `vacuumdb` | Executa limpeza (VACUUM) e análise de estatísticas. | `vacuumdb -d dbname --analyze` |
| `reindexdb` | Recria todos os índices de um banco ou tabela. | `reindexdb -d dbname -t my_table` |
| `createdb` / `dropdb` | Cria ou remove bancos de dados rapidamente. | `createdb -U postgres new_db` |

## ⚙️ Controle do Servidor

| Comando | Função | Exemplo de Uso |
| :--- | :--- | :--- |
| `pg_ctl` | Inicia, para ou reinicia o serviço do Postgres. | `pg_ctl restart -D "C:\caminho\dados"` |
| `psql` | Inicia o terminal interativo (cliente). | `psql -U postgres -d postgres` |

---
> [!important] Dica de Segurança
> Sempre teste o `pg_dump` com o parâmetro `--no-password` se estiver usando scripts de automação (configurando o arquivo `.pgpass`).

---
*Relacionado:* [[DBA/SQL Sintaxe]]
