# Docker & Container Management – Practical Cheat Sheet

> **Purpose**: Zero-nonsense, copy-paste-ready Docker guide.
> Built for **developers**, **ML engineers**, and **production systems**.
> Optimized for **Python**, **Django**, **AI workloads**, and **secure deployments**.
> Aligned with **OWASP Top 10** and **ISO/IEC 27001:2022**.

---

## 1. Core Concepts (If This Is Fuzzy, Stop and Fix It)

### What Docker Is

* Docker packages applications + dependencies into **containers**
* Containers are **isolated**, **portable**, and **reproducible**

### Key Terms

* **Image**: Blueprint (immutable)
* **Container**: Running instance of an image
* **Dockerfile**: Instructions to build an image
* **Volume**: Persistent storage
* **Network**: Container communication layer

---

## 2. Install & Verify

```bash
docker --version
docker compose version
```

Verify Docker Daemon:

```bash
docker info
```

---

## 3. Images (Blueprint Management)

### List Images

```bash
docker images
```

### Pull Image

```bash
docker pull python:3.11-slim
```

### Remove Image

```bash
docker rmi image_id
```

---

## 4. Containers (Runtime Control)

### Run Container

```bash
docker run python:3.11-slim
```

### Run Interactive

```bash
docker run -it python:3.11-slim bash
```

### List Containers

```bash
docker ps
docker ps -a
```

### Stop / Remove

```bash
docker stop container_id
docker rm container_id
```

---

## 5. Dockerfile (Non-Negotiable Skill)

### Minimal Python Dockerfile

```Dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```

### Build Image

```bash
docker build -t myapp:latest .
```

---

## 6. Best Practices (Do Not Skip)

* Use **slim** or **alpine** images
* Pin dependency versions
* One process per container
* Avoid running as root
* Multi-stage builds

---

## 7. Multi-Stage Build (Production Grade)

```Dockerfile
FROM python:3.11-slim AS builder
WORKDIR /build
COPY requirements.txt .
RUN pip install --user -r requirements.txt

FROM python:3.11-slim
WORKDIR /app
COPY --from=builder /root/.local /root/.local
ENV PATH=/root/.local/bin:$PATH
COPY . .
CMD ["python", "app.py"]
```

---

## 8. Volumes (Persistent Data)

### Create Volume

```bash
docker volume create app_data
```

### Use Volume

```bash
docker run -v app_data:/data myapp
```

---

## 9. Networking (Service Communication)

### Create Network

```bash
docker network create app_net
```

### Run with Network

```bash
docker run --network app_net myapp
```

---

## 10. Docker Compose (Mandatory for Real Apps)

### docker-compose.yml

```yaml
version: "3.9"
services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
    env_file:
      - .env
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: appdb
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

### Run Compose

```bash
docker compose up -d
docker compose down
```

---

## 11. Logs & Debugging

```bash
docker logs container_id
docker exec -it container_id bash
```

---

## 12. Environment Variables (Security Critical)

```bash
docker run -e ENV=prod myapp
```

Never bake secrets into images.

---

## 13. Clean Up (Do This Weekly)

```bash
docker system prune
docker volume prune
```

---

## 14. Security Best Practices (OWASP + ISO)

* Minimal base images
* Non-root users
* Read-only filesystems
* Scan images for CVEs
* Secrets via env or vaults

---

## 15. Docker for Django (Baseline)

```Dockerfile
CMD ["gunicorn", "config.wsgi:application", "--bind", "0.0.0.0:8000"]
```

---

## 16. Common Anti-Patterns (Stop Immediately)

* Huge images (>1GB)
* Running as root
* Hardcoded secrets
* No .dockerignore
* One container doing everything

---

## 17. .dockerignore (Mandatory)

```dockerignore
__pycache__/
.env
.git
.venv
node_modules
```

---

## 18. Emergency Commands (Memorize)

```bash
docker ps
docker logs <id>
docker exec -it <id> bash
docker stop $(docker ps -q)
docker system prune
```

---

## 19. Mental Model

> Containers are **cattle**, not pets.
> Rebuild, do not patch.
> Immutable infrastructure always wins.

---

