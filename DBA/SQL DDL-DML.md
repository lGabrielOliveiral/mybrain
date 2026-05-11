---
tags:
  - dba
  - sql
  - cheat-sheet
---

# 📝 Sintaxe SQL (Cheat Sheet)

Resumo rápido de comandos essenciais para o dia a dia do DBA.

## DDL (Data Definition Language)
```sql
-- Criar tabela
CREATE TABLE employees (
    id NUMBER PRIMARY KEY,
    name VARCHAR2(100),
    salary NUMBER(10,2)
);

-- Adicionar coluna
ALTER TABLE employees ADD (email VARCHAR2(100));
```

## DML (Data Manipulation Language)
```sql
-- Inserir dados
INSERT INTO employees (id, name, salary) VALUES (1, 'John Doe', 5000);

-- Atualizar
UPDATE employees SET salary = salary * 1.1 WHERE id = 1;
```

## Consultas de DBA (Oracle/General)
```sql
-- Verificar sessões ativas
SELECT username, status, machine FROM v$session WHERE status = 'ACTIVE';

-- Espaço em Tablespaces
SELECT tablespace_name, used_space, free_space FROM dba_tablespace_usage_metrics;
```

> [!info]
> Adicione aqui comandos específicos do seu banco (PostgreSQL, Oracle, SQL Server, etc).

---
*Relacionado:* [[DBA/SQL Sintaxe]]
