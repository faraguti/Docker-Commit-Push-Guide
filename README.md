<p align="center">
  <img src="https://github.com/faraguti/Docker-Commit-Push-Guide/assets/5418256/6fd6bda6-987e-4383-af25-b61d7d849d97" height="100%" width="100%">
</p>

# Docker Container Commit and Push to Docker Hub
<br/>

This repository provides a step-by-step guide on how to use `docker commit` to create a new Docker image from changes made to a container and push it to Docker Hub.

## Prerequisites

Before you begin, make sure you have the following installed on your system:

- Docker: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
- Docker Hub Account: Create an account on Docker Hub if you don't have one: [https://hub.docker.com/](https://hub.docker.com/)

## Steps

1. **Create the Container:**

   In Step 1, we will create a new Docker container using the official Microsoft SQL Server (mssql) container image from Docker Hub. The docker run command used in the guide sets up the container with specific configurations:
   ```
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=cit326Password$" -e "MSSQL_AGENT_ENABLED=true" -p 49433:1433 --name mssql -d --restart unless-stopped mcr.microsoft.com/mssql/server
   ```

    > [!NOTE] **Breakdown of the docker run command:**
    
    - `-e "ACCEPT_EULA=Y"`: This environment variable is set to "Y", which accepts the End-User License Agreement (EULA) for Microsoft SQL Server.
    - `-e "SA_PASSWORD=cit326Password$"`: This environment variable sets the password for the "SA" (System Administrator) account in SQL Server to "cit326Password$".
    - `-e "MSSQL_AGENT_ENABLED=true"`: This environment variable enables the SQL Server Agent service within the container.
    - `-p 49433:1433`: This option maps port 49433 on the host machine to port 1433 inside the container. Port 1433 is the default port used by SQL Server for communication, so this mapping allows access to the SQL Server instance running inside the container.
    - `--name mssql`: The `--name` option assigns the name "mssql" to the running container for easier reference.
    - `-d`: This option runs the container in detached mode, meaning it runs in the background.
    - `--restart unless-stopped`: This option specifies the container's restart policy to restart unless explicitly stopped. This ensures that the container automatically starts if the system reboots.
