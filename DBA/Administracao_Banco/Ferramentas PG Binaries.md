---
tags:
  - dba
  - postgres
  - shell
  - tools
---

# Utilitários de Terminal (PG Binaries)

Estes comandos são executados diretamente no prompt de comando (shell) do sistema operacional, e não dentro do SQL. Cada ferramenta possui uma nota dedicada com detalhes de uso.

## Backup e Restauração

Ferramentas para criar cópias de segurança e restaurar bancos de dados ou clusters inteiros.

| Ferramenta      | Descrição                                                         | Nota              |
| :-------------- | :---------------------------------------------------------------- | :---------------- |
| `pg_dump`       | Gera backup lógico de um único banco de dados.                    | [[pg_dump]]       |
| `pg_dumpall`    | Gera backup completo do cluster (roles, tablespaces e bancos).    | [[pg_dumpall]]    |
| `pg_restore`    | Restaura backups gerados em formato custom ou tar pelo `pg_dump`. | [[pg_restore]]    |
| `pg_basebackup` | Realiza backup físico (base backup) para replicação ou PITR.      | [[pg_basebackup]] |

## Manutenção e Administração

Ferramentas para manter a saúde do banco e gerenciar objetos globais.

| Ferramenta | Descrição | Nota |
| :--- | :--- | :--- |
| `vacuumdb` | Executa VACUUM e ANALYZE via shell. | [[vacuumdb]] |
| `reindexdb` | Reconstrói índices corrompidos ou inchados. | [[reindexdb]] |
| `clusterdb` | Reagrupa dados em tabelas com base em um índice. | [[clusterdb]] |
| `createdb` | Cria um novo banco de dados. | [[createdb]] |
| `dropdb` | Remove um banco de dados. | [[dropdb]] |
| `createuser` | Cria uma nova role (usuário) no Postgres. | [[createuser]] |
| `dropuser` | Remove uma role (usuário) existente. | [[dropuser]] |

## Diagnóstico e Performance

Ferramentas para monitoramento de conexão e testes de carga.

| Ferramenta | Descrição | Nota |
| :--- | :--- | :--- |
| `pg_isready` | Verifica o status da conexão com o servidor. | [[pg_isready]] |
| `pgbench` | Executa testes de benchmarking e carga no banco. | [[pgbench]] |
| `pg_test_fsync` | Testa o desempenho de sincronização de disco (fsync). | [[pg_test_fsync]] |

## Internos e Recuperação

Comandos de baixo nível para gerenciamento de arquivos e recuperação de desastres.

| Ferramenta | Descrição | Nota |
| :--- | :--- | :--- |
| `pg_controldata` | Exibe informações de controle do cluster (estado, checkpoint). | [[pg_controldata]] |
| `pg_checksums` | Ativa, desativa ou verifica checksums de dados no cluster. | [[pg_checksums]] |
| `pg_rewind` | Sincroniza um diretório de dados com outro (failback). | [[pg_rewind]] |
| `pg_resetwal` | Reseta o Write-Ahead Log (WAL) - **Uso de emergência**. | [[pg_resetwal]] |

## Controle do Servidor

Ferramentas para gerenciar o serviço e o terminal interativo.

| Ferramenta | Descrição                                                   | Nota       |
| :--------- | :---------------------------------------------------------- | :--------- |
| `pg_ctl`   | Controla o ciclo de vida do servidor (start, stop, status). | [[pg_ctl]] |
| `psql`     | Cliente de terminal interativo para SQL e meta-comandos.    | [[PSQL]]   |
| `initdb`   | Inicializa um novo diretório de dados (cluster).            | [[initdb]] |

---

> [!important] Dica de Segurança
> Sempre teste o `pg_dump` com o parâmetro `--no-password` se estiver usando scripts de automação (configurando o arquivo `.pgpass`).

---
*Relacionado:* [[DBA/Administracao_Banco]]
