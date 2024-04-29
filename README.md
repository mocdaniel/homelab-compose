# homelab-compose

This repository is the source of the compose stacks run in my Homelab. For details and setups, see below:

- [Traefik](./README.md#traefik)

## Traefik

Traefik serves as reverse-proxy for all workloads running on Docker, across different compose stacks.

> [!IMPORTANT]
> Because I am using the hardened [Chainguard Traefik image](https://images.chainguard.dev/directory/image/traefik/versions), a user `traefik` with uid `65532` needs
> to be created on the Docker host and added to the `docker` group in order for Traefik's [docker provider](https://doc.traefik.io/traefik/providers/docker/) to work.

```console
# useradd --uid 65532 --groups docker --no-create-home traefik
```

Traefik is configured to serve traffic exclusively via HTTPS (on port `443`). Thus, default certificates are configured and should be placed in `.config/tls.{crt,key}`
