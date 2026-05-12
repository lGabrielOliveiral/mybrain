---
tags:
  - dba
  - postgres
  - core
---

# postgres

O executável principal do motor do banco de dados (anteriormente conhecido também como `postmaster`). Embora na maioria das vezes o serviço seja iniciado por ferramentas como `systemd` ou `pg_ctl`, é o `postgres` que roda como processo central e gerencia as conexões e recursos. Em casos de debug severo, pode ser invocado diretamente.

## Exemplo

```bash
# Modo single-user para manutenção extrema:
postgres --single -D /var/lib/pgsql/data meubanco
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_ctl]]
