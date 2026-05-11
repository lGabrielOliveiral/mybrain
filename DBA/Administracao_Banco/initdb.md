---
tags:
  - dba
  - postgres
  - servidor
---

# initdb

Cria um novo cluster de banco de dados PostgreSQL (inicializa o diretório de dados).

## Sintaxe Básica

```bash
initdb [opcoes] -D /caminho/dados
```

## Opções Principais

| Opção | Descrição |
| :--- | :--- |
| `-E encoding` | Define o encoding padrão (ex: UTF8). |
| `-U usuario` | Define o superuser (padrão: usuário do SO). |
| `--data-checksums` | Ativa checksums de dados (altamente recomendado). |
| `-W` | Solicita senha para o superuser. |

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_ctl]]
