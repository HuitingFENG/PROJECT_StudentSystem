# PROJECT_StudentSystem

#### Course name: Software Engineering for the Cloud
#### Students: FOUR & FENG


## Prerequisite
### FrontEnd
#### git clone https://github.com/youtube-arjun-codes/FullStackAppFrontEnd.git 
#### npm start

### BackEnd
####  git clone https://github.com/youtube-arjun-codes/FullStackApp.git
#### Intellij: settings -> build tool -> choose maven -> apply
#### cd FullStackApp
#### brew install maven
#### mvn clean package (build the java application)

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
