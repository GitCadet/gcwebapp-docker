#  🐳 GitCadet: Dockerised Website

This repository contains a custom docker website, packaged and hosted using NGINX. Below, you'll find a detailed breakdown of the steps to build, tag, version, and then push the Docker image to a Docker registry, as well as some instructions for running the container. Additionally, I share key things I learned during this process.

---

## Building the Docker Image
In order to build GitCadet custom website, I first specified a Dockerfile that included:
- "`FROM nginx:latest`" - to set the base image. 
- "`ADD . /usr/share/nginx/html`" - to copy the files & directories from source to the destination filesystem of the image. This also ensures the custom website is served directly by NGINX.

(Used `nginx:latest` as the initial base image but for optimisation, I later switched to `nginx:1.27.3-alpine` to reduce image size.)

With the Dockerfile ready, I built the Docker image using the following command:
- "`docker build -t gitcadet-website:latest .`" 

### Tagging & Versioning:
To maintain a professional development workflow, I implemented a clear versioning strategy:

Initial Tagging:
- I tagged the image as "`gitcadet-website:latest`" during initial development.
- Utilised "`docker tag gitcadet-website:latest gitcadet-website:1`" to version the image.

Versioned Tags:
- `gitcadet-website:1`
- `gitcadet-website:2`
- `gitcadet-website:3`

This approach allows for organised deployments and easy rollback if necessary.

## Running the Docker Container

Run the Docker container using "`docker run --name gcwebappL -d -p 800:80 website:latest`"
- `-d`: Runs the container in detached mode.
- `-p 800:80`: Maps port 800 of the host to port 80 on the container.
- `--name`: Assigns the 'gcwebappL' name to the container for easier management.

I then verified the container is running using the "`docker ps`" command. Once verified, I accessed the application by navigating to "`http://localhost:800`" in my browser.

### Version 1:
![image alt](https://github.com/GitCadet/gcwebapp-docker/blob/main/Screenshot%202025-01-21%20at%2014.14.40.png?raw=true)

### Version 3 (Latest):
![image alt](https://github.com/GitCadet/gcwebapp-docker/blob/main/Screenshot%202025-01-21%20at%2014.14.55%201.png?raw=true)
## Pushing to Docker Registry
To share my Docker image, I pushed it to DockerHub by following these steps:

### Step 1: Authenticate with Docker Hub
Logged in to Docker Hub using Docker Desktop.

### Step 2: Push the Image
Pushed the tagged image to my Docker Hub repo:
- `docker push dock8pro/website:latest`

For versioned images:
- `docker push dock8pro/website:1`
- `docker push dock8pro/website:2`
- `docker push dock8pro/website:3`
### Step 3: Verify the Image
I checked my Docker Hub repository to confirm the image is available.
## Key Learnings and Improvements 💡
1. **Reducing Image Size:** Using Alpine Linux significantly reduces the image size, which leads to faster builds and deployments, hence I changed the Dockerfile to read "`FROM nginx:1.27.3-alpine`".
2. **Security Best Practices:** Use specific image versions instead of "`latest`" to avoid unexpected changes.
3. **Efficient Container Management:** I became more comfortable with managing Docker containers using commands "`docker logs`" to view container logs. This was essential in debugging and verifying that everything was running as expected.
