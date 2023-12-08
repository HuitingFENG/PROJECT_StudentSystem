# PROJECT_StudentSystem

## 1. Description
- Course name: Software Engineering for the Cloud
- Students M2 SE1: FOUR & FENG


## 2. Prerequisite
- java openjdk 11.0.21
- minikube version: v1.31.2
- Docker version 24.0.6
- mysql version 8.1.0 
- npm version 8.15.0
- git version 2.33.0


## 3. Steps
### 3.1. Start with a single local service (appbackend-service)
Git clone an application (java sprint boot) 

    git clone https://github.com/youtube-arjun-codes/FullStackAppFrontEnd.git
Create a new database named fullstack and a new table named student on MySQL Workbench
Run it in the local machine

    npm i
    npm start
start the MySQL server depending on your operating system
    
    brew services start mysql
Open a new browser and input 

    http://localhost:8080/student/getAll
Check if the application works correctly, otherwise troubleshoot problems to be able to run the application


Create a Docker image


Publish the Docker image to the Docker Hub

Create a Kubernetes deployment

Create a Kubernetes service

### 3.2. Add a local gateway using ingress
### 3.3. Add a second service (appfrontend-service)
### 3.4. Add a local database (mysql)
### 3.5. Deploy in a cloud infrastructure (Git Actions)


### FrontEnd
    - git clone https://github.com/youtube-arjun-codes/FullStackAppFrontEnd.git 
    - npm start

### BackEnd
    - git clone https://github.com/youtube-arjun-codes/FullStackApp.git
    - Intellij: settings -> build tool -> choose maven -> apply
    - cd FullStackApp
    - brew install maven
    - mvn clean package (build the java application)

### Database-MySQL
#### create a container MySQL
    - docker pull mysql
    - docker run --name fullstackappDB -v /usr/local/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=Huiting123.. -p 3300:3306 -d mysql:latest   
    - docker ps
    - mysql -h localhost -P 3300 -u root -p
    - select * from fullstack.student;
    - exit
#### deploy the MySQL container into the Kubernetes cluster 
    - minikube start
    - apply some yaml files of mysql



## 4. Google Labs
### FOUR

### FENG
![](Images/GoogleLabs_HuitingFENG.png)
