---
tags:
  - dba
  - postgres
  - replicacao
---

# pg_recvlogical

Utilitário de terminal que se conecta ao PostgreSQL e gerencia os slots de replicação lógica. Permite iniciar o streaming das mudanças lógicas do banco (logical decoding) capturando os eventos no servidor em formato legível sem precisar de um client complexo.

## Exemplo

```bash
pg_recvlogical -d meubanco --slot test_slot --create-slot
pg_recvlogical -d meubanco --slot test_slot --start -f -
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
