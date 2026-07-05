# 🐳 Docker Flask NGINX MySQL Lab

> Docker Lab 02: Containerizing a Flask application and deploying NGINX & MySQL using Docker Compose with networking and persistent storage.

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python)
![Flask](https://img.shields.io/badge/Flask-3.0.3-black?style=for-the-badge&logo=flask)
![NGINX](https://img.shields.io/badge/NGINX-009639?style=for-the-badge&logo=nginx)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-384d54?style=for-the-badge&logo=docker)

---

# 📖 Project Overview

This lab demonstrates how to containerize a simple Python Flask application using Docker and deploy a local development environment with **NGINX** and **MySQL** using **Docker Compose**.

The project covers:

- Docker Image creation
- Flask containerization
- Docker networking
- Docker volumes
- Docker Compose
- Service connectivity
- Persistent database storage

---

# 🎯 Lab Objectives

## Task 1

- Dockerize a Flask application.
- Build a Docker Image.
- Run the application inside a container.
- Verify the application using curl.

## Task 2

- Deploy NGINX and MySQL using Docker Compose.
- Connect services through a private bridge network.
- Store MySQL data using Docker Volumes.
- Verify service connectivity.

---

# 🛠 Technologies Used

- Docker
- Docker Compose
- Python 3.11
- Flask
- NGINX
- MySQL 8.0

---

# 📂 Project Structure

```text
docker-flask-nginx-mysql-lab/
│
├── app.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yaml
├── README.md
│
└── screenshots/
    ├── 01-project-files.png
    ├── 02-build-and-run.png
    ├── 03-install-docker-compose.png
    ├── 04-compose-deployment.png
    └── 05-connectivity-and-volume.png
```

---

# 🚀 Task 1 - Dockerizing Flask Application

## Build Docker Image

```bash
docker build -t flask-app .
```

---

## Run Container

```bash
docker run -d -p 8080:5000 --name flask-container flask-app
```

---

## Verify Running Container

```bash
docker ps
```

---

## Test Flask Application

```bash
curl http://localhost:8080
```

Expected Output

```text
Hello from Flask running inside Docker! Welcome, DevOps Engineer!
```

---

# 🐳 Dockerfile Explanation

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python","app.py"]
```

| Instruction | Description |
|------------|-------------|
| FROM | Uses the official Python 3.11 Slim image |
| WORKDIR | Sets `/app` as the working directory |
| COPY requirements.txt | Copies dependency file |
| RUN pip install | Installs Flask dependencies |
| COPY . . | Copies project files |
| EXPOSE 5000 | Documents application port |
| CMD | Starts the Flask application |

---

# 🚀 Task 2 - Docker Compose

## Deploy Stack

```bash
docker-compose up -d
```

---

## Verify Running Containers

```bash
docker ps
```

---

## Verify NGINX

```bash
curl http://localhost:8080
```

Expected Output

```text
Welcome to nginx!
```

---

## Verify Service Connectivity

```bash
docker exec -it web_nginx sh
```

```bash
getent hosts mysql_db
```

Example Output

```text
172.xx.xx.xx    mysql_db
```

---

## Verify Docker Volume

```bash
docker volume ls
```

---

# 🌐 Docker Compose Architecture

```text
                 +--------------------+
                 |      Browser       |
                 +---------+----------+
                           |
                        Port 8080
                           |
                    +------v------+
                    |    NGINX     |
                    +------+------+
                           |
                     app-net Network
                           |
                    +------v------+
                    |    MySQL     |
                    +-------------+

                 Persistent Storage
                        │
                        ▼
                  Docker Volume
```

---

# 📸 Screenshots

## Project Files

![Project Files](screenshots/01-project-files.png)

---

## Build Docker Image & Run Flask

![Build](screenshots/02-build-and-run.png)

---

## Install Docker Compose

![Compose](screenshots/03-install-docker-compose.png)

---

## Deploy NGINX & MySQL

![Compose Stack](screenshots/04-compose-deployment.png)

---

## Verify Connectivity & Volume

![Verification](screenshots/05-connectivity-and-volume.png)

---

# 📚 What I Learned

- Building Docker Images
- Writing Dockerfiles
- Containerizing Flask applications
- Docker networking
- Docker bridge networks
- Docker Volumes
- Docker Compose
- Service discovery using Docker DNS
- Container verification using Docker CLI

---

# 👨‍💻 Author

**Mohamed Mosad**

- GitHub: https://github.com/Mohamed-Mosad-98
- LinkedIn: https://www.linkedin.com/in/mohamed-mosad-516aa717b/

---

⭐ If you found this repository useful, consider giving it a Star.
