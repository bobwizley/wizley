# CLAUDE.md

This project is a static personal page served from `nginx:alpine` (see `README.md` for build/preview). It is a stateless, secret-free **application stack** on the CodeLab VPS.

## Platform contract

- The deploy action must be a full Gitea URL. On deploy, the workflow builds and pushes the image, then calls the shared `deploy-stack` action. The action renders the host `.env`, rsyncs `compose.yml` to `/opt/compose/wizley/`, and runs `docker compose up -d`.
- `traefik-public` is external and platform-owned. Never invent a new network. A stack-local network can't reach Traefik.
- The project owns its own zone and serves the apex, redirecting `www.` inline in `compose.yml`. It does not use the platform's wildcard-subdomain pattern.
- This repo carries the Gitea topic `codelab-stack` so it appears in the derived stack inventory.

Canonical contract (networks, middlewares, the deploy action, the stack template) lives in [codelab-infra](https://git.codelab.tec.br/codelab/infra) (`CONTEXT.md`, `docs/adr/`, `templates/stack/`). When in doubt, read codelab-infra.
