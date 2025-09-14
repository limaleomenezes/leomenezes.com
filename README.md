# [leomenezes.com](https://www.leomenezes.com)

This README shows the general step by step to setup a VPS and run a
webserver with **Docker**, **Nginx**, and **Hugo**.

---

## Domain and VPS

I personally recommend to using Cloudflare Registrar. Because they
give with simple setup HTTPS, www redirection, and
[Proxied Records](https://developers.cloudflare.com/dns/proxy-status/#proxied-records).

About VPS services. I think it's a real use case particular choice.
Anyway, below is listed services which I have used and don't have any
trouble.

- [FranTech](https://my.frantech.ca/)
- [Hetzner](https://www.hetzner.com/)
- [Scalahosting](https://www.scalahosting.com/)

---

## Secure Shell

The entry point to manager a server is learn about SSH protocal. I
recommend read with attention this references. They are the most
important ones. You should create an user first.

Main topics to learn about:

- Generate SSH key pair.
- Configure SSH daemon.
- Copy public key to remote server.
- Configure public key authentication.

References:

- [ArchWiki Users and group](https://wiki.archlinux.org/title/Users_and_groups)
- [ArchWiki OpenSSH](https://wiki.archlinux.org/title/OpenSSH)
- [ArchWiki SCP and SFTP](https://wiki.archlinux.org/title/SCP_and_SFTP)
- [Debian Wiki SSH](https://wiki.debian.org/SSH)

---

## Docker

With an user of `sudo`'s group. You can install Docker and enable its
systemd service unit.

Add an alias to always use docker command with sudo. As mentioned in
Debian Wiki, docker group can potentiolly increase vunaribilities.

- [Install Docker Engine on Debian](https://docs.docker.com/engine/install/debian/)
- [ArchWiki Docker](https://wiki.archlinux.org/title/Docker)
- [Debian Wiki Docker](https://wiki.debian.org/Docker)

---

## Nginx and Hugo

For production, purpose the `nginx:stable-alpine` is one ideal docker
image, mainly if having low storage limits. And remember to install
Hugo.

```
sudo docker pull nginx:stable-alpine
```

My website setup process follows this simple steps. Clone the
repository, start the submodules, build one time the website docker
image, and start docker compose.

```
git clone https://github.com/limaleomenezes/leomenezes.com
cd ./leomenezes.com/

git submodule init
git submodule update --remote

hugo

docker build -t leomenezes.com .
docker compose up -d
```
