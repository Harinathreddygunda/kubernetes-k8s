# Getting Started App

A simple Node.js/Express app used to practice Docker fundamentals — used alongside [docker-fundamentals](../docker-fundamentals/README.md).

Originally based on Docker's official [getting-started tutorial app](https://github.com/docker/getting-started).

## 📋 Table of Contents
1. [Run Locally (without Docker)](#run-locally-without-docker)
2. [Run with Docker (single-stage)](#run-with-docker-single-stage)
3. [Run with Docker (multi-stage)](#run-with-docker-multi-stage)
4. [Comparing Image Sizes](#comparing-image-sizes)

## Run Locally (without Docker)
```bash
npm install
npm start
# App runs on http://localhost:3000
```

## Run with Docker (single-stage)
```bash
docker build -t getting-started-app:single -f Dockerfile .
docker run -d -p 3000:3000 --name gsa-single getting-started-app:single
```

Check it's running:
```bash
docker ps
docker logs gsa-single
```

Stop and remove:
```bash
docker stop gsa-single
docker rm gsa-single
```

## Run with Docker (multi-stage)
```bash
docker build -t getting-started-app:multistage -f Dockerfile.multistage .
docker run -d -p 3000:3000 --name gsa-ms getting-started-app:multistage
```

## Comparing Image Sizes
```bash
docker images | grep getting-started-app
```
| Build type | Image size |
|---|---|
| Single-stage | *(fill in after build)* |
| Multi-stage | *(fill in after build)* |

## Notes
- Container listens on port `3000` (hardcoded in `src/index.js`) — port mapping only changes the **host** side (`-p 8080:3000`).
- `.dockerignore` excludes `node_modules` from the build context to keep builds fast and images clean.
