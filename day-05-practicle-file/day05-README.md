# 🐳 Day 05 — Two-Tier Flask App with Docker Networking

> **30 Days of DevOps Journey** | Day 5 of 30

---

## 📌 What I Built Today

A **Two-Tier Architecture** app using Docker — Flask (backend) + MySQL (database) running as separate containers connected via a custom Docker Network.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────┐
│           Docker Network: two-tier       │
│                                         │
│  ┌─────────────┐      ┌──────────────┐  │
│  │  Flask App  │ ───► │  MySQL DB    │  │
│  │  (port 5000)│      │  (port 3306) │  │
│  └─────────────┘      └──────────────┘  │
└─────────────────────────────────────────┘
```

---

## 🛠️ What I Did

- ✅ Cloned `two-tier-flask-app` from GitHub
- ✅ Built Docker image using `Dockerfile` (Python 3.9-slim base)
- ✅ Created custom Docker Network (`two-tier`)
- ✅ Ran MySQL container on the same network
- ✅ Ran Flask app container with environment variables for DB connection
- ✅ Verified app at `localhost:5000`
- ✅ Confirmed messages stored in MySQL using `SELECT * FROM messages`

---

## 📂 Project Structure

```
two-tier-flask-app/
├── app.py                  # Flask application
├── Dockerfile              # Docker image for Flask
├── Dockerfile-multistage   # Multi-stage build version
├── docker-compose.yml      # Compose setup
├── templates/              # HTML templates
├── k8s/                    # Kubernetes manifests
└── eks-manifests/          # AWS EKS manifests
```

---

## ⚙️ Commands Used

### 1. Clone the repo
```bash
git clone https://github.com/LondheShubham153/two-tier-flask-app.git
cd two-tier-flask-app
```

### 2. Build Docker image
```bash
docker build -t two-tire-backend .
```

### 3. Create custom network
```bash
docker network create two-tier
```

### 4. Run MySQL container
```bash
docker run -d --name mysql \
  --network two-tier \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=devops \
  mysql
```

### 5. Run Flask app container
```bash
docker run -d -p 5000:5000 \
  --network two-tier \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=root \
  -e MYSQL_DB=devops \
  two-tire-backend:latest
```

### 6. Verify running containers
```bash
docker ps
docker network inspect two-tier
```

---

## 🌐 App Output

The Flask app ran successfully at `http://localhost:5000`

Messages entered in the UI were saved to MySQL and confirmed via:
```sql
use devops;
select * from messages;
```

| id | message |
|----|---------|
| 1  | hello |
| 2  | this is output |
| 3  | flask app or mysql are connecting in same network |

---

## 💡 Key Concepts Learned

| Concept | Description |
|--------|-------------|
| Docker Networking | Containers communicate via custom bridge network |
| Environment Variables | DB credentials passed via `-e` flags |
| Two-Tier Architecture | Frontend/Backend separated into different containers |
| Container Logs | Debugging using `docker logs <container_id>` |
| Network Inspect | `docker network inspect` to verify connections |

---

## 📅 Journey Progress

| Day | Topic | Status |
|-----|-------|--------|
| Day 01 | Linux Basics | ✅ Done |
| Day 02 | Git & GitHub | ✅ Done |
| Day 03 | Docker Basics | ✅ Done |
| Day 04 | Docker Advanced (Multi-stage, Security) | ✅ Done |
| Day 05 | Docker Networking + Two-Tier App | ✅ Done |
| Day 06 | Coming next... | 🔜 |

---

## 🔗 Resources

- [TrainWithShubham - Docker In One Shot](https://www.youtube.com/@TrainWithShubham)
- [Original Project Repo](https://github.com/LondheShubham153/two-tier-flask-app)

---

> *Consistency > Perfection. Small steps every day = Big results.* 🚀
