---
tags:
  - dba
  - postgres
  - instalacao
  - revisado
---

# pg_config

Fornece informações detalhadas sobre a instalação atual do PostgreSQL, incluindo a versão exata, diretórios de binários e bibliotecas, as flags de compilação usadas e caminhos de documentação. Muito utilizado por scripts de instalação de módulos e extensões.

## 🎯 Casos de Uso

1. **Compilar e Instalar Extensões:** Ferramentas e bibliotecas externas (como PostGIS ou plugins em C customizados) usam o `pg_config --pgxs` para saber onde estão os cabeçalhos (`headers`) necessários para compilar o código-fonte de forma perfeitamente compatível com a sua versão instalada.
2. **Descobrir caminhos absolutos do sistema:** Em servidores Linux modificados onde o PostgreSQL foi compilado do zero ou instalado em diretórios não convencionais (como `/opt/postgres`), o `pg_config` é a forma oficial de encontrar a pasta real de `binários` (`--bindir`) ou de `bibliotecas dinâmicas` (`--libdir`).
3. **Auditoria de Build (Compilação):** Saber com quais flags o servidor foi compilado originalmente. Por exemplo, você pode descobrir se a instalação atual teve suporte embutido a OpenSSL ou LLVM rodando a flag `--configure`.

## ⚙️ Opções Completas (Parâmetros)

Ao rodar `pg_config` sozinho, ele retornará uma lista com **todas** as variáveis. Para retornar apenas um valor, utilize as opções abaixo:

| Flag                    | Descrição                                                                          |
| :---------------------- | :--------------------------------------------------------------------------------- |
| `--bindir`              | Diretório dos executáveis (ex: psql, pg_dump).                                     |
| `--docdir`              | Diretório dos arquivos de documentação geral.                                      |
| `--htmldir`             | Diretório da documentação em formato HTML.                                         |
| `--includedir`          | Diretório dos arquivos de cabeçalho C (headers) para clientes.                     |
| `--pkgincludedir`       | Diretório de outros cabeçalhos C internos.                                         |
| `--includedir-server`   | Diretório dos cabeçalhos C para desenvolvimento focado no servidor.                |
| `--libdir`              | Diretório das bibliotecas de código (libs compartilhadas).                         |
| `--pkglibdir`           | Diretório de módulos dinâmicos (onde ficam as extensões `.so` ou `.dll`).          |
| `--localedir`           | Diretório de suporte a internacionalização (locales/idiomas).                      |
| `--mandir`              | Diretório das páginas de manual (`man` do Linux).                                  |
| `--sharedir`            | Diretório para arquivos de suporte independentes de arquitetura.                   |
| `--sysconfdir`          | Diretório dos arquivos de configuração globais do sistema.                         |
| `--pgxs`                | Caminho do *Extension Makefile* (PGXS), usado ao compilar extensões usando `make`. |
| `--configure`           | Opções e flags passadas ao script `./configure` quando o Postgres foi compilado.   |
| `--cc`, `--cflags`, etc | Retornam as opções exatas de compilação em C, C++ e linker (`LDFLAGS`).            |
| `--version`             | Retorna a versão principal e minoritária do PostgreSQL instalado.                  |

## 💻 Exemplos

### 1. Consultando o Makefile de Extensões (PGXS)
Muitos tutoriais de instalação de extensões pelo código-fonte precisam que você passe o caminho do seu `pg_config` no terminal antes de dar `make`:
```bash
make USE_PGXS=1 PG_CONFIG=/usr/pgsql-15/bin/pg_config
```
Descobrindo apenas o caminho isolado do PGXS:
```bash
pg_config --pgxs
# Saída Hipotética: /usr/pgsql-15/lib/pgxs/src/makefiles/pgxs.mk
```

### 2. Verificando as Opções de Compilação
Se você quer saber se seu binário do Postgres no Linux possui suporte a Systemd, OpenSSL, ou Python nativo:
```bash
pg_config --configure
# Saída Hipotética: '--build=x86_64-redhat-linux-gnu' '--with-systemd' '--with-openssl' '--with-python'
```

---
*Relacionado:* [[Ferramentas PG Binaries]]
