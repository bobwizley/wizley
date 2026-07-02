# wizley.com.br

Static personal page served from `nginx:alpine`.

## Local preview

```sh
docker build -t wizley:dev . && docker run --rm -p 8080:80 wizley:dev
# open http://localhost:8080
```
