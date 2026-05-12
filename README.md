# wizley.com.br

Static personal page served from `nginx:alpine`.

## Local preview

```sh
docker build -t wizley:dev . && docker run --rm -p 8080:80 wizley:dev
# open http://localhost:8080
```

## Deploy

Push to `main` → Gitea Actions builds the image, pushes `registry.codelab.tec.br/vctrtvfrrr/wizley:{sha,latest}`, and recreates the container on the host (`/opt/compose/wizley`).
