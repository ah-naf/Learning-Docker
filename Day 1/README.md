# What is Docker?
Docker is a platform for packaging, deploying, and running application. Docker application run in **containers** that can be used on any system: a developer's laptop, system on premises, or in the cloud. Which if the application run in local environment then it will run on any environment.

# What is Container?
Containers are a technology that allow us to isolate certein kernal process and trick them into thinking they're the only ones running in a completely new computer. You don't need to have whole different OS installed inside your host OS.  You can have several containers running within a single OS without having several different guest OS's installed.

This makes containers much smaller, faster, and more efficient. While a VM can take about a minute to spin up and can weigh several Gigabytes, a container weighs, on average, 400 to 600mb (the biggest ones).

# How Does Docker Work?
Docker packages an application and all its dependencies in a virtual container that can run on any Linux server. This is why we call them containers. Because they have all the necessary dependencies contained in a single piece of software.

Docker is composed of the following elements:

- a Daemon, which is used to build, run, and manage the containers
- a high-level API which allows the user to communicate with the Daemon,
- and a CLI, the interface we use to make this all available.

# Dockerfile and Image
A Dockerfile is plain-text file that includes instruction that docker uses to package the application into an image. This image contains everything that needs to run an application. An image contains:
- A cut-down operating system
- A runtime environment like node/python
- Application files
- Third-party libraries
- Environment variables

Dockerfile creates an image using dockerfile instruction. We can start a container using an image. 

# Docker in Action
Let us create a new directory called hello-docker and open it using vs-code
```sh
mkdir hello-docker
cd hello-docker
code .
```
We will create a new javascript file called app.js and write some basic code
```js
console.log("Hello Docker!")
```
Typically we can run this app by :
- Start with an OS
- Install Node
- Copy app file (if your willing to run it on another machine)
- Run **node app.js**

If we follow this step will see ***Hello Docker!*** in terminal as a output.

But what if our application is large and it depend on many third-party dependencies and libraries? We might end up with complex release document that had to be precisely followed. This is where docker comes to rescue. We can write this instruction in dockerfile and let docker package our application.

Now we will create a new file in vs-code called **Dockerfile**. 

[***Note*** : It doesn't have any extension and it starts with capital 'D' ]

And write the following instructions in **Dockerfile**. 
```dockerfile
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js
```
<details>
<summary>Some Dockerfile Instructions</summary>
  
* ## FROM
    **FROM** in Dockerfile Instruction used to specify Docker Image Name and start the build process.
    ```Dockerfile
    # Specify a Base Image or Runtime Environment with base image
    FROM ubuntu:latest
    #or
    FROM node:12
    #or
    FROM node:alphine
    ```

* ## MAINTAINER
    **MAINTAINER** in Dockerfile Instruction is used to about the person who creates the Docker Image.
    ```Dockerfile
    MAINTAINER yourmail@gmail.com
    ```

* ## WORKDIR
    **WORKDIR** in Dockerfile Instruction is used to set the working directory.
    ```Dockerfile
    # If directory doesn't exist it will create one.
    WORKDIR /app
    ```

* ## COPY
    **COPY** in Dockerfile Instruction used to Copies a file or directory from your host to Docker image, It is used to simply copying files or directories into the build context.
    ```Dockerfile
    # COPY <source> <destination>
    COPY package*.json .
    # To copy all files
    COPY . .
    ```

* ## RUN
    **RUN** in Dockerfile Instruction is used to execute any commands on top of current Docker Image

    **RUN** executes the command when you are building Image.
    ```Dockerfile
    RUN apt update

    # To install nano in docker container
    FROM ubuntu
    RUN apt update
    RUN apt install nano
    ```

* ## ENV
    **ENV** in Dockerfile Instruction is used to set Environment Variables with key and value.
    ```Dockerfile
    ENV name=ahnaf
    ```

* ## ADD
    **ADD** works same as COPY. However it can also fetch remote URLs, extract TAR/ZIP files, etc. It is used downloading remote resources, extracting TAR/ZIP files.
    ```Dockerfile
    # ADD <source> <destination>
    ADD https://fosstechnix.com/test.tar.xz /home/ubuntu/test/
    ```

* ## EXPOSE
    **EXPOSE** in Dockerfile Instruction is used to specify Network port for Docker container
    ```Dockerfile
    # To Expose port 80 of Docker container
    EXPOSE 80
    ```

* ## USER
    **USER** in Dockerfile Instruction is used to set the user name and UID when running container.
    ```Dockerfile
    USER admin

    # To create new user in Dockerfile and login to user
    RUN adduser -D admin
    USER admin
    ```

* ## CMD
    **CMD** in Dockerfile Instruction is used to execute a command in Running container, There should be one CMD in a Dockerfile.

    **CMD** executes the commands when your Docker Image is deployed.
    ```Dockerfile
    # To start a react-app in container
    CMD ["npm", "start"]
    ```

<hr />
<hr />
</details>

Now we go to the terminal and tell docker to package our application.
```
docker build [OPTIONS] [name of the image] [where docker can find Dockerfile]

docker build -t hello-docker .
```
After running this command we might expect an docker image file inside the current directory. But there is nothing in the directory. An image is not a single file. How docker stores an image is very complex. For now we don't have to worry about what happens in background.

To see all the images on the computer we will execute the following command
```
docker images
or
docker image ls
```
After running the command we will see some ouput with the following column
- **REPOSITORY** : Name of the image that you have given. For this application it will be **hello-docker**.
- **TAG** : Tag is used to versioning our images. By default it will show **latest**.
- **IMAGE ID** : It is a unique identifier for the image you have created.
- **CREATED** : When was the image created.
- **SIZE** : Size of the image.

Now we can run this image on any computer using docker by executing
```
docker run hello-docker
```
We will see **Hello Docker!** in terminal.

Which means we just ran a dockerized app. Next will dockerize a react-app and will learn about other docker command.