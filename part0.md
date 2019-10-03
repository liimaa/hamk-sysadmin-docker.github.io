---
layout: page
title: Part 0
inheader: yes
permalink: /part0/
order: 0
---

## General ##

This course is an introductory course to Docker and docker-compose. The course will also look into what different parts web services consist of, such as reverse proxies, databases, etc. Docker can not be installed on faculty computers, so students will need to provide their own computers to follow the examples outlined in this course material and to complete the exercises.

### Prerequisites ###

Attendees need to provide their own computers with admin/superuser priviledges. Attendees are also expected to have a general understanding of software development and experience with a CLI of their choice.

### Course material ###

The course material is meant to be read sequentially, part by part, from start to finish. To get a passing grade you have to complete each exercise, although one exercise can be skipped for each part. Some of the exercises are marked as mandatory and those can not be skipped. The exercises are placed in the material in such a way that you will have learned the necessary skills from the material prior to each given exercise. You can do the exercises as you're going through the material.

The course material is written for Ubuntu, so some instructions may lack platform specific details.

### Completing course ###

The course is composed of 4 parts, first of which is part 0 and contains the pre-requisites for all the upcoming exercises. The parts should take 5-25 hours each to complete.

This forked Course is only for self learning and being part of normal university education. If you are interested to get MOOC credits we recommend Helsinki university course <https://courses.helsinki.fi/en/aytkt21025en/129059389> /  <https://docker-hy.github.io/>


### Learning objectives ###

Part 1

Can explain what images and containers are and how they're related.
Can build images with Docker for existing projects and run them.

Part 2

Can manage complex multi-container applications with docker-compose.

Part 3

Can optimize images sizes and security for production.
Knows why docker-compose is not an optimal production solution and what is.

	
Part 4 Rocket.Chat

We will do an assignment where we go through the all topics of course


## Installing Docker ##

Use the official documentation to find download instructions for docker-ce for the platform of your choice:

[Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

[MacOS](https://docs.docker.com/docker-for-mac/install/)



Confirm that Docker installed correctly by opening a terminal and running `docker -v` to see the installed version.


## Installing docker-compose ##

During the writing of these materials, both MacOS and Windows have docker-compose included in their respective Docker packages.

Use the official documentation to find download instructions for docker-compose for the platform of your choice:

[Install instructions](https://docs.docker.com/compose/install/)

Confirm that docker-compose installed correctly by opening a terminal and running `docker-compose -v` to see the installed docker-compose version.

> TIP: To avoid writing sudos you may consider [adding yourself to docker group](https://docs.docker.com/install/linux/linux-postinstall/)

### First exercise ###

Do the first exercise over **[here](/exercises/#part-0)**

