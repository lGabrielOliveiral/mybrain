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
| `pg_upgrade` | Atualiza clusters do PostgreSQL entre versões principais (major versions). | [[pg_upgrade]] |

## Diagnóstico e Performance

Ferramentas para monitoramento de conexão e testes de carga.

| Ferramenta | Descrição | Nota |
| :--- | :--- | :--- |
| `pg_isready` | Verifica o status da conexão com o servidor. | [[pg_isready]] |
| `pgbench` | Executa testes de benchmarking e carga no banco. | [[pgbench]] |
| `pg_test_fsync` | Testa o desempenho de sincronização de disco (fsync). | [[pg_test_fsync]] |
| `pg_test_timing` | Mede o overhead de tempo do sistema no servidor. | [[pg_test_timing]] |

## Internos e Recuperação

Comandos de baixo nível para gerenciamento de arquivos e recuperação de desastres.

| Ferramenta | Descrição | Nota |
| :--- | :--- | :--- |
| `pg_controldata` | Exibe informações de controle do cluster (estado, checkpoint). | [[pg_controldata]] |
| `pg_checksums` | Ativa, desativa ou verifica checksums de dados no cluster. | [[pg_checksums]] |
| `pg_rewind` | Sincroniza um diretório de dados com outro (failback). | [[pg_rewind]] |
| `pg_resetwal` | Reseta o Write-Ahead Log (WAL) - **Uso de emergência**. | [[pg_resetwal]] |
| `pg_waldump` | Lê e exibe o conteúdo dos arquivos de Write-Ahead Log (WAL). | [[pg_waldump]] |
| `pg_receivewal` | Faz stream contínuo de arquivos WAL do servidor para o disco local. | [[pg_receivewal]] |
| `pg_recvlogical` | Controla e recebe fluxos de replicação lógica (logical decoding). | [[pg_recvlogical]] |
| `pg_archivecleanup` | Limpa arquivos WAL antigos de arquivos de archive. | [[pg_archivecleanup]] |
| `pg_standby` | Utilitário de suporte para criar um servidor warm standby. | [[pg_standby]] |
| `oid2name` | Mapeia OIDs internos de objetos em nomes reais de arquivos. | [[oid2name]] |

## Controle do Servidor

Ferramentas para gerenciar o serviço e o terminal interativo.

| Ferramenta | Descrição                                                   | Nota       |
| :--------- | :---------------------------------------------------------- | :--------- |
| `pg_ctl`   | Controla o ciclo de vida do servidor (start, stop, status). | [[pg_ctl]] |
| `psql`     | Cliente de terminal interativo para SQL e meta-comandos.    | [[PSQL]]   |
| `initdb`   | Inicializa um novo diretório de dados (cluster).            | [[initdb]] |
| `postgres` | O executável principal do motor do servidor de banco de dados. | [[postgres]] |
| `pg_config`| Fornece informações sobre a instalação (versão, caminhos, compilação). | [[pg_config]] |

## Gerenciamento de Clusters (Debian/Ubuntu)

Estes comandos não fazem parte dos binários padrão (source) do PostgreSQL, mas são instalados pelo pacote `postgresql-common` em distribuições baseadas em Debian e Ubuntu (como o Ubuntu Server). Eles atuam como um "wrapper" focado em facilitar o gerenciamento de múltiplos clusters e versões rodando na mesma máquina simultaneamente.

| Ferramenta | Descrição | Nota |
| :--- | :--- | :--- |
| `pg_lsclusters` | Lista todos os clusters PostgreSQL configurados no sistema. | [[pg_lsclusters]] |
| `pg_ctlcluster` | Alternativa ao pg_ctl, controla o serviço de um cluster específico. | [[pg_ctlcluster]] |
| `pg_createcluster` | Inicializa um novo cluster PostgreSQL vinculando portas e configs. | [[pg_createcluster]] |
| `pg_dropcluster` | Remove completamente um cluster e todos os seus dados. | [[pg_dropcluster]] |

---

> [!important] Dica de Segurança
> Sempre teste o `pg_dump` com o parâmetro `--no-password` se estiver usando scripts de automação (configurando o arquivo `.pgpass`).

---
*Relacionado:* [[DBA/Administracao_Banco]]
