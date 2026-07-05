# Task 1 - Dockerizing Flask Application

## Build Docker Image

```bash
docker build -t flask-app .
```

## List Docker Images

```bash
docker images
```

## Run Flask Container

```bash
docker run -d -p 8080:5000 --name flask-container flask-app
```

## Verify Running Containers

```bash
docker ps
```

## Test Flask Application

```bash
curl http://localhost:8080
```

## Stop Container

```bash
docker stop flask-container
```

## Remove Container

```bash
docker rm flask-container
```
