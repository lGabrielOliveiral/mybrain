---
tags:
  - dba
  - postgres
  - manutencao
---

# clusterdb

Wrapper para o comando SQL `CLUSTER`. Reorganiza fisicamente os dados de uma tabela com base na ordem de um índice específico.

## Utilidade

Diferente do `VACUUM`, o `CLUSTER` reordena os dados, o que pode melhorar drasticamente a performance de queries que buscam ranges de dados baseados no índice clusterizado.

## Sintaxe e Exemplos

```bash
# Clusterizar todo um banco
clusterdb -d meu_banco

# Clusterizar apenas uma tabela
clusterdb -d meu_banco -t minha_tabela
```

> [!warning] Bloqueio
> O `CLUSTER` exige um lock exclusivo na tabela, impedindo leituras e escritas durante o processo.

---
*Relacionado:* [[Ferramentas PG Binaries]] | [[vacuumdb]]
