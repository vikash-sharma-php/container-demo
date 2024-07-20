Sure! Here's a `README.md` file that includes instructions and basic Docker commands for building, running, and managing the simple Flask container described above.

```markdown
# Simple Flask App in a Docker Container

This repository contains a simple Flask web application that runs inside a Docker container. The following instructions will guide you through building and running the Docker container.

## Prerequisites

- Docker installed on your machine. You can download and install Docker from [here](https://docs.docker.com/get-docker/).

## Files

- `app.py`: A simple Flask web application.
- `Dockerfile`: Instructions to build the Docker image.

## Instructions

### 1. Create `app.py`

Create a file named `app.py` with the following content:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=80)
```

### 2. Create `Dockerfile`

Create a file named `Dockerfile` in the same directory as `app.py` with the following content:

```dockerfile
# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install Flask
RUN pip install flask

# Make port 80 available to the world outside this container
EXPOSE 80

# Run app.py when the container launches
CMD ["python", "app.py"]
```

### 3. Build the Docker Image

Open a terminal, navigate to the directory containing `app.py` and `Dockerfile`, and run the following command:

```sh
docker build --tag simple-flask-app --load .
```

This command builds a Docker image named `simple-flask-app`.

### 4. Run the Docker Container

Once the image is built, you can run the container with the following command:

```sh
docker run -p 4000:80 simple-flask-app
```

This command maps port 4000 on your host to port 80 in the container. You can now access the Flask app in your web browser by navigating to `http://localhost:4000`.

### Basic Docker Commands

Here are some basic Docker commands for managing images and containers:

- **List Docker images:**

  ```sh
  docker images
  ```

- **List running containers:**

  ```sh
  docker ps
  ```

- **List all containers (including stopped ones):**

  ```sh
  docker ps -a
  ```

- **Stop a running container:**

  ```sh
  docker stop <container_id>
  ```

- **Remove a stopped container:**

  ```sh
  docker rm <container_id>
  ```

- **Remove a Docker image:**

  ```sh
  docker rmi <image_id>
  ```

Replace `<container_id>` and `<image_id>` with the actual IDs from the output of `docker ps -a` and `docker images`, respectively.

## Summary

This guide walks you through creating a simple Flask web application, containerizing it with Docker, and running the container. Additionally, it provides basic Docker commands for managing images and containers.

Feel free to reach out if you have any questions or need further assistance!
```

This `README.md` file includes all the necessary steps and commands for beginners to understand how to build, run, and manage a Docker container for the simple Flask application.