---
tags:
  - dba
  - postgres
  - manutencao
  - shell
---

# vacuumdb

Wrapper de linha de comando para os comandos SQL `VACUUM` e `ANALYZE`. Permite executar limpeza de dead tuples e atualizacao de estatisticas.

## Sintaxe Basica

```bash
vacuumdb [opcoes] [nome_do_banco]
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-d banco` | Banco de dados alvo. |
| `-U usuario` | Define o usuario de conexao. |
| `-h host` | Define o host do servidor. |
| `-a` / `--all` | Executa em todos os bancos do cluster. |
| `-t tabela` | Executa apenas na tabela especificada. |
| `-z` / `--analyze` | Executa ANALYZE apos o VACUUM. |
| `-Z` / `--analyze-only` | Executa apenas ANALYZE, sem VACUUM. |
| `-f` / `--full` | Executa VACUUM FULL (reescreve toda a tabela, requer lock exclusivo). |
| `-F` / `--freeze` | Executa VACUUM FREEZE agressivo. |
| `-j N` | Numero de jobs paralelos. |
| `-v` / `--verbose` | Modo verbose. |
| `--min-xid-age N` | Processa apenas tabelas com xid age acima de N. |
| `--min-mxid-age N` | Processa apenas tabelas com multixact age acima de N. |

## Exemplos

```bash
# VACUUM + ANALYZE em um banco
vacuumdb -U postgres -d meu_banco --analyze

# VACUUM em todos os bancos do cluster
vacuumdb -U postgres --all

# VACUUM FULL em uma tabela especifica
vacuumdb -U postgres -d meu_banco -t pedidos --full

# Apenas ANALYZE (atualizar estatisticas)
vacuumdb -U postgres -d meu_banco --analyze-only

# VACUUM paralelo (4 jobs)
vacuumdb -U postgres -d meu_banco -j 4 --analyze
```

> [!warning] VACUUM FULL
> O `--full` reescreve fisicamente a tabela inteira e requer um lock exclusivo (ACCESS EXCLUSIVE). Evite em producao durante horario de pico. Prefira o VACUUM normal para manutencao rotineira.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[reindexdb]]
