## About The Project

The private docker registry is a small project in order to upload/download your private docker images in your own server.

Here's why:
* You prefer your images to be private.
* To use the Docker API to manage the images.
* Secure access with nginx over HTTP.

Of course, you can pay to Docker for a private docker hub, but with this solution, you can upload/download your private images free.

### References
Above we have the reference links, 
* [Docker Registry](https://docs.docker.com/registry/deploying/)
* [Nginx](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/)

## Getting Started

This is an example of how you may create a private docker registry.

### Prerequisites

This is an example of how to list things you need to use the service and how to install them.
* Docker version 19.03.13
* docker-compose version 1.27.4
<!-- * HTTP Domain, this example has configured "myregistry.com"
* Valid SSL for HTTP Domain -->

### How to Run

1. Clone the repo
```
git clone https://github.com/AguGriguol/private-docker-registry.git
```
2. We have two enviroments, development and production. In console run:

In the project root, build the docker images for development
```
docker-compose -f docker/docker-compose-dev.yml build
```
In the project root, build the docker images for production
```
docker-compose -f docker/docker-compose-prod.yml build
```
3. You can check the built image with the command
```
docker images
```
4. Run the registry
Development
```
docker-compose -f docker/docker-compose-dev.yml up
```
Production (we will run in background with -d option)
```
docker-compose -f docker/docker-compose-prod.yml up -d
```
5. Ready to login you local docker. To test, you must configure your /etc/hosts with myregistry.com to 127.0.0.1 (or server IP)
```
docker login http://myregistry.com
```
The example has configured the follow credentilas:
* username: myregistry
* password: myregistry..

If you want to change then credentials, you must generate "registry.password" file in auth folder. How?

On MacOS: 
```
htpasswd -Bc registry.password [USERNAME]
```

### What's next

* Create a safe access configuration with nginx reverse proxy.

