# PROJECT_StudentSystem

## 1. Description
- Course name: Software Engineering for the Cloud
- Students M2 SE1: FOUR & FENG


## 2. Prerequisite
- Java version: 11.0.21
- minikube version: v1.31.2
- Docker version 24.0.6
- mysql client version 8.1.0 
- mysql server version 8.0.28
- npm version 8.15.0
- git version 2.33.0
- Apache Maven 3.9.5
- IntelliJ IDEA
- Postman
- Docker Desktop
- MySQLWorkbench

## 3. Steps
Open the docker desktop and go to the project and start the minikube via terminal
    
    minikube start
Check the status if wanted
    
    minikube status
![](Images/MinikubeStatus.png)
Open the dashboard if wanted
    
    minikube dashboard

### 3.1. Start with a single local service (appbackend-service)
Git clone a backend repository (java sprint boot) 

    git clone https://github.com/youtube-arjun-codes/FullStackApp.git
Copy this directory into another new directory to make changes and to git push to our own github repository

    cp -R ./FullStackApp ./AppBackEnd
Remove the old backend repository

    rm FullStackApp
Set up Intellij: settings -> build tool -> choose maven -> apply
Install maven if necessary

    brew install maven
Go to the directory AppBackEnd and build the java application with maven

    mvn clean package
Create a new database named fullstack and a new table named student on MySQL Workbench
Start the MySQL server depending on your operating system
Open a new browser and input 

    http://localhost:8080/student/getAll
Check if the application works correctly, otherwise troubleshoot problems to be able to run the application
![](Images/BackendDemo1.png)
![](Images/BackendDemoAdd.png)
![](Images/BackendDemoGetAll.png)
![](Images/BackendDemo2.png)
Stop the mysql server to make the port 3306 available
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
Go to the root of project and git clone a frontend repository (React)
    
    git clone https://github.com/youtube-arjun-codes/FullStackAppFrontEnd.git
Copy this directory into another new directory to make changes and to git push to our own github repository

    cp -R ./$OldGitHubRepoName ./AppFrontEnd
Remove the old frontend repository

    rm $OldGitHubRepoName
Go to the new directory AppFrontEnd and add an .env file
    
    cd AppFrontEnd
    touch .env
Ensure having the correct local gateway (REACT_APP_API_BASE_URL) that routes requests to the appropriate backend system (appbackend-service) and we will use "studentsystem" as local gateway in this project
Update two url to fetch in the file src/components/Student (line 26, 27, 38, 39)
Create a dockerfile in this directory AppFrontEnd 
    
    touch dockerfile
Copy the corresponding content
Create a docker image
    
    docker build -t appfrontend:12.0 .
Push the docker image into docker hub (login if necessary)

    docker images
    docker tag $appfrontend12.0ImageID $dockerID/appfrontend:12.0
    docker push $dockerID/appfrontend:12.0
Return to the root of project and create a .yaml files with the provided codes 

    cd ..
    touch app-configMap.yaml
Add two parts into the app-deployment .yaml file (appfrontend-deployment, appfrontend-service)
Apply the .yaml to create an appfrontend-deployment and an appfrontend-service

    kubectl apply -f app-deployment.yaml
Check the status if wanted, but it's not finished yet

    kubectl get pods,deployments,svc
Check if all pods, deployments, services are running correctly as below
![](Images/KubernetesRunningStatus.png)


### 3.4. Add a local gateway using ingress


### 3.5. Deploy in a cloud infrastructure (Git Actions)




## 4. Google Labs
### FOUR

### FENG
![](Images/GoogleLabs_HuitingFENG.png)
