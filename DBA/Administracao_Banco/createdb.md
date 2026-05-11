---
tags:
  - dba
  - postgres
  - admin
  - shell
---

# createdb

Wrapper de linha de comando para o comando SQL `CREATE DATABASE`. Permite criar bancos de dados diretamente do shell.

## Sintaxe Basica

```bash
createdb [opcoes] [nome_do_banco] [descricao]
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-U usuario` | Define o usuario de conexao. |
| `-h host` | Define o host do servidor. |
| `-p porta` | Define a porta de conexao. |
| `-O dono` | Define o owner do novo banco. |
| `-T template` | Usa um banco de dados existente como template. |
| `-E encoding` | Define o encoding (ex: `UTF8`). |
| `--locale locale` | Define o locale do banco. |
| `-l locale` | Atalho para `--locale`. |
| `--lc-collate` | Define a collation. |
| `--lc-ctype` | Define a classificacao de caracteres. |
| `--tablespace ts` | Define o tablespace padrao do banco. |

## Exemplos

```bash
# Criar banco simples
createdb -U postgres meu_banco

# Criar banco com owner especifico
createdb -U postgres -O app_user meu_banco

# Criar banco a partir de template
createdb -U postgres -T template_producao meu_banco_staging

# Criar banco com encoding e locale
createdb -U postgres -E UTF8 --locale pt_BR.UTF-8 meu_banco

# Criar banco com descricao
createdb -U postgres meu_banco "Banco principal da aplicacao"
```

## Equivalente SQL

```sql
CREATE DATABASE meu_banco
    OWNER app_user
    ENCODING 'UTF8'
    LC_COLLATE 'pt_BR.UTF-8'
    LC_CTYPE 'pt_BR.UTF-8'
    TEMPLATE template0;
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[dropdb]]
