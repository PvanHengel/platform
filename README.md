# Platform In A Box
This repo outlines a "simple" implementation of a platform in a box.  Modern applications require a common set of core capabilities that can scale as you scale.  Cloud providers such as AWS, MS AZure and Google GCP, provide some/all of these as a service, which you can mix and match.  The below is a way for you to get farmiliar (also 'free') with a fully functional and scalable system.  Its a good place to begin your journey if you working as one, or one in a team of thousands that needs to trasform the way they develop software.  All you need is a decent powered Mac (or access to linux box on cloud provider of your picking), some time, coffee (and beer/wine).  


## Core Capabilities

Container Managament - Docker Swarm - for this implementation we will use a local instance of docker swarm, but suggest others such as EKS, K8 (kube provider), etc.
    
Admin Dashboard - Portainer.io - a consolidated GUI to view high level platform stats
     
    portainer/agent
    portainer/portainer-ce
    
Service Discovery & Load Balancing - HAProxy, Remco, Registrar, ETCd, etcdKeeper - a collection of tools, to keep an eye on containers, and setup proper routing rules

    gcr.io/etcd-development/etcd
    gliderlabs/registrator
    evildecay/etcdkeeper
    haproxy **
        For HAProxy, we will build a custom image with some cool stuff we need
        rsyslog to get logs from HAProxy to LogStash
        lua script to parse JWT access token into log file (for user based metrics)
        Remco https://heavyhorst.github.io/remco/details/ so we can pull services from ETCD into config file for service registry
        
    
Logging & Metrics - Elastic Stack - a collection of key tools to provide a vast array of aggregation & reporting capabilities
    (Elastic Search, FileBeat, Log Stash, Kibana, APM)
    You might want Kafka & Zookeeper too
    
    docker.elastic.co/elasticsearch/elasticsearch:7.10.0
    docker.elastic.co/kibana/kibana:7.10.0
    docker.elastic.co/logstash/logstash:7.10.0
    docker.elastic.co/apm/apm-server:7.10.0
    docker.elastic.co/beats/filebeat:7.10.0
    
    TODO: Kafka & ZooKeeper (can be added later but not required)
    
Binary & Library Managament - Nexus - a place to store all our images, and shared libraries (could use artifactory or code artifact & ecr)

    sonatype/nexus3
    
CI/CD - Jenkins - (depends on SoCat) a tool to automate our CI/CD pipelines and manage the container build process
    
    jenkins/jenkins:lts **
        We use a custom docker image, to add some important plugins and configs to get this running on swarm, with dynamic worker nodes
     
Scheduling / Coordionation - Apache Airflow (depends on GitSync)
    
    openweb/git-sync:0.0.1
    akkids/airflow:blog1 **
        We will setup a local image, but this blog article's image is great for what we need to get started
    
    
Database - Postgres & Redis
    
    postgres:9.6-alpine
    dpage/pgadmin4:latest
    
    redis:latest
    rediscommander/redis-commander:latest
    
Messaging - RabbitMQ - a simple easy to cluster message broker supported by many languages & framework
  
  gsantomaggio/rabbitmq-autocluster:latest
  
Testability - Selenium 

    selenium/node-chrome:
    selenium/node-firefox:
    selenium/node-opera:
    selenium/hub:
    
Languages - While you can develop in just about any language and framework you wish the following are great starting points:
  Front End - Javascript / ReactJS & ReactNative
  API - Python Flask, Java SpringBoot, NodeJS Express
  
  
  
## Getting Started

1. Download and install Docker Desktop on your Mac (https://desktop.docker.com/mac/stable/Docker.dmg)

2. Beef up the memory & CPU access for docker (trust me you will need it)


