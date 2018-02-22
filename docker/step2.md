In this step, you will containerize the Node.js application.

#### Stop the Node application

In the terminal window, do `Ctrl+C` to stop the node process. Instead, we will walk through how to run the same application in a container.

#### Create a new Dockerfile

First, create an empty Dockerfile:

`touch Dockerfile`{{execute}}

#### Author the Dockerfile

In the top window, click the Refresh button (circular double arrows) to refresh the folder view. Expand the `acd_docker_workshop` folder, select `Dockerfile` and click on it to open in the built-in editor.

You can use this as a starting point:

<pre class="file" data-filename="Dockerfile" data-target="replace">
# This is your Editor pane. Write the Dockerfile here and 
# use the command line to execute commands

FROM node:9.5.0

# Install dependencies

</pre>

Note that you don't have to click Save, the editor will automatically save the file.

#### Create the docker image

Once the `Dockerfile` is completed, create the docker image. Replace `myusername` with an account name (no spaces or special characters) for yourself. We won't be uploading this to Docker Hub, so you can pick any name for now.

`v1` is the version number.

`docker build -t myusername/acdfortune:v1 .`{{execute}}

#### Run the docker image

`docker run -d myusername/acdfortune:v1`{{execute}}

The docker container will be listening on port 8080. You can visit it via the URL:
https://[[CLIENT_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

#### Delete the docker image

As an exercise, see if you can figure out how to:
* list running docker containers
* stop the docker container
* delete the docker container

You may find the reference documentation helpful: https://docs.docker.com/engine/reference/commandline/cli/