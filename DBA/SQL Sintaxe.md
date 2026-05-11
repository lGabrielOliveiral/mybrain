---
tags:
  - dba
  - syntax
  - index
  - postgres
---

# ⌨️ Índice de Sintaxe e Ferramentas DBA

Este mapa centraliza toda a sintaxe necessária para operar o banco de dados, desde comandos SQL puros até ferramentas de terminal e utilitários do sistema.

## 🔗 Conexões de Sintaxe

| Ferramenta / Linguagem | Descrição | Link |
| :--- | :--- | :--- |
| **Linguagem SQL** | Sintaxe pura de DDL (Data Definition), DML (Data Manipulation) e consultas avançadas. | [[DBA/SQL DDL-DML\|SQL Puro (DDL/DML)]] |
| **Terminal psql** | Meta-comandos (`\`) exclusivos do cliente interativo para navegação e inspeção rápida. | [[DBA/Comandos psql\|Meta-comandos psql]] |
| **Binários PG** | Ferramentas de sistema do Postgres instaladas no SO para manutenção e backup. | [[DBA/Ferramentas PG Binaries\|Utilitários de Terminal (PG Tools)]] |

---

## 🛠️ Detalhes dos Nós

### [[DBA/SQL DDL-DML|1. SQL Puro]]
Focado na linguagem padrão SQL. Ideal para quando você está dentro de qualquer IDE ou ferramenta de query.
- **Destaques**: `CREATE`, `UPDATE`, `JOINs`, `WINDOW FUNCTIONS`.

### [[DBA/Comandos psql|2. Meta-comandos psql]]
Comandos que só funcionam dentro do terminal `psql`. Facilitam a vida do DBA sem precisar digitar queries longas em tabelas de catálogo.
- **Destaques**: `\dt` (tabelas), `\d+` (detalhes), `\x` (modo expandido).

### [[DBA/Ferramentas PG Binaries|3. PG Tools (Binários do SO)]]
Comandos executados diretamente no shell do Windows/Linux (fora do banco). Essenciais para automação e manutenção pesada.
- **Destaques**: `pg_dump` (backup), `vacuumdb` (limpeza), `pg_ctl` (controle do serviço).

---
> [!tip] Status
> Use a tag `#revisado` para marcar os tópicos que você já domina!
