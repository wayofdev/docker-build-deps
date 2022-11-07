<br>

<div align="center">
<img width="456" src="https://raw.githubusercontent.com/wayofdev/docker-build-deps/master/assets/logo.gh-light-mode-only.png#gh-light-mode-only">
<img width="456" src="https://raw.githubusercontent.com/wayofdev/docker-build-deps/master/assets/logo.gh-dark-mode-only.png#gh-dark-mode-only">
</div>

<br>

<br>

<div align="center">
<a href="https://actions-badge.atrox.dev/wayofdev/docker-build-deps/goto"><img alt="Build Status" src="https://img.shields.io/endpoint.svg?url=https%3A%2F%2Factions-badge.atrox.dev%2Fwayofdev%2Fdocker-build-deps%2Fbadge&style=flat-square"/></a>
<a href="https://github.com/wayofdev/docker-build-deps/tags"><img src="https://img.shields.io/github/v/tag/wayofdev/docker-build-deps?sort=semver&style=flat-square" alt="Latest Version"></a>
<a href="https://hub.docker.com/repository/docker/wayofdev/build-deps"><img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/wayofdev/build-deps?style=flat-square"></a>
<a href="LICENSE"><img src="https://img.shields.io/github/license/wayofdev/docker-build-deps.svg?style=flat-square&color=blue" alt="Software License"/></a>
<a href="#"><img alt="Commits since latest release" src="https://img.shields.io/github/commits-since/wayofdev/docker-build-deps/latest?style=flat-square"></a>
</div>

<br>

# Docker Image: Build Dependencies

Repository contains docker image with build dependencies for WOD projects.

Installed and enabled packages in this image:

| Package                                                      | Type | Description                                                  |
| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| git                                                          | apk  |                                                              |
| bash                                                         | apk  |                                                              |
| unzip                                                        | apk  |                                                              |
| nano                                                         | apk  |                                                              |
| ca-certificates                                              | apk  |                                                              |
| tzdata                                                       | apk  |                                                              |
| curl                                                         | apk  |                                                              |
| bash                                                         | apk  |                                                              |
| gettext (envsubst)                                           | apk  |                                                              |
| make                                                         | apk  |                                                              |
| tar                                                          | apk  |                                                              |
| bzip2                                                        | apk  |                                                              |
| net-tools                                                    | apk  | Linux networking base tools                                  |
| [goss](https://goss.rocks/)                                  | bin  | Quick and Easy server testing / validation                   |
| [dgoss](https://github.com/aelsabbahy/goss/tree/master/extras/dgoss) | bin  | Wrapper around goss to perform tests on docker containers    |
| [dcgoss](https://github.com/aelsabbahy/goss/blob/master/extras/dcgoss/dcgoss) | bin  | Uses docker-compose file instead of passing docker run args  |
| [wait4x](https://github.com/atkrad/wait4x)                   | bin  | Allows to wait for a port or a service to enter the requested state |
| [mkcert](https://github.com/FiloSottile/mkcert)              | bin  | A simple zero-config tool to make locally trusted development certificates with any names |

<br>

If you **like/use** this repository, please consider **starring** it. Thanks!

<br>

## 🔧 Configuration

Ansible is used to generate distribution files. To add or remove packages, or configure project, see [group_vars/all.yml](https://github.com/wayofdev/docker-build-deps/blob/master/src/group_vars/all.yml)

**Default package configuration:**

```yaml
docker_version: "20.10.21"

system_packages:
  - git
  - bash
  - unzip
  - nano
  - ca-certificates
  - tzdata
  - curl
  - bash
  - gettext
  - make
  - tar
  - gzip
  - bzip2
  - gnupg
  - net-tools

system_user: wod
system_group: wod
system_user_uid: 1000
system_user_gid: 1000
system_shell: bash

goss_version: "0.3.20"
```

<br>

To generate dist files use ansible command:

```bash
$ make generate
```

<br>

## ⚙️ Development

To install dependencies and start development you can check contents of our `Makefile`

### →  Requirments

For testing purposes we use **goss** and **dgoss**, follow installation instructions on  [their official README](https://github.com/aelsabbahy/goss/blob/master/extras/dgoss/README.md)

<br>

### → Building locally

Generating distributable Dockerfiles from yaml source code:

```bash
$ make generate
```

<br>

Building default image:

```bash
$ git clone git@github.com:wayofdev/docker-build-deps.git
$ make build
```

To **build** image, **test** it and then **clean** temporary files run:

```bash
$ make
```

<br>

## 🧪 Testing

You can check `Makefile` to get full list of commands for local testing. For testing you can use these comands to test whole role or separate tasks:

Testing default image:

```bash
$ make test
```

<br>

### → Code quality tools

Run **yamllint** to validate all yaml files in project:

```bash
$ make lint
```

Run hadolint to validate created Dockerfiles:

```bash
$ make hadolint
```

<br>

## 🤝 License

[![Licence](https://img.shields.io/github/license/wayofdev/docker-build-deps?style=for-the-badge&color=blue)](./LICENSE)

<br>

## 🙆🏼‍♂️ Author Information

This repository was created in **2022** by [lotyp / wayofdev](https://github.com/wayofdev).

<br>

## 🫡 Contributors

<img align="left" src="https://img.shields.io/github/contributors-anon/wayofdev/docker-build-deps?style=for-the-badge"/>

<a href="https://github.com/wayofdev/docker-nginx/graphs/contributors">
  <img src="https://opencollective.com/wod/contributors.svg?width=890&button=false">
</a>

<br>

