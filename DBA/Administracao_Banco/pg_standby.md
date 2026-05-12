---
tags:
  - dba
  - postgres
  - replicacao
---

# pg_standby

Um pequeno utilitário incluído na suíte PostgreSQL usado em `restore_command` para criar um ambiente de warm standby simples. Nas versões mais recentes, muitas de suas funções foram integradas nativamente na engine principal, mas ainda existe.

## Exemplo

```bash
# Antigamente usado no recovery.conf
restore_command = 'pg_standby /mnt/archive %f %p %r'
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
