---
tags:
  - dba
  - postgres
  - seguranca
  - admin
---

# dropuser

Wrapper de linha de comando para o comando SQL `DROP ROLE`. Remove um usuário ou role do sistema.

## Sintaxe Básica

```bash
dropuser [opcoes] usuario
```

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-i` | Solicita confirmação antes de remover. |
| `-e` | Exibe o comando SQL executado. |
| `-U` | Usuário para conectar (geralmente postgres). |

## Exemplos

```bash
# Remover usuário
dropuser -U postgres meu_usuario

# Remover com confirmação
dropuser -i -U postgres usuario_antigo
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[createuser]]
