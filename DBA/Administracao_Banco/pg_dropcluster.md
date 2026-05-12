---
tags:
  - dba
  - postgres
  - ubuntu
  - cluster
---

# pg_dropcluster

Ferramenta destrutiva do pacote `postgresql-common` (Debian/Ubuntu). Ela desliga o cluster (se estiver rodando) e apaga completamente seu diretório de dados, os arquivos de configuração em `/etc/postgresql` e remove sua entrada dos registros do sistema. 

> [!danger] Perda de Dados
> Diferente de dar um `DROP DATABASE` via SQL, o `pg_dropcluster` destrói **toda a instância** (todos os bancos de dados daquele cluster, todas as roles configuradas e todos os tablespaces associados).

## Exemplo

```bash
# Apaga completamente o cluster "homologacao" da versão 15
pg_dropcluster 15 homologacao --stop
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_createcluster]]
