In this step, you will clone, deploy, and run a Node.js application.

#### Clone the application from its repository

`git clone https://github.com/chukmunnlee/acd_docker_workshop.git`{{execute}}

#### Change into the repository directory

`cd acd_docker_workshop`{{execute}}

#### Install the required dependencies

`npm install`{{execute}}

#### Run the Node application

`node main.js`{{execute}}

The application will be listening on port 3000. You can visit it by clicking on this link:
https://[[CLIENT_SUBDOMAIN]]-3000-[[KATACODA_HOST]].environments.katacoda.com/

#### Stop the Node application

In the terminal window, do `Ctrl+C` to stop the node process. Next, we will walk through how to run the same application in a container.
