---
tags:
  - dba
  - postgres
  - ubuntu
  - cluster
---

# pg_createcluster

Ferramenta do `postgresql-common` (Debian/Ubuntu) que automatiza a criação de um novo cluster PostgreSQL. Ela executa o `initdb` por baixo dos panos, aloca automaticamente uma nova porta se a padrão (5432) estiver ocupada e gera a estrutura de configuração padronizada do Debian (separando a pasta `/etc/postgresql` do diretório de dados em `/var/lib/postgresql`).

## Exemplo

```bash
# Cria um cluster da versão 15 chamado "homologacao"
pg_createcluster 15 homologacao
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_dropcluster]] | [[initdb]]
