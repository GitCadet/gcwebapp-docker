# GitCadet: Dockerised Webpage

This repository contains a Dockerised webapp, packaged and hosted using NGINX. Below, you'll find a detailed breakdown of how I built, tagged, versioned, and pushed the Docker image to a Docker registry, as well as some instructions for running the container.

---

## Building the Docker Image
In order to build GitCadet custom webpage, I first specified a Dockerfile that included a "`FROM nginx:latest`" in order to set the base image. Then, I copied the files & directories from source to the destination filesystem of the image by using "`ADD . /usr/share/nginx/html`"


### Tagging & Versioning:



## Running the Docker Container

Run the Docker container using:

docker run -d -p 8000:80 --website your-username/your-app-name:latest

- `-d`: Runs the container in detached mode.
- `-p 8000:80`: Maps port 8080 of the container to port 8080 on the host.
- `--name`: Assigns a name to the container for easier management.

I then verified the container is running using the `docker ps -format=$FORMAT` command. Once verified, I access the application by navigating to `http://localhost:8000` in my browser.
[image alt](https://github.com/GitCadet/gcwebapp-docker/blob/main/Screenshot%202025-01-21%20at%2014.14.40.png?raw=true)

## Pushing to Docker Registry

To share my Docker image, I pushed it to DockerHub.

### Step 1: Authenticate with Docker Hub

Log in to Docker Hub using `docker login`

### Step 2: Push the Image

Pushed the tagged image to your Docker Hub repository:
- `docker push dock8pro/website:latest`

For versioned images:
- `docker push dock8pro/website:1`
- `docker push dock8pro/website:2`
- `docker push dock8pro/website:3`

### Step 3: Verify the Image

I checked my Docker Hub repository to confirm the image is available.

## Additional Notes

1. **Reducing Image Size:** Using Alpine Linux significantly reduces the image size. Ensure dependencies are installed using `apk add --no-cache` or `pip install --no-cache-dir` to avoid caching unnecessary files.
2. **Security Best Practices:**
   - Use specific image versions instead of `latest` to avoid unexpected changes.
   - Scan your images for vulnerabilities using tools like [Docker Scan](https://docs.docker.com/engine/scan/).

