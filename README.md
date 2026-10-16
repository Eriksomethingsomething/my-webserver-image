# Dockerized Web Server

A static website served by **Nginx inside a Docker container**, with Docker Compose used to configure and run the service.

## 📌 Overview

This project demonstrates how to build and run a containerized web server using Docker and Nginx. It includes a custom Nginx configuration, a custom 404 error page, a health check, a restart policy, and read-only volume mounts for easier development.

## 🛠️ Technologies Used

- **HTML & CSS** — Website structure and styling
- **Nginx** — Serves the website and handles HTTP requests
- **Docker** — Builds images and runs containers
- **Docker Compose** — Configures and manages the website service
- **Git & GitHub** — Version control and project hosting

## 📂 Project Structure

```text
my-webserver-image/
├── html/
│   ├── index.html
│   ├── style.css
│   └── 404.html
├── nginx/
│   └── default.conf
├── .dockerignore
├── .gitignore
├── Dockerfile
├── compose.yaml
└── README.md
```

| File or folder | Purpose |
|---|---|
| `html/` | Contains the website files |
| `html/index.html` | Defines the main webpage |
| `html/style.css` | Controls the website's appearance |
| `html/404.html` | Custom page displayed for missing URLs |
| `nginx/default.conf` | Custom Nginx server configuration |
| `Dockerfile` | Defines how the Docker image is built |
| `compose.yaml` | Configures the website container, ports, volumes, and health check |
| `.dockerignore` | Excludes selected files from the Docker build context |
| `.gitignore` | Specifies files Git should ignore |
| `README.md` | Documents the project |

## ⚙️ How It Works

1. **Build the image:** Docker reads the `Dockerfile`, which uses `nginx:alpine` as its base image.
2. **Copy the website:** The Dockerfile copies the contents of `html/` into Nginx's web directory in the image.
3. **Configure Nginx:** Docker Compose mounts `nginx/default.conf` into `/etc/nginx/conf.d/default.conf` inside the container.
4. **Run the service:** Docker Compose starts the website and configures port mapping, volume mounts, a restart policy, and a health check.
5. **Access the website:** Port `8082` on the host maps to port `80` inside the container.
6. **Edit website files:** The read-only mount `./html:/usr/share/nginx/html:ro` makes local HTML and CSS changes available inside the container without rebuilding the image. The mounted files take precedence over the files copied into the image while the mount is active.
7. **Handle missing pages:** The custom Nginx configuration directs 404 errors to `html/404.html`.
8. **Check service health:** Docker periodically checks whether Nginx responds successfully to a local HTTP request.
9. **Restart if needed:** The `unless-stopped` restart policy allows Docker to restart the container after unexpected stops unless it has been manually stopped.

## 🚀 Getting Started

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Git

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

### 4. Test the Custom 404 Page

Visit [http://localhost:8082/doesnotexist](http://localhost:8082/doesnotexist).

You should see the custom 404 page rather than the default Nginx error page.

### 5. Check Container Status

```bash
docker compose ps
```

The container should eventually report `healthy` if the health check succeeds.

### 6. View Logs

```bash
docker compose logs
```

To view only the latest logs:

```bash
docker compose logs --tail=30
```

### 7. Test the Nginx Configuration

```bash
docker compose run --rm website nginx -t
```

This runs an Nginx configuration syntax test in a temporary container using the Compose configuration and mounts.

### 8. Stop the Website

```bash
docker compose down
```

## ✨ Features

- Static website served by Nginx
- Lightweight Alpine-based Nginx image
- Docker image built from a Dockerfile
- Service configuration using Docker Compose
- Custom Nginx server configuration
- Custom 404 error page
- Local port mapping (`8082:80`)
- Read-only volume mounts
- Automatic container restart policy
- Docker health check
- Git and GitHub version control

## 🎯 Learning Objectives

This project provides hands-on experience with:

- Building Docker images and running containers
- Configuring services with Docker Compose
- Understanding ports, volumes, and health checks
- Hosting static websites with Nginx
- Configuring custom Nginx behavior
- Testing configurations and troubleshooting errors
- Using Git and GitHub to track project changes
- Preparing a containerized project for automated testing and CI/CD

## 👨‍💻 Author

**Erik Andersen**

---

*Built as a hands-on project to learn Docker, web servers, and version control.*
