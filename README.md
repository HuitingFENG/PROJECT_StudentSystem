# PROJECT_StudentSystem

## 1. Description
- Course name: Software Engineering for the Cloud
- Students M2 SE1: FOUR & FENG


## 2. Prerequisite
- Java version: 11.0.21
- minikube version: v1.31.2
- Docker version 24.0.6
- mysql version 8.1.0 
- npm version 8.15.0
- git version 2.33.0
- Apache Maven 3.9.5
- IntelliJ IDEA


## 3. Steps
Open the docker desktop and go to the project and start the minikube via terminal
    
    minikube start
Check the status if wanted
    
    minikube status
Open the dashboard if wanted
    
    minikube dashboard

### 3.1. Start with a single local service (appbackend-service)
Git clone an application (java sprint boot) 

    git clone https://github.com/youtube-arjun-codes/FullStackApp.git
Copy this directory into another new directory to make changes and to git push to our own github repository

    cp -R ./FullStackApp ./AppBackend
Set up Intellij: settings -> build tool -> choose maven -> apply
Install maven if necessary

    brew install maven
Build the java application with maven

    mvn clean package
Create a new database named fullstack and a new table named student on MySQL Workbench
Start the MySQL server depending on your operating system
    
    brew services start mysql
Open a new browser and input 

    http://localhost:8080/student/getAll
Check if the application works correctly, otherwise troubleshoot problems to be able to run the application


Go to the directory AppBackEnd and create a dockerfile

    cd AppBackend
    touch dockerfile
Copy the provided dockerfile and save it and then create a Docker image (open the docker desktop if necessary)

    docker build -t appbackend:1.0 .
Publish the Docker image to the Docker Hub (login if necessary)

    docker images
    docker tag $appbackend1.0ImageID $dockerHubID/appbackend:1.0
    docker push $dockerHubID/appbackend:1.0

Return to the root of project and create a .yaml files with the provided codes (appbackend-deployment, appbackend-service)
    
    cd ..
    touch app-deployment.yaml
Apply the .yaml to create an appbackend-deployment and an appbackend-service
    
    kubectl apply -f app-deployment.yaml
Check the status if wanted, but it's not finished yet

    kubectl get pods,deployments,svc

### 3.2. Add a local database (mysql)
Go to the directory AppBackEnd and update three parts (pom.xml, src/main/resources/application.properties, src/test)
Go to the root of project and create three .yaml files (db-deployment.yaml, mysql-secret.yaml, mysql-configMap.yaml)

    touch db-deployment.yaml
    touch mysql-secret.yaml
    touch mysql-configMap.yaml
Copy the corresponding contents and update the password in the mysql-secret.yaml (ex: if using "test" as password)
    
    echo "test" | base64
Copy the result (the encoded password) from terminal and replace the old password with the encoded password
Update the host, database, username in the mysql-configMap.yaml and the mysql-secret.yaml if necessary
Apply these three .yaml files
    
    kubectl apply -f mysql-secret.yaml -f mysql-configMap.yaml -f db-deployment.yaml 
Check the status if wanted, but it's not finished yet

    kubectl get pods,deployments,svc

### 3.3. Add a second service (appfrontend-service)


### 3.4. Add a local gateway using ingress


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
