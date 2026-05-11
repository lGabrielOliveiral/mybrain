---
tags:
  - dba
  - postgres
  - admin
  - shell
---

# dropdb

Wrapper de linha de comando para o comando SQL `DROP DATABASE`. Remove um banco de dados diretamente do shell. Operacao irreversivel.

## Sintaxe Basica

```bash
dropdb [opcoes] nome_do_banco
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-U usuario` | Define o usuario de conexao. |
| `-h host` | Define o host do servidor. |
| `-p porta` | Define a porta de conexao. |
| `-i` / `--interactive` | Pede confirmacao antes de executar. |
| `--if-exists` | Nao gera erro se o banco nao existir. |
| `-f` / `--force` | Desconecta sessoes ativas antes de remover (PostgreSQL 13+). |

## Exemplos

```bash
# Remover banco
dropdb -U postgres meu_banco

# Remover com confirmacao interativa
dropdb -U postgres -i meu_banco

# Remover sem erro se nao existir
dropdb -U postgres --if-exists meu_banco

# Forcar desconexao de sessoes ativas e remover
dropdb -U postgres --force meu_banco
```

## Equivalente SQL

```sql
DROP DATABASE IF EXISTS meu_banco WITH (FORCE);
```

> [!danger] Irreversivel
> O `dropdb` remove permanentemente o banco e todos os seus dados. Sempre faca um [[pg_dump]] antes de executar em producao.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[createdb]]
