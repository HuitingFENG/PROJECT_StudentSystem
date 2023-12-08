# PROJECT_StudentSystem

#### Course name: Software Engineering for the Cloud
#### Students M2 SE1: FOUR & FENG

## Prerequisite
- java openjdk 11.0.21
- minikube version: v1.31.2
- Docker version 24.0.6
- mysql version 8.1.0 
- npm version 8.15.0


## Steps
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



## Google Labs
### FOUR

### FENG
![](Images/GoogleLabs_HuitingFENG.png)
