# Spring Boot + MySQL Dockerized Application with Jenkins CI/CD Pipeline

## Overview

This project demonstrates the deployment of a Dockerized Spring Boot application integrated with a MySQL database and automated using a Jenkins CI/CD pipeline.

The project includes:

* Spring Boot application packaged as a Docker container
* MySQL database running in a separate Docker container
* Shared Docker network for container communication
* Jenkins pipeline for automated build and deployment
* Deployment on AWS EC2 with Apache Reverse Proxy

---

## Technologies Used

* Java 17
* Spring Boot
* MySQL
* Docker
* Apache HTTP Server
* Jenkins
* Maven
* Git
* AWS EC2
* Linux

---

## Repository Contents

* Dockerfile – Builds Docker image for the Spring Boot application
* application.properties – MySQL database configuration
* Jenkinsfile – CI/CD pipeline script
* Spring Boot source code and Maven project files

---

## Architecture

User Browser
↓
AWS EC2
↓
Apache HTTP Server (Reverse Proxy)
↓
Spring Boot Application (Docker Container)
↓
MySQL Database

---

## Prerequisites

* Java 17
* Maven
* Docker
* MySQL
* Jenkins
* Git

---

## Deployment Steps

### Clone Repository

git clone https://github.com/Sanjay-Hegde16/sak_spring_jenkins_mysql_docker.git

### Build Application

mvn clean package

### Build Docker Image

docker build -t sak-app .

### Run MySQL Container

docker run -d 
--name mysql-container 
--network app-network 
-e MYSQL_ROOT_PASSWORD=1234 
mysql:8

### Run Application Container

docker run -d 
--name spring-app-container 
--network app-network 
-p 8080:8080 
spring-app

---

## Application Configuration

spring.datasource.url=jdbc:mysql://mysql-container:3306/myapplication?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=1234

---

## Admin Login

Username: admin
Password: admin

---

## Troubleshooting

### Issue 1

Error:
Communications link failure

Reason:
Docker container could not connect to MySQL.

Solution:
Configured Docker networking correctly and ensured MySQL container was running.

### Issue 2

Error:
Port 8080 was already in use.

Reason:
Another Spring Boot application was already running on port 8080.

Solution:
Stopped the existing service or changed the port mapping.

---

## Future Enhancements

* Configure custom domain using DNS.
* Enable HTTPS using SSL certificates.
* Deploy using Docker Compose or Kubernetes.

---



