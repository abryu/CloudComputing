# Cloud Monitor Description


## Architecture Overview

> [Open this link for graphic visualization](https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1#G1ASOKu9zKSIOoosrMf84RkAvozgMljbxS)

## Source Code
* registration
    * https://github.com/abryu/eureka-zuul
* zuul
    * https://github.com/abryu/cc-zuul
* auth
    * https://github.com/abryu/auth-zuul
* vm
    * https://github.com/abryu/vm-zuul

## Infrastucture

### Evoluation

* Second Assignment 
    * Standalone App ran on Google App Engine
    * Cloud SQL (relational database)
* Third Assignment
    * Microservices deployed on Google Compute Engine Instances
    * Cloud Datastore (non-relational database)
* Final Project
    * Microservices deployment on Google Kubernetes Engine
    * Cloud Datastore (non-relational database)

### Google Cloud Platform
* Kubernetes Engine
    * frontend
        * 1 replica
        * exposed to external access
    * registration
        * 1 replica
        * NodePort exposed to external and internal access
    * zuul
        * 1 replica
        * NodePort exposed to external and internal access
        * could be exposed by LoadBalancer as well (save money for a static ip address at this moment)
    * auth
        * 1 replica
        * exposed to internal access
    * vm
        * 2 replicas
        * exposed to internal access
* Datastore
    * non-relational database for storing vm operations logs
* Cloud SQL
    * relational database for storing user login information
* Firewall
* Other Google Cloud Services
    * Cloud Storage
    * Cloud Pub/Sub
    * Cloud Functions

## Tech Stack

### Services List
* frontend
    * ui
* registration
    * services registration and discovery
* zuul
    * gateway to distribute requests
    * handle and forward authentication requests
* auth
    * validate user identities by OAuth (jwt)
* vm
    * process operations on virtual machines
    * process billing management

### Framework
* front-end
    * Bootstrap
    * jQuery
* registration
    * Spring.cloud
    * Spring.eureka
* zuul
    * Spring.cloud
    * Spring.zuul
    * Spring.security
* auth
    * Spring.cloud
    * Spring.security
* vm
    * Spring.cloud
    * Spring.gcp





## DevOps Practice
* Continuous Integration
    * Source Code Repositories
        * Google Cloud Source Repositories
        * Github
    * Google Cloud Build
        * listens events from Cloud Source Repostiroes
        * once a change detected
            * download required dependeices
            * package java code
            * build and publish an image to Container Registry
    * Container Images Repositories
        * Google Container Registry
        * Dockerhub
* Continuous Testing
    * Cloud Build (currently skip tests)
* Continuous Deployment
    * Cloud Build
        * deploy the newly created image from Container Registry to Kubenetes

## Administration and Auditing
* Stackdrive
* Cloud IAM