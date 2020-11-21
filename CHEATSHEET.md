
# CHEATSHEET

	• docker build -t counter-image -f Dockerfile .
	• docker images
	• docker create --name core-counter counter-image
	• Docker ps -a
	• Docker start core-counter
	• Docker ps
	• docker attach --sig-proxy=false core-counter
		--sig-proxy=false parameter ensures that Ctrl+C will not stop the process in the container
	
	• To remove docker image, first stop the container, and then remove the image
	• Docker stop core-counter
	• Docker image rm core-counter [--force]

	• docker run -it --rm --entrypoint "bash" counter-image
		○ Docker run: creates and then starts
		○ --rm: Automatically remove the container when it exits
		○ -it: interactive
	
    • docker run -d -P --name static-site static-site-image
        ○ -d will detach our terminal
        ○ -P will publish all exposed ports to random ports
        ○ --name corresponds to a name we want to give

Now we can see the ports by running the docker port [CONTAINER] command

`docker stop` preserves the container in the `docker ps -a` list (which gives the opportunity to commit it if you want to save its state in a new image).
It sends SIGTERM first, then, after a grace period, SIGKILL.

docker `rm` will remove the container from `docker ps -a` list, losing its "state" (the layered filesystems written on top of the image filesystem)

https://www.tutorialspoint.com/docker/docker_working_with_containers.htm
https://docker-curriculum.com/
	
	1. Docker run <image>
		a. Docker run -it ubuntu bash
	2. Docker rmi <imageID>
	3. Docker images
	4. Docker inspect <image>
	5. Docker ps (currently running containers)
	6. Docker ps -a (all containers)
	7. Docker history <imageID>
	8. Docker stop <containerID>
	9. Docker rm <containerID>
    10. Docker network ls

---------
Docker networking

docker network create -d bridge -subnet 10.0.0.1/24 my-nw
docker network inspect my-nw
docker network ls
docker run -dt --name container1 --network my-nw alpine sleep 1d
docker run -dt --name container2 --network my-nw alpine sleep 1d
docker exec -it container1
*# ip a
*# ping 10.0.0.2 OR ping container2



---------
## [Docker RUN vs CMD vs ENTRYPOINT](https://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/#:~:text=ENTRYPOINT%20instruction%20allows%20you%20to,runs%20with%20command%20line%20parameters.)
###  In a nutshell
* RUN executes command(s) in a new layer and creates a new image. E.g., it is often used for installing software packages.
* CMD sets default command and/or parameters, which can be overwritten from command line when docker container runs.
* ENTRYPOINT configures a container that will run as an executable.

### The bottom line
* Use RUN instructions to build your image by adding layers on top of initial image.
* Prefer ENTRYPOINT to CMD when building executable Docker image and you need a command always to be executed. Additionally use CMD if you need to provide extra default arguments that could be overwritten from command line when docker container runs.
* Choose CMD if you need to provide a default command and/or arguments that can be overwritten from command line when docker container runs.

