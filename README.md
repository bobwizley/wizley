# wizley.com.br

Static personal page served from `nginx:alpine`.

## Local preview

```sh
docker build -t wizley:dev . && docker run --rm -p 8080:80 wizley:dev
# open http://localhost:8080
```

## Deploy

Push to `master` → Gitea Actions builds the image, pushes `registry.codelab.tec.br/vctrtvfrrr/wizley:{sha,latest}`, then the shared `deploy-stack` action renders the host `.env`, rsyncs `compose.yml` to `/opt/compose/wizley`, and runs `docker compose up -d`. See `CLAUDE.md` → Platform contract.
