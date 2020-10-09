# Docker: Step by step

## 1. Static-html-page

* Switch to Linux container for nginx

### To consume
```
1. docker pull paritosh64ce/static-html-page:latest
2. docker run -d -p 80:80 --name my-static-page paritosh64ce/static-html-page
```

* Navigate to http://localhost/ to verify that NGINX is running
* Navigate to http://localhost/hello-world.html

* Once done, check container ID with `docker ps` and then `docker stop <containerID>`, `docker rm <containerID>` to remove the container.

### To make changes and build
```
* cd static-html-page
* docker build -t <your-image-name> .
```

## 2. Hello node

### To consume
```
1. docker pull paritosh64ce/hello-node
2. docker run paritosh64ce/hello-node
```

* cd hello-node
* docker build -t paritosh64ce/hello-node .

## 3. Hello dot-net-core

### To consume
```
1. docker pull paritosh64ce/hello-dotnet-core 
2. docker run paritosh64ce/hello-dotnet-core
```
### To make changes and build
```
* cd hello-dotnet-core
* docker build -t paritosh64ce/hello-dotnet-core .
```

* Once done, check container ID with `docker ps` and then `docker stop <containerID>`, `docker rm <containerID>` to remove the container.

## 4. Hello microservice

### To consume
```
1. docker pull paritosh64ce/hello-ms:latest
2. docker run -it -p 5000:80 --name my-microservice paritosh64ce/hello-microservice
```

* Navigate to http://localhost:5000/WeatherForecast to verify that we are getting JSON result

* Now keep this image running

### To make changes and build
```
* cd hello-microservice
* docker build -t <your-image-name> .
```

## 5. Hello Angular

### To consume
```
1. docker pull paritosh64ce/hello-angular:latest
2. docker run -it -p 5000:80 --name my-angular paritosh64ce/hello-angular
```

* Navigate to http://localhost:5000/ to verify that our Angular application is working

### To make changes and build
```
* cd hello-angular
* docker build -t <your-image-name> .
// this takes too much time. Not worth the effort tbh
```



# TODO:

* Host a simple dotnet REST microservice, which call some free open microservice
* dotnet core app with sql server in different docker image
* host two microservices in different images, and establish communication with proper message-bus
