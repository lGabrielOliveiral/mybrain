---
tags:
  - dba
  - postgres
  - shell
  - tools
---

# Utilitarios de Terminal (PG Binaries)

Estes comandos sao executados diretamente no prompt de comando (shell) do sistema operacional, e nao dentro do SQL. Cada ferramenta possui uma nota dedicada com detalhes de uso.

## Backup e Restauracao

Ferramentas para criar copias de seguranca e restaurar bancos de dados ou clusters inteiros.

| Ferramenta | Descricao | Nota |
| :--- | :--- | :--- |
| `pg_dump` | Gera backup logico de um unico banco de dados em diversos formatos (plain, custom, directory, tar). | [[pg_dump]] |
| `pg_dumpall` | Gera backup completo do cluster, incluindo todos os bancos, roles e tablespaces. | [[pg_dumpall]] |
| `pg_restore` | Restaura backups gerados em formato custom ou tar pelo `pg_dump`. | [[pg_restore]] |

## Manutencao e Administracao

Ferramentas para manter a saude do banco: limpeza de dead tuples, reconstrucao de indices e gestao de bancos.

| Ferramenta | Descricao | Nota |
| :--- | :--- | :--- |
| `vacuumdb` | Executa VACUUM e ANALYZE via shell, sem precisar abrir o `psql`. | [[vacuumdb]] |
| `reindexdb` | Reconstroi indices corrompidos ou inchados de um banco ou tabela especifica. | [[reindexdb]] |
| `createdb` | Cria um novo banco de dados a partir do shell. | [[createdb]] |
| `dropdb` | Remove um banco de dados a partir do shell. | [[dropdb]] |

## Controle do Servidor

Ferramentas para iniciar, parar, reiniciar o servico e conectar ao terminal interativo.

| Ferramenta | Descricao | Nota |
| :--- | :--- | :--- |
| `pg_ctl` | Controla o ciclo de vida do servidor PostgreSQL (start, stop, restart, reload, status). | [[pg_ctl]] |
| `psql` | Cliente de terminal interativo para executar queries e meta-comandos. | [[PSQL]] |

---

> [!important] Dica de Seguranca
> Sempre teste o `pg_dump` com o parametro `--no-password` se estiver usando scripts de automacao (configurando o arquivo `.pgpass`).

---
*Relacionado:* [[Sintaxe]]
