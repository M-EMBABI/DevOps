
# **Node.js Application with Docker**

This repository contains a **Node.js application** configured to run inside a Docker container. Follow the steps below to build, run, and interact with the container.

---

## **Prerequisites**

Ensure the following are installed:

1. **Docker**  
   [Download and Install Docker](https://docs.docker.com/get-docker/).

2. **Node.js Application Files**:
   - `Dockerfile`
   - `package.json`
   - Application entry point (e.g., `node.js`)

---

## **Steps to Build and Run the Docker Container**

### **1. Clone the Repository**

Clone this repository and navigate to the project directory:

```bash
git clone <repository-url>
cd <repository-folder>
```

---

### **2. Build the Docker Image**

Run the following command to build the Docker image:

```bash
docker build -t nodejs-app .
```

- **`-t nodejs-app`**: Tags the image with the name `nodejs-app`.  
- **`.`**: Specifies the current directory as the build context.

---

### **3. Run the Docker Container**

To run the container and map the app to port `3000` on the host machine, use:

```bash
docker run -d -p 3000:3000 --name nodejs-container nodejs-app
```

- **`-d`**: Runs the container in detached mode.  
- **`-p 3000:3000`**: Maps port `3000` on the container to port `3000` on the host.  
- **`--name nodejs-container`**: Names the container `nodejs-container`.  
- **`nodejs-app`**: Specifies the image name to use.

---

### **4. Verify the Container is Running**

Check the running containers:

```bash
docker container ps
```

You should see your container listed, similar to:

```
CONTAINER ID   IMAGE         COMMAND                  CREATED       STATUS       PORTS                    NAMES
abc1234efg56   nodejs-app    "docker-entrypoint.s…"   2 minutes ago Up 2 minutes 0.0.0.0:3000->3000/tcp   nodejs-container
```

---

### **5. Access the Application**

Open your browser and go to:

```
http://localhost:3000
```

If running on a remote server, replace `localhost` with the server's IP address.

---

## **Additional Docker Commands**

### Stop the Container

```bash
docker stop nodejs-container
```

### Restart the Container

```bash
docker start nodejs-container
```

### View Logs

```bash
docker logs nodejs-container
```

### Access the Container Shell

```bash
docker exec -it nodejs-container /bin/bash
```

---

## **Example Files**

### **Dockerfile**

```dockerfile
# Use the official Node.js image
FROM node:16

# Set the working directory
WORKDIR /usr/src/app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy application files
COPY . .

# Expose the app port
EXPOSE 3000

# Start the application
CMD ["node", "node.js"]
```

---

### **package.json** (Sample)

```json
{
  "name": "nodejs-docker-app",
  "version": "1.0.0",
  "main": "node.js",
  "scripts": {
    "start": "node node.js"
  },
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

---

## **Docker Hub Link**

You can find the Docker image on Docker Hub:  
[**Node.js App - Docker Hub**](https://hub.docker.com/r/embabi/nodejs-app/tags)

---

