In this workshop, you will containerize the Node.js application.

You may find the reference documentation helpful: https://docs.docker.com/engine/reference/commandline/cli/

#### Write the Dockerfile

In the top window, select `Dockerfile` and click on it to open in the built-in editor.

You may wish to use this as a starting point:

<pre class="file" data-filename="Dockerfile" data-target="replace">
# This is your Editor pane. Write the Dockerfile here and 
# use the command line to execute commands

FROM node:9.5.0

# Install dependencies

</pre>

Note that you don't have to click Save, the editor will automatically save the file as you write it.

#### Create the docker image

Once you've finished writing the `Dockerfile`, change directory to the location of the Dockerfile.

`cd ..`{{execute}}

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
