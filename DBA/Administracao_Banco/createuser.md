---
tags:
  - dba
  - postgres
  - seguranca
  - admin
---

# createuser

Wrapper de linha de comando para o comando SQL `CREATE ROLE`. Permite criar usuários e roles diretamente do shell.

## Sintaxe Básica

```bash
createuser [opcoes] [usuario]
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-s` | Define o usuário como Superuser. |
| `-d` | Permite ao usuário criar bancos de dados. |
| `-r` | Permite ao usuário criar outras roles. |
| `-l` | Permite ao usuário fazer login (padrão). |
| `-P` | Solicita uma senha para o novo usuário. |
| `-e` | Exibe o comando SQL que está sendo enviado ao servidor. |

## Exemplos

```bash
# Criar usuário simples
createuser -U postgres meu_usuario

# Criar superuser com senha
createuser -s -P -U postgres admin_db
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[dropuser]]
