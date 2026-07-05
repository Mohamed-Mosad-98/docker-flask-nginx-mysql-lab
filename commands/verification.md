# Verification Commands

## Verify Flask

```bash
curl http://localhost:8080
```

---

## Verify NGINX

```bash
curl http://localhost:8080
```

---

## Verify Docker Images

```bash
docker images
```

---

## Verify Running Containers

```bash
docker ps
```

---

## Verify Docker Volumes

```bash
docker volume ls
```

---

## Verify Docker Networks

```bash
docker network ls
```

---

## Enter NGINX Container

```bash
docker exec -it web_nginx sh
```

---

## Verify Service Discovery

```bash
getent hosts mysql_db
```
