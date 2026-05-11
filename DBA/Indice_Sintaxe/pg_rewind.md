---
tags:
  - dba
  - postgres
  - recuperacao
---

# pg_rewind

Ferramenta para sincronizar um diretório de dados que divergiu de outro diretório (geralmente após um failover). 

## Cenário de Uso
Em uma replicação, se o Master falha e o Slave assume, o antigo Master agora tem dados "divergentes". O `pg_rewind` evita que você precise baixar um backup físico inteiro de novo (pg_basebackup), copiando apenas os blocos alterados.

## Exemplo

```bash
pg_rewind -D /antigo/master --source-server="host=novo_master user=postgres"
```

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[pg_basebackup]]
