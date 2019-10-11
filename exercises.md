---
layout: page
title: Exercises
inheader: yes
permalink: /exercises/
order: 1
---

[Part 1](#part-1) [Part 2](#part-2) [Part 3](#part-3)[Part 4](#part-4)



## Intro

Remember to start reading from **[here](https://hamk-sysadmin-docker.github.io/part0/)** before starting to do exercises.

Docker documentation is available at [https://docs.docker.com/engine/reference/run/](https://docs.docker.com/engine/reference/run/)



## Part 1, Basics ##

Part 1 exercises were created by [Jami Kousa](https://github.com/jakousa) 

### 1.1 ###

Practice the commands.

Start 3 containers from image that does not automatically exit, such as nginx, detached.

Stop 2 of the containers leaving 1 up.

Prove that you have completed this part of exercise by delivering the output for docker ps -a.

### 1.2 ### 

We've left containers and a image that won't be used anymore and are taking space, as `docker ps -a` and `docker images` will reveal.
Clean the docker daemon from all images and containers.

Prove that you have completed this part of exercise by delivering the output for `docker ps -a` and `docker images`

### 1.3 ###

Start image `devopsdockeruh/pull_exercise` with flags `-it` like so: `docker run -it devopsdockeruh/pull_exercise`. It will wait for your input. Navigate through [docker hub](https://hub.docker.com/r/devopsdockeruh/pull_exercise) to find the docs and Dockerfile that was used to create the image.

Read the Dockerfile and/or docs to learn what input will get the application to answer a "secret message".

Submit the secret message and command(s) given to get it as your answer.

### 1.4 ###

Now that we've warmed up it's time to get inside a container while it's running!

Start image `devopsdockeruh/exec_bash_exercise`, it will start a container with clock-like features and create a log. Go inside the container and use `tail -f ./logs.txt` to follow the logs. Every 15 seconds the clock will send you a "secret message".

Submit the secret message and command(s) given as your answer.

### 1.5 ### 

Start a ubuntu image with the process `sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'`

You will notice that a few things required for proper execution are missing. Be sure to remind yourself which flags to use so that the read actually waits for input.

> Note also that curl is NOT installed in the container yet. You will have to install it from inside of the container.

Test inputting `helsinki.fi` into the application. It should respond with something like

```
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
```

This time return the command you used to start process and the command(s) you used to fix the ensuing problems.

> This exercise has multiple solutions, if the curl for helsinki.fi works then it's done. Can you figure out other (smart) solutions?

**For the following exercises, return both Dockerfile(s) and the command you used to run the container(s)**

### 1.6 ###

Create a Dockerfile that starts with `FROM devopsdockeruh/overwrite_cmd_exercise` and works only as a clock.

The developer has poorly documented how the application works. Passing flags will open different functionalities, but we'd like to create a simplified version of it. You can view flags from [github repo](https://github.com/docker-hy/overwrite_cmd_exercise) or by passing empty CMD to Dockerfile, like so.

```
FROM ...
CMD []
```

Add a CMD line to the Dockerfile and tag it as "docker-clock" so that `docker run docker-clock` starts the application and the clock output. You will need to use [Docker run reference](https://docs.docker.com/engine/reference/run/)

### 1.7 ### 

Now that we know how to create and build Dockerfiles we can improve previous works.

Make a script file for `echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;` and run it inside the container using CMD. Build the image with tag "curler".

Run command `docker run [options] curler` (with correct flags again, as in 1.5) and input helsinki.fi into it. Output should match the 1.5 one.

### 1.8 ###

In this exercise we won't create a new Dockerfile. 
Image `devopsdockeruh/first_volume_exercise` has instructions to create a log into `/usr/app/logs.txt`. Start the container with bind mount so that the logs are created into your filesystem.

Submit your used commands for this exercise.

### 1.9 ###

In this exercise we won't create a new Dockerfile. 
Image `devopsdockeruh/ports_exercise` will start a web service in port `80`. Use -p flag to access the contents with your browser.

Submit your used commands for this exercise.


### 1.10 ### 

Create an image that contains your favorite CMS environment in it's entirety. Example of CMS software is wordpress
This means that a computer that only has docker can use the image to start a container which contains all the tools and libraries. 

Explain what you created and publish it to Docker Hub.


## Ending ##





## Part 2, docker-compose ##
Part 2 exercises were created by [Jami Kousa](https://github.com/jakousa) and [Sasu Mäkinen](https://github.com/sasumaki)

*Do not alter the code of the projects, unless by pull-requests to the original projects*

*Exercises in part 2 should be done using docker-compose*

### 2.1 ###

Container of `devopsdockeruh/first_volume_exercise` will create logs into its `/usr/app/logs.txt`.

Create a docker-compose.yml file that starts `devopsdockeruh/first_volume_exercise` and saves the logs into your filesystem.

Submit the docker-compose.yml, make sure that it works simply by running `docker-compose up`



### 2.2 ###

`devopsdockeruh/ports_exercise` starts a web service that will answer in port `80`

Create a docker-compose.yml and use it to start the service so that you can use it with your browser.

Submit the docker-compose.yml, make sure that it works simply by running `docker-compose up`

### 2.3 ###

A project over at <https://github.com/docker-hy/scaling-exercise> has a hardly working application. Go ahead and clone it for yourself. The project already includes docker-compose.yml so you can start it by running `docker-compose up`.

Application should be accessible through <http://localhost:3000>. However it doesn't work well enough and I've added a load balancer for scaling. Your task is to scale the `compute` containers so that the button in the application turns green.

This exercise was created with [Sasu Mäkinen](https://github.com/sasumaki)

``` git clone ``` clones repositories.

### 2.4 ### 

Postgres image uses volume by default. Manually define volumes for the database in convenient location such as in `./database` . Use the image [documentations(postgres)](https://hub.docker.com/_/postgres) to help you with the task. You may do the same for redis as well.

After you have configured the volume:

* Save a few messages through the frontend
* Run `docker-compose down`
* Run `docker-compose up` and see that the messages are available after refreshing browser
* Run `docker-compose down` and delete the volume folder manually
* Run `docker-compose up` and the data should be gone

Maybe it would be simpler to back them up now that you know where they are.

> TIP: To save you the trouble of testing all of those steps, just look into the folder before trying the steps. If it's empty after docker-compose up then something is wrong.

> TIP: Since you may have broken the buttons in nginx exercise you should test with docker-compose.yml from before it

Submit the docker-compose.yml



## Ending ##




# Part 3, Security
Part 3 exercises were created by [Jami Kousa](https://github.com/jakousa) 


### 3.1 ###


Security issues with the user being a root are serious for the example frontend and backend as the containers for web services are supposed to be accessible through the internet.

Make sure the containers start their processes as a non-root user.

> TIP `man chown` may help you if you have access errors

### 3.2 ### 

Document the image size before the changes.

Rather than going to FROM alpine or scratch, lets go look into [docker-node](https://github.com/nodejs/docker-node) and we should find a way how to run a container that has everything pre-installed for us. Theres even a [best practices guide](https://github.com/nodejs/docker-node/blob/master/docs/BestPractices.md)

Return back to our Youtube exercise (First docker-compose.yml) and change the FROM to something more suitable. Make sure the application still works after the changes.

Document the size after this change. If you used the alpine version the size for frontend can be less than 250MB. The backend can be below 150MB.



## Ending ##

