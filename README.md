# haven-lander

A field guide to **Haven Apartments**, 11924 W. Washington Blvd, Culver City — published at https://haven.makeacompany.ai. 97 units, one Airstream on the roof, and the Rodeway Inn (32 rooms) directly across the street. Built as a memorial for the Neighborhood Watch group chat.

## Stack

- `index.html` — vanilla HTML/CSS/JS, Google Fonts (Fraunces + Inter + JetBrains Mono), inline SVG data viz, no build step.
- `Dockerfile` — `nginx:1.27-alpine` serving the file.
- `.github/workflows/build.yml` — builds + pushes `geeemoney/haven-lander:<version>` to Docker Hub on tag.
- Cluster manifests live in [`BimRoss/rancher-admin`](https://github.com/BimRoss/rancher-admin) under `admin/apps/haven/`.

## Releasing

```sh
git tag -a v0.1.0 -m "v0.1.0"
git push origin v0.1.0
# bump the image tag in rancher-admin/admin/apps/haven/deployment.yaml via PR
```

## Local preview

```sh
docker build -t haven-lander . && docker run --rm -p 8080:80 haven-lander
# open http://localhost:8080
```
