# Docker-Commands

# **_Basic Commands in Docker_**

    docker -v
    docker run hello-world
    docker ps -all
    docker container ls -a
    docker rm 7b8b1ae0669d
    docker image rm hello-world
    docker image rm 7b8b1ae0669d
    docker container run -d redis:alpine
    docker inspect redis //metadata-exposed port
    docker logs 7b8b1ae0669d
    docker stats 7b8
    docker info
    docker inspect --format='{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' 7b8
    docker container run --detach --publish 80:80 --name <name> nginx
    docker container stop <name>
    docker container start <name>
    docker help run
    docker exec -it <container name> bash //open bash in nginx
    docker history redis

# **_Create New Tags and Push to Docker Hub_**

    docker tag redis ibrahimradi/redis:dev //copy from src to dist
    docker login
    docker push ibrahimradi/redis
    docker logout

# **_Building Docker Image from Dockerfile_**

    docker build --tag <name> .
    dotnet new mvc --name hrapp --output dockerhrapp
    dotnet build
    docker build -t counter-image -f Dockerfile .
    docker images
    docker run -d -p 8080:80 --name hrapp dockerhrapp
    docker run -d --name mymariadb -e MARIADB_ROOT_PASSWORD=1234 -v <volume name>:/var/lib/mysql mariadb
    docker inspect mariadb

# **_Using Docker Volumes & Bind Mounting_**

    docker volume ls
    docker volume create maria-vol
    docker exec -it mymariadb bash
    mysql -u root -p //write sql commands
    exit
    exit
    docker container run -d --name nginx_dashboard -p 8080:80 -v ${pwd}:/usr/share/nginx/html nginx  //shared files

# **_Docker Networking_**

    docker network ls
    docker network inspect
    docker network inspect bridge
    docker network create --driver bridge n1
    docker network ls
    docker network inspect n1
    docker run --name test --network=n1 -d -it ubuntu
    docker container inspect test
    docker network create --driver bridge --subnet 172.25.0.0/16 n2
    docker network disconnect n1 test
    docker network connect n2 test
    docker run --network=n2 -it alpine ash
    #ping 172.25.0.2

# **_Docker Compose_**

    docker-compose -v
    docker compose up -d
    docker compose down

# **_Containerize .NET Application Without Writing Dockerfile_**

    dotnet tool install --global dotnet-build-image
    dotnet build-image -t <image name>
    docker run -p 80:8080 <image name>

# **_Docker CLI Autocomplete_**

    Install-Module -Name posh-cli -Repository PSGallery
    Install-TabCompletion

# **_Running SQL Server on Linux Container_**

    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=yourStrong(!)Password" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2022-latest

# **_Docker Commit_**

    docker commit <container name> <image name>:<tag name> //create image from container
