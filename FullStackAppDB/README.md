# Deploiement d'un conteneur MySQL dans un cluster Kubernetes 

## Deploiement du serveur MySQL
### Prérequis
    - minikube start
### Descriptif des fichiers :
mysql-secret.yaml
Ce fichier définit le mot de passe qui sera utilisé lors de la connexion au serveur MySQL.
    - kubectl apply -f mysql-secret.yaml
mysql-storage.yaml
Ce fichier définit les volumes qui vont être utilisés par le serveur MySQL pour stocker les données.
    - kubectl apply -f mysql-storage.yaml
mysql-deployment.yaml
Ce fichier définit le conteneur mysql à déployer sur le cluster kubernetes.
    - kubectl apply -f mysql-deployment.yaml
### Création de service
Il existe deux fichiers de création de service, il n'est pas nécessaire d'exécuter les deux.
Exécuter uniquement celui qui correspond le mieux à votre besoin.
Le service de type ClusterIP
Le fichier mysql-serviceClusterIp.yaml crée un service 'mysql' qui est uniquement accessible dans le cluster.
    - kubectl apply -f mysql-serviceClusterIp.yaml
Le service de type NodePort
Le fichier mysql-serviceNodePort.yaml crée un service 'mysql' qui est accessible à la fois à l'intérieur et à l'extérieur du cluster.
    - kubectl apply -f mysql-serviceNodePort.yaml

## Vérification des configurations
    - kubectl get secrets
    - kubectl get PersistentVolumes
    - kubectl get PersistentVolumeClaims
    - kubectl get deployments
    - kubectl get services
    - kubectl get pods

## Connexion au server MySQL
    - kubectl exec --stdin --tty <Nom du pod> -- mysql -p<Password>
Création d'une table et d'un utilisateur
    - mysql> create database db_example; -- Creates the new database 
    - mysql> create user 'test'@'%' identified by 'test'; -- Creates the user
    - mysql> grant all on db_example.* to 'test'@'%'; -- Gives all privileges to the new user on the newly created database
Le service de type NodePort 
    - minikube service mysql
L'url du service
    - minikube service mysql --url