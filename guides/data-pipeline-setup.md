---
explains: Setting up a docker analysis project
---

# Setting up

## Introduction
This document describes a common workflow for the analists how to get up-and-running and have a quickstart for their 
particular projects using Dockers. It is not meant as an encompassing document but rather as way a standardized proposal to work and save time.

## How we use docker and docker-compose

A lot of the [open source code software of the City of Amsterdam]((https://github.com/Amsterdam)) uses docker containers.
Seperate tasks are normally organised in seperate dockers.

In general we follow common community guidelines:
- [Dockerfile best practices](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
, including multi-stage builds

Preferably use [docker-ce](https://www.docker.com/community-edition)
and [docker-compose](https://docs.docker.com/compose/), most recent version

`.dockerignore` files are used to exclude files that are not relevant to the build.
Ideally this file starts by ignoring everything (`*`) and then explicitly add the files that belong to the build
by means of exceptions (e.g. `!**\*.py` to include all python source files).
Most often you will however find .dockerignore files that only specify files that are not part of the build. 

## Install procedure for a project. 

**install docker**
First check your OS version. 
For Windows users the 10 Home editions use Docker Toolbox, a Legacy desktop solution intended for older for older Mac and Windows systems that do not meet the requirements of Docker for Mac and Docker for Windows. It is recommended upgrading to newer applications, if possible and for Windows users to upgrade to PRO. Windows: https://docs.docker.com/toolbox/toolbox_install_windows/ . This toolbox run on Oracle VirtualBox VM and is therefore a lot slower than the following install solution. 

Windows 10 PRO: download Docker for Windows PC Community Edition from the Docker Store.  https://www.docker.com/docker-windows 
download and install <a href="https://www.docker.com">docker</a></br>

To get started with Docker, see [starting guide](https://docs.docker.com/get-started/)

**build postgreSQL data base image**

```
git clone https://github.com/Amsterdam/schoonmonitor.git schoonmonitor
cd schoonmonitor
docker-compose build database
docker-compose up database
```

This builds a postgres Image from the public repository of Docker Hub (https://hub.docker.com/r/amsterdam/postgres/)
based on a build context stored in the offical repository https://github.com/Amsterdam/docker. A build context is a Dockerfile and any files at a specific location. For an automated build, the build context is a repository containing a Dockerfile.

Create a local environment and activate it:
```
virtualenv --python=$(which python3) venv
source venv/bin/activate
```

**build importer**

Instantiate a new docker client to import project specific data
general components include:
  - download_from_objectstore.py
  - etc....
  
Set the openstack config in auth.conf by using and renaming auth.conf-example and set the openstack password in your environment:
```
SET ENV EXTERNAL_DATASERVICES_PASSWORD = yourpassword
```
or on Unix
```
export EXTERNAL_DATASERVICES_PASSWORD = yourpassword
```

In the docker client run:

## Where do we store code**

Every project should share reproducible code. We distinguish between sensitive projects (like for privacy sensitive projects) and 
projects with data that is not particularly sensitive.

- code should be pushed to github.com/amsterdam with the exception of privacy-sensitive projects that are hosted on our own closed git at git.datapunt.amsterdam.nl https://git.datapunt.amsterdam.nl/
- We also publish code snippets as gists on https://gist.github.com publicly but in that case make sure you add the following tag 
  to the snippet: #AmsterdamCityData




