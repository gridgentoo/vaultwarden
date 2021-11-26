Оригинальный репозиторий  
https://github.com/dani-garcia/vaultwarden

Vaultwarden 1.23.0 (бывший bitwarden_rs), развивающего альтернативную серверную часть для менеджера паролей Bitwarden, совместимую на уровне API и способную работать с официальными клиентами Bitwarden. Целью проекта является предоставление кроссплатформенной реализации, позволяющей запускать сервера Bitwarden на своих мощностях, но в отличие от официального сервера Bitwarden, потребляющих существенно меньше ресурсов.

Код проекта Vaultwarden написан на языке Rust и распространяется под лицензией GPLv3.0. В качестве СУБД поддерживаются PostgreSQL, SQLite и MySQL. Для сравнения официальный сервер Bitwarden написан на языке C# с использованием .NET Core, ASP.NET Core, привязан к MS SQL Server и поставляется под лицензией AGPLv3.0, не допускающей создание сервисов без открытия их кода.

На данный момент Vaultwarden поддерживает практически все возможности Bitwarden API:

поддержка веб-интерфейса;
возможность использования как одиночными пользователями, так и организациями;
настраиваемые права доступа к тем или иным веткам в дереве паролей с поддержкой вложенных файлов;
совместимость с TOTP Bitwarden;
поддержка Vault API;
поддержка U2F, YubiKey и Duo;
поддержка LDAP;
динамическое обновление паролей на пользовательских устройствах.
Поставка в форме готового веб-сервера в Docker-контейнере.
В новой версии отмечаются следующие новшества:

добавлена возможность аварийного (emergency) доступа к базе;
добавлена поддержка выполнения операций управления пользователями в пакетном режиме;
добавлена проверка соединения с базой данных;
добавлено принудительное использование персональной политики при импорте.

### Alternative implementation of the Bitwarden server API written in Rust and compatible with [upstream Bitwarden clients](https://bitwarden.com/download/)*, perfect for self-hosted deployment where running the official resource-heavy service might not be ideal.

📢 Note: This project was known as Bitwarden_RS and has been renamed to separate itself from the official Bitwarden server in the hopes of avoiding confusion and trademark/branding issues. Please see [#1642](https://github.com/dani-garcia/vaultwarden/discussions/1642) for more explanation.

---

[![Docker Pulls](https://img.shields.io/docker/pulls/vaultwarden/server.svg)](https://hub.docker.com/r/vaultwarden/server)
[![Dependency Status](https://deps.rs/repo/github/dani-garcia/vaultwarden/status.svg)](https://deps.rs/repo/github/dani-garcia/vaultwarden)
[![GitHub Release](https://img.shields.io/github/release/dani-garcia/vaultwarden.svg)](https://github.com/dani-garcia/vaultwarden/releases/latest)
[![GPL-3.0 Licensed](https://img.shields.io/github/license/dani-garcia/vaultwarden.svg)](https://github.com/dani-garcia/vaultwarden/blob/master/LICENSE.txt)
[![Matrix Chat](https://img.shields.io/matrix/vaultwarden:matrix.org.svg?logo=matrix)](https://matrix.to/#/#vaultwarden:matrix.org)

Image is based on [Rust implementation of Bitwarden API](https://github.com/dani-garcia/vaultwarden).

**This project is not associated with the [Bitwarden](https://bitwarden.com/) project nor 8bit Solutions LLC.**

#### ⚠️**IMPORTANT**⚠️: When using this server, please report any bugs or suggestions to us directly (look at the bottom of this page for ways to get in touch), regardless of whatever clients you are using (mobile, desktop, browser...). DO NOT use the official support channels.

---

## Features

Basically full implementation of Bitwarden API is provided including:

 * Organizations support
 * Attachments
 * Vault API support
 * Serving the static files for Vault interface
 * Website icons API
 * Authenticator and U2F support
 * YubiKey and Duo support

## Installation
Pull the docker image and mount a volume from the host for persistent storage:

```sh
docker pull vaultwarden/server:latest
docker run -d --name vaultwarden -v /vw-data/:/data/ -p 80:80 vaultwarden/server:latest
```
This will preserve any persistent data under /vw-data/, you can adapt the path to whatever suits you.

**IMPORTANT**: Some web browsers, like Chrome, disallow the use of Web Crypto APIs in insecure contexts. In this case, you might get an error like `Cannot read property 'importKey'`. To solve this problem, you need to access the web vault from HTTPS. 

This can be configured in [vaultwarden directly](https://github.com/dani-garcia/vaultwarden/wiki/Enabling-HTTPS) or using a third-party reverse proxy ([some examples](https://github.com/dani-garcia/vaultwarden/wiki/Proxy-examples)).

If you have an available domain name, you can get HTTPS certificates with [Let's Encrypt](https://letsencrypt.org/), or you can generate self-signed certificates with utilities like [mkcert](https://github.com/FiloSottile/mkcert). Some proxies automatically do this step, like Caddy (see examples linked above).

## Usage
See the [vaultwarden wiki](https://github.com/dani-garcia/vaultwarden/wiki) for more information on how to configure and run the vaultwarden server.

## Get in touch
To ask a question, offer suggestions or new features or to get help configuring or installing the software, please [use the forum](https://vaultwarden.discourse.group/).

If you spot any bugs or crashes with vaultwarden itself, please [create an issue](https://github.com/dani-garcia/vaultwarden/issues/). Make sure there aren't any similar issues open, though!

If you prefer to chat, we're usually hanging around at [#vaultwarden:matrix.org](https://matrix.to/#/#vaultwarden:matrix.org) room on Matrix. Feel free to join us!

### Sponsors
Thanks for your contribution to the project!

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/netdadaltd">
        <img src="https://avatars.githubusercontent.com/u/77323954?s=75&v=4" width="75px;" alt="netdadaltd"/>
        <br />
        <sub><b>netDada Ltd.</b></sub>
      </a>
  </td>
  </tr>
</table>

<br/>

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/Gyarbij" style="width: 75px">
        <sub><b>Chono N</b></sub>
      </a>
    </td>
  </tr>
  <tr>
    <td align="center">
       <a href="https://github.com/themightychris">
        <sub><b>Chris Alfano</b></sub>
      </a>
    </td>
  </tr>
</table>
