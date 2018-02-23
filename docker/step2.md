In this workshop, you will containerize the Node.js application.

You may find the reference documentation helpful: https://docs.docker.com/engine/reference/commandline/cli/

#### Write the Dockerfile

First, we'll create two empty files:

`touch Dockerfile`{{execute}}
`touch .dockerignore`{{execute}}

In the top (file browse) pane, click the refresh icon (looks like a circle), expand the `acd_docker_workshop`. Select `Dockerfile` and click on it to open in the editor.

You may wish to use this as a starting point:

<pre class="file" data-filename="Dockerfile" data-target="replace">
# This is your Editor pane. Write the Dockerfile here and 
# use the command line to execute commands

FROM node:9.5.0

# Install dependencies

</pre>

Note that you don't have to click Save, the editor will automatically save the file as you write it.

#### Create .dockerignore

Select `.dockerignore` and click on it to open in the editor. Paste the following lines into that file

<pre class="file" data-filename=".dockerignore" data-target="replace">
node_modules
npm-debug.log
package-lock.json
</pre>

#### Create the docker image

Enter the Docker command to build the image in the Terminal. Tag your image with your Docker Hub account name, your image name (call it `acdfortune`) and a version (e.g. `v1`).

#### Run the docker image

Run the image that you have just built. Bind the container’s port to 8080 on the host. 

#### View the running container

Enter the Docker command to view your container in the Terminal.

#### Test the docker

Test the deployed application by clicking this link:
https://[[CLIENT_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

#### Delete the container

Enter the Docker command(s) to delete the `acdfortune` container in the Terminal.

#### Upload to DockerHub

Share your image with the world. Push your image to Docker Hub.
