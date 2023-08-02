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
  docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=1StrongPassword!" -e "MSSQL_AGENT_ENABLED=true" -p 49433:1433 --name mssql -d --restart unless-stopped mcr.microsoft.com/mssql/server
  ```
  
  > [!IMPORTANT]
  > **Breakdown of the docker run command:**
    
  - `-e "ACCEPT_EULA=Y"`: This environment variable is set to "Y", which accepts the End-User License Agreement (EULA) for Microsoft SQL Server.
  - `-e "SA_PASSWORD=1StrongPassword!"`: This environment variable sets the password for the "SA" (System Administrator) account in SQL Server to "1StrongPassword!". Using a weak password may prevent the container from starting. Prioritize a strong password to ensure security and avoid authentication issues.
  - `-e "MSSQL_AGENT_ENABLED=true"`: This environment variable enables the SQL Server Agent service within the container.
  - `-p 49433:1433`: This option maps port 49433 on the host machine to port 1433 inside the container. Port 1433 is the default port used by SQL Server for communication, so this mapping allows access to the SQL Server instance running inside the container.
  - `--name mssql`: The `--name` option assigns the name "mssql" to the running container for easier reference.
  - `-d`: This option runs the container in detached mode, meaning it runs in the background.
  - `--restart unless-stopped`: This option specifies the container's restart policy to restart unless explicitly stopped. This ensures that the container automatically starts if the system reboots.

  <br/>
  <img src="https://github.com/faraguti/Docker-Commit-Push-Guide/assets/5418256/f34818fe-cfb4-4d47-be03-070910cde1f9" height="90%" width="90%">
  
<br><br/>
2. **Make Changes to the Container:**

  In Step 2, you can make any desired changes to the running container. For example, you might install additional software, modify configurations, or create sample data. Use the container interactively or execute commands directly on it.

  Once you have made the necessary changes, you need to create a new Docker image based on the modified container. To do this, we will use the `docker commit` command.
  ```
  docker commit mssql my-modified-mssql:v1.0
  ```

  > [!IMPORTANT]
  > **Breakdown of the docker commit command:**

  - `mssql`: This is the name of the running container you want to commit.
  - `my-modified-mssql`: This is the name you give to the new Docker image. You can replace this with a name of your choice.
  - `v1.0`: This is the tag assigned to the new image. You can use different tags to manage different versions of the image.

  The `docker commit` command creates a new Docker image that includes all the changes you made to the container. You can verify the new image using `docker images` command.
  <br/>
  <img src="https://github.com/faraguti/Docker-Commit-Push-Guide/assets/5418256/497a634b-b57f-4296-8c78-6dcf50289802" height="90%" width="90%">

  
<br><br/>
3. **Push the Image to Docker Hub:**

  In Step 3, we will push the newly created Docker image to Docker Hub. First, you need to log in to your Docker Hub account using the `docker login` command.
  ```
  docker login
  ```
  After running the `docker login` command, enter your Docker Hub credentials (username and password) when prompted. Once you are logged in, you can push the image to Docker Hub using the `docker push` command.

  > [!NOTE]
  > **Security Note:** When entering your password during the `docker login` command, the characters will not be displayed on the screen for security reasons. Simply type the password and press Enter without expecting visible feedback.





