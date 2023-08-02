<summary><strong>Docker Container Commit and Push to Docker Hub</strong></summary>
<br>

This repository provides a step-by-step guide on how to use `docker commit` to create a new Docker image from changes made to a container and push it to Docker Hub.

## Prerequisites

Before you begin, make sure you have the following installed on your system:

- Docker: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
- Docker Hub Account: Create an account on Docker Hub if you don't have one: [https://hub.docker.com/](https://hub.docker.com/)

## Steps

1. **Create the Container:**

   First, create a new Docker container from the base image that you want to modify. You can pull a base image from Docker Hub or use an existing image from your local environment. Run the following command to create the container:

   ```bash
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=cit326Password$" -e "MSSQL_AGENT_ENABLED=true" -p 49433:1433 --name mssql -d --restart unless-stopped mcr.microsoft.com/mssql/server
