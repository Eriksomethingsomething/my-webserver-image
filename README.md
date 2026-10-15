# Dockerized Web Server

A static website served by **Nginx inside a Docker container**, with Docker Compose used to configure and run the service.

## 📌 Overview

This project demonstrates how to build a Docker image, run a containerized web server, and serve a static website locally. It also includes a health check, a restart policy, and a read-only volume mount for easier development.

## 🛠️ Technologies Used

- **HTML & CSS** — Website structure and styling
- **Nginx** — Serves the website to visitors
- **Docker** — Builds images and runs containers
- **Docker Compose** — Configures and runs the website service
- **Git & GitHub** — Version control and project hosting

## 📂 Project Structure

```text
my-webserver-image/
├── html/
│   ├── index.html
│   └── style.css
├── .dockerignore
├── .gitignore
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
| `compose.yaml` | Configures and runs the website container |
| `.dockerignore` | Excludes selected files from the Docker build context |
| `.gitignore` | Tells Git which untracked files to ignore |
| `README.md` | Documents the project |

## ⚙️ How It Works

1. **Build the image:** Docker reads the `Dockerfile`, which uses `nginx:alpine` as its base image.
2. **Copy the website:** The `Dockerfile` copies the contents of `html/` into Nginx's web directory in the image.
3. **Run the container:** Docker Compose uses `compose.yaml` to configure and run the website service, including its ports, volume mount, restart policy, and health check.
4. **Access the website:** Port `8082` on the computer maps to port `80` inside the container.
5. **Edit website files:** The read-only volume mount makes local HTML and CSS changes visible inside the running container without rebuilding the image. The mount takes precedence over the files copied into the image while it is active. The `COPY` instruction still puts the website files into the image itself.
6. **Check the service:** Docker periodically checks whether Nginx responds successfully to a local HTTP request. The container reports `healthy` when the health check succeeds.
7. **Restart if needed:** The `unless-stopped` restart policy tells Docker to restart the container if it stops unexpectedly, unless it has been manually stopped.

## 🚀 Getting Started

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

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

Visit [http://localhost:8082](http://localhost:8082) in your browser.

### 4. Check Container Status

```bash
docker compose ps
```

The container should eventually report `healthy` if the health check succeeds.

### 5. View Logs

```bash
docker compose logs
```

### 6. Stop the Website

```bash
docker compose down
```

## ✨ Features

- Static website served by Nginx
- Lightweight Alpine-based Nginx image
- Docker image built from a Dockerfile
- Container configuration using Docker Compose
- Local port mapping
- Read-only volume mount for website files
- Automatic container restart policy
- Docker health check
- Git and GitHub version control

## 🎯 Learning Objectives

This project demonstrates practical experience with:

- Building Docker images and running containers
- Configuring services with Docker Compose
- Understanding ports, volumes, and health checks
- Hosting static websites with Nginx
- Troubleshooting and managing a containerized service
- Using Git and GitHub to track project changes
- Working across macOS and Windows

## 👨‍💻 Author

**Erik Andersen**

---

*Built as a hands-on project to learn Docker, web servers, and version control.*