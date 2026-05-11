---
tags:
  - dba
  - postgres
  - backup
  - shell
---

# pg_dump

Utilitario de linha de comando para gerar backup logico de um unico banco de dados PostgreSQL. Suporta diversos formatos de saida e permite selecionar objetos especificos (schemas, tabelas).

## Sintaxe Basica

```bash
pg_dump [opcoes] [nome_do_banco]
```

## Formatos de Saida

| Formato | Flag | Descricao |
| :--- | :--- | :--- |
| Plain (SQL) | `-Fp` (padrao) | Gera um script SQL puro. Restaurado com `psql`. |
| Custom | `-Fc` | Formato comprimido e flexivel. Restaurado com [[pg_restore]]. |
| Directory | `-Fd` | Gera um diretorio com arquivos separados por tabela. Suporta paralelismo. |
| Tar | `-Ft` | Formato tar. Restaurado com [[pg_restore]]. |

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-U usuario` | Define o usuario de conexao. |
| `-h host` | Define o host do servidor. |
| `-p porta` | Define a porta de conexao. |
| `-d banco` | Nome do banco (alternativa a informar como argumento posicional). |
| `-n schema` | Exporta apenas o schema especificado. |
| `-t tabela` | Exporta apenas a tabela especificada. |
| `-T tabela` | Exclui a tabela especificada do backup. |
| `--schema-only` | Exporta apenas a estrutura (DDL), sem dados. |
| `--data-only` | Exporta apenas os dados, sem estrutura. |
| `-j N` | Numero de jobs paralelos (somente com `-Fd`). |
| `--no-owner` | Nao inclui comandos de ownership no dump. |
| `--no-privileges` | Nao inclui comandos GRANT/REVOKE. |
| `--clean` | Inclui comandos DROP antes de CREATE. |
| `--if-exists` | Adiciona IF EXISTS aos comandos DROP. |
| `-v` | Modo verbose. |

## Exemplos

```bash
# Backup simples em SQL
pg_dump -U postgres -d meu_banco > backup.sql

# Backup em formato custom (comprimido)
pg_dump -U postgres -Fc -d meu_banco -f backup.dump

# Backup paralelo em diretorio (4 jobs)
pg_dump -U postgres -Fd -j 4 -d meu_banco -f /backups/meu_banco/

# Backup apenas da estrutura de um schema
pg_dump -U postgres -d meu_banco -n public --schema-only -f estrutura.sql

# Backup de uma tabela especifica
pg_dump -U postgres -d meu_banco -t clientes -Fc -f clientes.dump
```

> [!tip] Automacao
> Para scripts automatizados, configure o arquivo `~/.pgpass` com as credenciais. Formato: `host:porta:banco:usuario:senha`.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_restore]] | [[pg_dumpall]]
