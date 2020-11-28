# Platform In A Box
This repo outlines a "simple" implementation of a platform in a box.  Modern applications require a common set of core capabilities that can scale as you scale.  Cloud providers such as AWS, MS AZure and Google GCP, provide some/all of these as a service, which you can mix and match.  The below is a way for you to get farmiliar (also 'free') with a fully functional and scalable system.  Its a good place to begin your journey if you working as one, or one in a team of thousands that needs to trasform the way they develop software.  All you need is a decent powered Mac (or access to linux box on cloud provider of your picking), some time, coffee (and beer/wine).  


## Core Capabilities

Container Managament - Docker Swarm - for this implementation we will use a local instance of docker swarm, but suggest others such as EKS, K8 (kube provider), etc.

Admin Dashboard - Portainer.io - a consolidated GUI to view high level platform stats

Service Discovery & Load Balancing - HAProxy, Remco, Registrar, ETCd, etcdKeeper - a collection of tools, to keep an eye on containers, and setup proper routing rules

Logging & Metrics - Elastic Stack - a collection of key tools to provide a vast array of aggregation & reporting capabilities
    (Elastic Search, FileBeat, Log Stash, Kibana, APM)
    You might want Kafka & Zookeeper too
    
Binary & Library Managament - Nexus - a place to store all our images, and shared libraries (could use artifactory or code artifact & ecr)

CI/CD - Jenkins - (depends on SoCat) a tool to automate our CI/CD pipelines and manage the container build process

Scheduling / Coordionation - Apache Airflow (depends on GitSync)

Database - Postgres & Redis

Messaging - RabbitMQ - a simple easy to cluster message broker supported by many languages & framework
  You might want Kafka w/ Zookeeper too

Testability - Selenium 

Languages - While you can develop in just about any language and framework you wish the following are great starting points:
  Front End - Javascript / ReactJS & ReactNative
  API - Python Flask, Java SpringBoot, NodeJS Express
  
  
## Getting Started

1. Download and install Docker Desktop on your Mac (https://desktop.docker.com/mac/stable/Docker.dmg)

2. Beef up the memory & CPU access for docker (trust me you will need it)


