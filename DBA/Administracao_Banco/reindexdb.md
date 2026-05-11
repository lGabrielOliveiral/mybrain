---
tags:
  - dba
  - postgres
  - manutencao
  - shell
---

# reindexdb

Wrapper de linha de comando para o comando SQL `REINDEX`. Reconstroi indices corrompidos ou com bloat excessivo.

## Sintaxe Basica

```bash
reindexdb [opcoes] [nome_do_banco]
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-d banco` | Banco de dados alvo. |
| `-U usuario` | Define o usuario de conexao. |
| `-h host` | Define o host do servidor. |
| `-a` / `--all` | Reindeza todos os bancos do cluster. |
| `-t tabela` | Reindeza apenas a tabela especificada. |
| `-i indice` | Reindeza apenas o indice especificado. |
| `-s` / `--system` | Reindeza apenas os catalogos do sistema. |
| `-S schema` | Reindeza apenas o schema especificado. |
| `-j N` | Numero de jobs paralelos. |
| `--concurrently` | Reconstroi indices sem bloquear escritas (PostgreSQL 12+). |
| `-v` / `--verbose` | Modo verbose. |

## Exemplos

```bash
# Reindexar todo um banco
reindexdb -U postgres -d meu_banco

# Reindexar uma tabela especifica
reindexdb -U postgres -d meu_banco -t pedidos

# Reindexar um indice especifico
reindexdb -U postgres -d meu_banco -i idx_pedidos_data

# Reindexar sem bloqueio (concurrently)
reindexdb -U postgres -d meu_banco --concurrently

# Reindexar catalogos do sistema
reindexdb -U postgres -d meu_banco --system

# Reindexar todos os bancos em paralelo
reindexdb -U postgres --all -j 4
```

> [!tip] Quando reindexar
> Indicado apos import massivo de dados, quando indices apresentam bloat significativo, ou apos corrucao de indice. Use `--concurrently` em producao para evitar locks.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[vacuumdb]]
