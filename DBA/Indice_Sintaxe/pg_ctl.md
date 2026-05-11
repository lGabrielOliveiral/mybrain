---
tags:
  - dba
  - postgres
  - servidor
  - shell
---

# pg_ctl

Utilitario para controlar o ciclo de vida do servidor PostgreSQL. Permite iniciar, parar, reiniciar, recarregar configuracoes e verificar o status da instancia.

## Sintaxe Basica

```bash
pg_ctl <acao> [opcoes]
```

## Acoes Disponiveis

| Acao | Descricao |
| :--- | :--- |
| `start` | Inicia o servidor PostgreSQL. |
| `stop` | Para o servidor. |
| `restart` | Para e reinicia o servidor. |
| `reload` | Recarrega os arquivos de configuracao (`postgresql.conf`, `pg_hba.conf`) sem parar o servidor. |
| `status` | Exibe se o servidor esta rodando e o PID do processo. |
| `promote` | Promove um standby replica a servidor primario. |
| `logrotate` | Rotaciona o arquivo de log do servidor. |
| `init` / `initdb` | Inicializa um novo data directory. |

## Opcoes Principais

| Opcao | Descricao |
| :--- | :--- |
| `-D datadir` | Caminho do data directory do cluster. |
| `-l logfile` | Arquivo de log para redirecionar a saida do servidor. |
| `-m modo` | Modo de parada: `smart` (aguarda conexoes), `fast` (desconecta clientes), `immediate` (mata processos). |
| `-w` | Aguarda a conclusao da acao antes de retornar. |
| `-W` | Nao aguarda (retorna imediatamente). |
| `-t segundos` | Tempo maximo de espera (padrao: 60s). |
| `-o opcoes` | Opcoes adicionais passadas diretamente ao processo `postgres`. |

## Modos de Parada

| Modo | Comportamento |
| :--- | :--- |
| `smart` | Aguarda todas as conexoes se desconectarem. Pode demorar indefinidamente. |
| `fast` | Desconecta todos os clientes e faz shutdown graceful. Padrao recomendado. |
| `immediate` | Mata todos os processos imediatamente. Requer recovery na proxima inicializacao. |

## Exemplos

```bash
# Iniciar o servidor
pg_ctl start -D /var/lib/postgresql/16/main -l /var/log/postgresql/server.log

# Parar o servidor (modo fast)
pg_ctl stop -D /var/lib/postgresql/16/main -m fast

# Reiniciar
pg_ctl restart -D /var/lib/postgresql/16/main -m fast

# Recarregar configuracao sem downtime
pg_ctl reload -D /var/lib/postgresql/16/main

# Verificar status
pg_ctl status -D /var/lib/postgresql/16/main

# Promover replica a primario
pg_ctl promote -D /var/lib/postgresql/16/main

# Inicializar novo data directory
pg_ctl initdb -D /var/lib/postgresql/16/novo_cluster
```

> [!important] Variavel PGDATA
> Se a variavel de ambiente `PGDATA` estiver definida, nao e necessario informar `-D` em cada comando.

---
*Relacionado:* [[Ferramentas PG Binaries]] 
