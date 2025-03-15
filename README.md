# Docker-CMD


# Docker Commands Cheat Sheet

## DOCKER ALL PULL COMMANDS

### 1. Pull the Latest Version of an Image
```
docker pull <image_name>
```
**Example:**
```
docker pull ubuntu  # Pulls the latest Ubuntu image
```

### 2. Pull a Specific Version of an Image
```
docker pull <image_name>:<tag>
```
**Example:**
```
docker pull ubuntu:20.04
```

### 3. Pull from a Specific Registry
```
docker pull <registry>/<image_name>:<tag>
```
**Example:**
```
docker pull myregistry.com/myrepo/myimage:latest
```

### 4. Pull from Docker Hub with Organization Name
```
docker pull <organization>/<image_name>:<tag>
```
**Example:**
```
docker pull library/nginx:alpine
```

### 5. Pull Multiple Versions of an Image
```
docker pull ubuntu:20.04
docker pull ubuntu:22.04
docker pull ubuntu:latest
```

---

## DOCKER IMAGE AND CONTAINER COMMANDS

### 1. List All Images
```
docker images  # Shows all locally available Docker images
```

### 2. Remove a Specific Image
```
docker rmi <image_id>
```

### 3. Show Running Containers
```
docker ps
```

### 4. List All Containers (Including Stopped Ones)
```
docker ps -a  # Displays all containers, including stopped ones
```

### 5. Run a Container Interactively
```
docker run -it <image_name>
```
**Example:**
```
docker run -it ubuntu  # Starts an interactive Ubuntu shell
```

### 6. Run a Container in Detached Mode (Background)
```
docker run -d <image_name>
```
**Example:**
```
docker run -d nginx  # Starts an Nginx container in the background
```

### 7. Attach to a Running Container
```
docker attach <container_id>
```

### 8. Stop a Running Container
```
docker stop <container_id>
```

### 9. Start a Stopped Container
```
docker start <container_id>
```

### 10. Restart a Container
```
docker restart <container_id>
```

### 11. Remove a Container
```
docker rm <container_id>
```

### 12. Remove a Running Container
```
docker rm -f <container_id>
```

### 13. Remove All Stopped Containers
```
docker container prune
```

---

## PORT MAPPING IN DOCKER

### 1. Run a Container and Expose a Port
```
docker run -p <host_port>:<container_port> <image_name>
```
**Example:**
```
docker run -p 8080:80 nginx  # Maps port 80 of the container to port 8080 on the host
```

### 2. List All Mapped Ports
```
docker ps  # Shows running containers and their port mappings
```

### 3. Check Container Logs
```
docker logs <container_id>
```

---

## MISCELLANEOUS COMMANDS

### 1. Run a Command Inside a Running Container
```
docker exec -it <container_id> <command>
```
**Example:**
```
docker exec -it my_container bash  # Opens a shell inside the running container
```

### 2. Show Real-Time Container Stats
```
docker stats  # Displays CPU, memory, network usage of running containers
```

### 3. Show Container Process List
```
docker top <container_id>
```

---

## PUSH AN IMAGE TO DOCKER HUB

### Step 1: Log in to Docker Hub
```
docker login
```

### Step 2: Tag the Image
```
docker tag <image_id> <your_dockerhub_username>/<repository_name>:<tag>
```
**Example:**
```
docker tag myapp myusername/myapp:latest
```

### Step 3: Push the Image
```
docker push <your_dockerhub_username>/<repository_name>:<tag>
```
**Example:**
```
docker push myusername/myapp:latest
```

---

## STEPS FOR CREATING YOUR OWN IMAGE

### Step 1: Create a Dockerfile
A Dockerfile is a script containing all the commands to build an image.
```
# Use base image (e.g., Ubuntu)
FROM ubuntu:latest

# Set the working directory inside the container
WORKDIR /app

# Copy local files into the container
COPY . /app

# Install dependencies (example for Python)
RUN apt update && apt install -y python3

# Set the command to run the container
CMD ["python3", "--version"]
```

### Step 2: Build the Image
```
docker build -t my_custom_image .
```
- `-t my_custom_image` → Assigns a name to the image
- `.` → Tells Docker to look for a Dockerfile in the current directory

### Step 3: Verify the Image
```
docker images  # Check if your image is created
```

### Step 4: Run a Container from Your Image
```
docker run my_custom_image
```
**For Interactive Mode:**
```
docker run -it my_custom_image bash
```

### Step 5: Tag Your Image (For Pushing)
```
docker tag my_custom_image myusername/my_custom_image:latest
```

### Step 6: Push Your Image to Docker Hub
```
docker login
docker push myusername/my_custom_image:latest
```

### Step 7: Remove the Image (Optional)
```
docker rmi my_custom_image
```

---

## Additional Docker Commands
```
docker commit  # Save changes made to a container

docker push    # Push an image to a registry

docker copy    # Copy files between container and host

docker logs    # View logs of a container

docker volume  # Manage Docker volumes (used for storing data)

docker logout  # Logout from Docker Hub
```

---

This cheat sheet covers essential Docker commands to help you manage images and containers effectively.

