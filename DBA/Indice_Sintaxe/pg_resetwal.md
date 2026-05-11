---
tags:
  - dba
  - postgres
  - recuperacao
  - emergencia
---

# pg_resetwal

Ferramenta de **último recurso** para limpar o Write-Ahead Log (WAL) e resetar informações de controle se o banco não iniciar por corrupção nestes arquivos.

> [!danger] Risco de Perda de Dados
> O uso deste comando pode levar a inconsistências e perda de transações. Use apenas quando não houver backups e o banco estiver inacessível.

## Exemplo

```bash
pg_resetwal -D /caminho/dados
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_controldata]]
