# Docker

Docker run docker/whalesay cowsay Hello-World 

    Pull the image from the repository and runs it 

 

Docker run  

    Run a container from an image 

 

Docker run nginx 

    Runs an instance of nginx 

 

Docker ps 

    List all running containers 

 

Docker ps -a 

    List running and stopped containers 

 

Docker stop (ContainerId/ContainerName) 

    Stop a docker container 

 

Docker rm (ContainedID/ContainerName) 

    Throw permanently (Saves space) 

 

Docker images 

    See images 

 

Docker rmi nginx 

    Remove docker images 

Delete all dependent containers to remove image 

 

Docker pull nginx 

    Pull, not run 

 

Once the task is complete, the container stops and that why we see most of the containers on exited state. 

 

Docker run ubuntu sleep 5 

    Runs the ubuntu container and then sleeps for about 5 seconds and then exists 

 

Docker exec (ContainedID/ContainerName) cat /etc/hosts 

    Execute a command inside a container 

 

Docker run –d docker/whapesay 

    Run the Docker Container in the background 

 

Docker attach (ContainedID) 

    Run the Docker Container in the foreground 

 

Docker run –name webapp imageName 

    Make an instance with a name 

 

Docker run redis 

Docker run redis:4.0 

    Tag is used to run a specific type of version of the software 

    (default=latest) 

    Can find supported tags on dockerhub.com 

 

Docker run -it kodekloud/simple-prompt-docker 

    By default, docker doesn't listen the input: Runs on non interactive mode 

    '-I' is interactive mode 

    Also need to attach the container terminal with our terminal 

    '-t' sudo terminal 

 

Port mapping 

 

 

We can map internal docker port on our external system port through the command 

Docker run –p 80:5000 simple-webapp 

    This will map the port of 500 which is inside the docker container into 80 of our external port. 

    To run this on the browser we use 192.168.1.5:80 

    We can map multiple ports 

 

Volume mapping 

 

 

Docker run –v /opt/datadir:/var/lib/mysql mysql 

    We need to persist the data outside the container 

    -v mounts and the data are all stored outside 

  

Docker inspect blissful_hopper 

    Inspect the container to find the details 

 

Docker logs blissful_hopper 

    Get the logs 

 

Environment Variable 

 

Docker run –e APP_COLOR=blue/red/yel-dlow simple-webapp-with-color 

    Setting Environment Variables from docker command 

    How to find? Inspect the container first and then see the json where it says Config:Env:App_Color 


    Making a docker Image:  

Why? To create an application according to my needs. 

    OS-Ubuntu 

    Update apt-repo 

    Install dependencies using apt 

    Install Python dependencies using pip 

    Copy source code to /opt folder 

    Run the web server using "flask" command 

 

Make a Docker File: 

Dockerfile 

 

 

FROM ubuntu:16.04   (base OS) 

 

RUN apt-get update 

RUN apt-get install python -y  

RUN apt-get install python-pip -y 

RUN pip install --upgrade pip 

 

RUN pip install flask 

RUN pip install flask-mysql 

 

COPY . /opt/source-code 

 

ENTRYPOINT FLAS_APP=/opt/source-code/app.py flask run 

 

Build the code: 

Docker build -t sulabh/first-image-app. 

 

To prompt the answer, just type –y –n after the command 

Example: RUN apt-get install python -y 

 

Push the code: 

Docker push sulabh/first-image-app 

 

Dockerfile is easy to write: 

INSTRUCTION 	 ARGUMENT 
FROM    ubuntu 
RUN     apt-get update 

 