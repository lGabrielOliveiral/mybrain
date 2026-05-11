---
tags:
  - dba
  - postgres
  - diagnostico
  - internos
---

# pg_controldata

Exibe informações detalhadas sobre o estado de controle do cluster PostgreSQL. Lê o arquivo `global/pg_control`.

## Informações Exibidas

- Versão do catálogo do sistema.
- Estado do banco (shut down, in production, in recovery).
- Último Checkpoint (Location, WAL file).
- System identifier único.
- Configurações de tamanho de bloco e WAL.

## Exemplo de Uso

```bash
pg_controldata -D /var/lib/postgresql/data
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_resetwal]]
