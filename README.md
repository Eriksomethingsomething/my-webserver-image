# Dockerized Web Server

A simple static website hosted with **Nginx and Docker**. This project demonstrates how to build a Docker image, configure a container with Docker Compose, and serve a website locally.

## 📌 Overview

The website runs inside a Docker container using Nginx as its web server. Docker Compose manages the container, while a volume mount allows HTML and CSS changes to appear without rebuilding the image.

## 🛠️ Built With

- **HTML & CSS** — Website structure and styling
- **Nginx** — Web server that delivers the website
- **Docker** — Builds the image and runs the container
- **Docker Compose** — Configures ports, volumes, restart policy, and health checks
- **Git & GitHub** — Version control and project hosting

## 📂 Project Structure

```text
my-webserver-image/
├── html/
│   ├── index.html
│   └── style.css
├── .dockerignore
├── Dockerfile
├── compose.yaml
└── README.md
```

| File or folder | Purpose |
|---|---|
| `html/` | Contains the website files |
| `index.html` | Defines the webpage content |
| `style.css` | Controls the website's appearance |
| `Dockerfile` | Defines how the Docker image is built |
| `compose.yaml` | Configures and manages the container |
| `.dockerignore` | Excludes selected files from the build context |
| `README.md` | Project documentation |

## ⚙️ How It Works

1. **Build:** Docker reads the `Dockerfile` and creates an image based on `nginx:alpine`.
2. **Copy:** The website files are copied into Nginx's web directory in the image.
3. **Run:** Docker Compose starts the website container.
4. **Connect:** Port `8082` on the computer maps to port `80` inside the container.
5. **Update:** A read-only volume mount makes local HTML and CSS changes visible inside the container.
6. **Monitor:** A health check tests whether Nginx responds to a local HTTP request.
7. **Restart:** The restart policy tells Docker to restart the container if it stops unexpectedly, unless it was manually stopped.

## 🚀 Getting Started

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Git (optional if you download the project another way)

### 1. Clone the Repository

```bash
git clone https://github.com/Eriksomethingsomething/my-webserver-image.git
cd my-webserver-image
```

### 2. Start the Website

```bash
docker compose up -d --build
```

### 3. Open the Website

Visit:

**http://localhost:8082**

### 4. Check Container Status

```bash
docker compose ps
```

The container should eventually report `healthy` when the health check succeeds.

### 5. View Logs

```bash
docker compose logs
```

### 6. Stop the Website

```bash
docker compose down
```

## ✨ Features

- Lightweight Nginx Alpine image
- Dockerized static website
- Docker Compose configuration
- Local port mapping
- Read-only volume mount for website files
- Automatic container restart policy
- Container health check
- Git and GitHub version control

## 🎯 Learning Objectives

This project was created to develop practical skills in:

- Building and running Docker images and containers
- Configuring services with Docker Compose
- Understanding ports, volumes, and container health checks
- Hosting static websites with Nginx
- Using Git and GitHub to manage project changes
- Working across macOS and Windows

## 👨‍💻 Author

**Erik Andersen**

---

*Built as a hands-on project to learn Docker, web servers, and version control.*