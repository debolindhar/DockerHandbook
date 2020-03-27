# DockerHandbook

1. Docker -
--------------------------

>> How to run docker image -
>> Docker run hello-world

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

>> How to list the containers in my system 
>> docker ps -a

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
abb730b5bc41        hello-world         "/hello"            3 minutes ago       Exited (0) 3 minutes ago                       hardcore_wozniak

>> How to rerun existing container
>> docker start --attach <Name of existing container>

>> How to stop a docker container
>> docker stop <container name>

>> How to remove a docker container
>> docker rm <container name>

>> How to run Ubuntu image in Docker 
>> docker run -it ubuntu bash

** -it --> stands for interactive


>> How to check the processes running inside container from docker shell 
>> docker top <container name>

>> How to list all the docker images in my system
>> docker image ls

>> Create docker image
>> docker run -v /full/path/to/html/directory:/usr/share/nginx/html:ro -p 8080:80 -d nginx

>> How to run docker container interactively -
>> docker container run --interactive --tty --rm ubuntu bash

** --interactive is for interactive session
** --tty - provides terminal information
** --rm - remove container when exited
** ubuntu is the image name
** bash - is the main process to run on on ubuntu as PID1

>> How to get detail of an image 
>> docker inspect <image name> 

>>How to see all the commands that were run with an image via a container
>> docker history ImageID 

>> How to kill a container
>> docker kill ContainerID

>> BUILD DOCKER IMAGE
** We need to create Dockerfile for creating our docker image

** Example of Docker File 

#This is a sample Image 
FROM ubuntu 
MAINTAINER demousr@gmail.com 

RUN apt-get update 
RUN apt-get install –y nginx 
CMD [“echo”,”Image created”] 

**
** FROM -> is the base image

>> How to build a docker image
>> docker build  -t ImageName:TagName dir

** -t - is used mention a tag to the image
** ImageName - Name of my image
** TagNum 
** dir - location of docker file (.) if root folder

>> How to allow one to tag an image to the relevant repository.
>> docker tag imageID Repositoryname 
>> docker tag ab0c1d3744dd demousr/demorep:1.0


>> How to push docker image to docker repo
>> docker push Repositoryname 

2. Terraform, ARM (IAC)
3. Test Automation (Unit Test, Functional, Load)
4. Monitoring
5. Power BI
6. ETL
7. Powershell - Trigger, Hook

Calling a build using Powershell -
--------------------------------------
$body = '
{ 
        "definition": {
            "id": 
        } 
}
'
$bodyJson=$body | ConvertFrom-Json
Write-Output $bodyJson
$bodyString=$bodyJson | ConvertTo-Json -Depth 100
Write-Output $bodyString
$user="VSTSAPI"
$token=""
$base64AuthInfo = [Convert]::ToBase64String([Text.Encoding]::ASCII.GetBytes(("{0}:{1}" -f $user,$token)))

$Uri = "https://dev.azure.com/"
$buildresponse = Invoke-RestMethod -Method Post -UseDefaultCredentials -ContentType application/json -Uri $Uri -Body $bodyString -Headers @{Authorization=("Basic {0}" -f $base64AuthInfo)}
write-host $buildresponse


---------------------------------------------------------------------------------------------

Personal Azure DevOps Account --> https://dev.azure.com/debolindhar/Test01


{ "action": "Microsoft.Resources/checkPolicyCompliance/read", "scope": "/subscriptions/d1013fc6-d428-4525-9c85-7c751e391cd6" }	
