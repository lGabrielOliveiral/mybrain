---
tags:
  - dba
  - postgres
  - backup
  - shell
---

# pg_restore

Utilitario de linha de comando para restaurar backups do PostgreSQL gerados pelo [[pg_dump]] em formato custom (`-Fc`), directory (`-Fd`) ou tar (`-Ft`). Nao funciona com dumps em formato plain SQL (para esses, usar `psql -f`).

## Sintaxe Basica

```bash
pg_restore [opcoes] [arquivo_de_backup]
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-d banco` | Banco de dados de destino para a restauracao. |
| `-U usuario` | Define o usuario de conexao. |
| `-h host` | Define o host do servidor. |
| `-p porta` | Define a porta de conexao. |
| `-C` | Cria o banco de dados antes de restaurar. |
| `-c` / `--clean` | Executa DROP dos objetos antes de recria-los. |
| `--if-exists` | Adiciona IF EXISTS aos comandos DROP (usar com `-c`). |
| `-n schema` | Restaura apenas o schema especificado. |
| `-t tabela` | Restaura apenas a tabela especificada. |
| `-j N` | Numero de jobs paralelos para restauracao. |
| `--no-owner` | Nao restaura ownership dos objetos. |
| `--no-privileges` | Nao restaura permissoes GRANT/REVOKE. |
| `--data-only` | Restaura apenas os dados, sem estrutura. |
| `--schema-only` | Restaura apenas a estrutura, sem dados. |
| `-l` | Lista o conteudo do arquivo de backup (Table of Contents). |
| `-L listfile` | Restaura apenas os itens listados no arquivo. |
| `-v` | Modo verbose. |

## Exemplos

```bash
# Restaurar backup custom em banco existente
pg_restore -U postgres -d meu_banco backup.dump

# Restaurar criando o banco automaticamente
pg_restore -U postgres -C -d postgres backup.dump

# Restaurar com limpeza previa (DROP + CREATE)
pg_restore -U postgres -d meu_banco -c --if-exists backup.dump

# Restauracao paralela (4 jobs)
pg_restore -U postgres -d meu_banco -j 4 backup.dump

# Listar conteudo do backup
pg_restore -l backup.dump

# Restaurar apenas uma tabela
pg_restore -U postgres -d meu_banco -t clientes backup.dump

# Restauracao seletiva com listfile
pg_restore -l backup.dump > toc.list
# (editar toc.list removendo linhas indesejadas)
pg_restore -U postgres -d meu_banco -L toc.list backup.dump
```

> [!tip] Restauracao Seletiva
> Use `-l` para gerar a lista de conteudo, edite o arquivo removendo o que nao deseja restaurar, e use `-L` para aplicar apenas os itens restantes.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_dump]] | [[pg_dumpall]]
