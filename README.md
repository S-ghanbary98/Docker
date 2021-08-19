# Docker

![docker icon](image.png)


##### What is Docker?

- Docker is an open platform for developing, shipping, and running applications. 
- Docker enables you to separate your applications from your infrastructure, so you can deliver software quickly.
-  With Docker, you can manage your infrastructure in the same ways you manage your applications.


#### Installation

- To install first you need to create an account and verify your email.
- Install the version specific to the operating system you are using.
- Run the following command in the terminal `docker run -d -p 80:80 docker/getting-started`.

#### Docker Dashboard

- The Docker Dashboard, which gives you a quick view of the containers running on your machine.
- You can also see all the logs of the containers.

#### Benefits

- <strong>Performance :</strong> containers do not contain an operating system whereas VMs do so containers are faster to create and quicker to start.
- <strong>Scalability :</strong> You are able to create new containers quickly and on demand per your application requirements. You can take full advantage of a range of container management options.
 - <strong>Isolated :</strong> Docker containers are totally independent of one other. So the images you create at various stages of the development lifecycle will perform exactly the same as it moves through testing and potentially to your users.
- <strong>Portability :</strong> Once containerized application is tested it can be deployed to any other system where docker is running, and the application will perform the same.


### Microservices Architecture

- Microservices architecture is an approach where a single application is composed into many loosely coupled independent components or services.
- These services have their own tech stack, database, data management model.
- These services communicate via APIs, event handlers and message brokers.


#### Microservices Architecture vs monolithic architecture

- While a monolithic application is a single unified unit, a microservices' architecture breaks it down into a collection of smaller independent units.
- Monolithic architecture does have its own benefits. For example, it's easier to test, simpler to develop, easy to deploy.
- monolithic architecture also has a range of drawbacks which include, being to complex to understand if application is big, Bad start up time, size can slow application, continuous deployment is difficult. Just to name a few.
- For small application monolithic architecture is ideal, for larger more complex application Microservices Architecture takes the win.


### Docker Documentation and Command

- We can run the documentation and see it on the `localhost:4000`
- We do this by first running the command `docker pull -d -p 4000:4000 docs/docker.github.io`.

```
    ##### Additionals
    -d          ===>         Detach so we get the command line while downloading
    -p          ===>         Port Number to run on
    
    
    ### COMMANDS
    docker run -d -p <PORT> <SERVICE>     =====>    run a container
    docker ps -a                          =====>    See all running containers
    docker stop <ID>                      =====>    Stop container with id <ID>
    docker rm <ID> -f                     =====>    Force Destroy container with id <ID>
    docker exec -it <ID> sh               =====>    Enter container
    docker push <IMAGEID NAME>            =====>    Push image to docker hub repository
    docker rmi <IMAGEID?                  =====>    Delete Image
    +
    
```



- We can see it running by typing the command `docker ps` this will give the container id and all running containers.

### Running Nginx

- We can also run nginx and see it displayed on local host via the `docker run` command.
- We run `docker run -d -p 80:80 nginx`.
- We can now se nginx displayed on the web at `localhost:80`.

### Displaying Static HTML Using NGINX

- This task involves creating a static html file called 'index.html'.
- We will use this to create our own image and run a docker container.
- If successful we should see the static web pages displayed on the localhost.

##### Creating Docker Image

- Firstly we have to create a docker file, so we can build the image.
- We will build the image to automate the tasks.
 

```
#### DOCKERFILE

FROM nginx

COPY app /usr/share/nginx/html          ### Copy files from app folder into container
 

LABEL MAINTANER=shervin

# Adding the port
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

- Build the image via `docker build -t sherv1360/nginx`.
- You can see all the images via `docker images`.
- Now you can run the container via `docker run -d -p 50:80 sherv1360/nginx`.
- The static website is now visible on localhost:50.



### Creating Volumes 

- Volumes allow for real-time syncing between the localhost and the container.
- For nginx this can be done via the command `docker run -d -v <PWD OF INDEX.HTML>:/usr/share/nginx/html -p 5000:80 sherv1360/nginx`.

```python
docker run -d -v /Users/shervin888/dock/app:/usr/share/nginx/html -p 5000:80 sherv1360/nginx
```