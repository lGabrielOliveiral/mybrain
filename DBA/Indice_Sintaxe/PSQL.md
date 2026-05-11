---
tags:
  - dba
  - postgres
  - psql
  - cheat-sheet
  - favorito
---

# 🐘 Comandos psql (PostgreSQL)

O `psql` é o terminal interativo para trabalhar com PostgreSQL. Este resumo foca nos meta-comandos (que começam com `\`) e comandos de ambiente.

## 🔍 Navegação e Listagem (Meta-comandos)

| Comando | Descrição |
| :--- | :--- |
| `\l` | Lista todos os bancos de dados. |
| `\c <banco>` | Conecta a um banco de dados específico. |
| `\dt` | Lista todas as tabelas do banco atual. |
| `\d <tabela>` | Descreve a estrutura da tabela (colunas, tipos, índices). |
| `\du` | Lista todos os usuários (roles) e suas permissões. |
| `\dn` | Lista os schemas do banco. |
| `\df` | Lista as funções criadas. |
| `\dv` | Lista as views. |

## ⚙️ Controle de Execução

| Comando | Descrição |
| :--- | :--- |
| `\i <arquivo>` | Executa comandos a partir de um arquivo SQL externo. |
| `\o <arquivo>` | Redireciona a saída dos comandos para um arquivo. |
| `\timing` | Ativa/Desativa a exibição do tempo de execução de cada query. |
| `\watch <segundos>` | Executa a query atual repetidamente a cada X segundos. |
| `\x` | Ativa o modo de exibição expandida (útil para tabelas com muitas colunas). |

## 📝 Comandos Úteis de Terminal

- **Sair do psql**: `\q`
- **Ajuda geral**: `\?`
- **Ajuda de sintaxe SQL**: `\h <comando>` (ex: `\h SELECT`)
- **Editar comando no editor externo**: `\e` (abre o Vim/Notepad com a última query)

## 💡 Dicas de DBA

> [!tip] Consultas de Monitoramento Rápidas
> ```sql
> -- Ver sessões ativas
> SELECT pid, usename, query, state FROM pg_stat_activity WHERE state = 'active';
> 
> -- Tamanho do banco de dados
> SELECT pg_size_pretty(pg_database_size(current_database()));
> ```

---
*Relacionado:* [[DBA/Indice_Sintaxe]]
