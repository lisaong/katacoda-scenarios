### Install Keras

We will launch a docker container with a [keras image](https://hub.docker.com/r/lisaong/jupyter-keras-cpu-py3/). The image is hosted on *Docker hub* and has already been downloaded to this environment.

Run the following command in the Terminal:

`docker run -d -p=6006:6006 -p=8888:8888 -v=/srv/notebooks:/srv lisaong/jupyter-keras-cpu-py3:v1`{{execute}}

This command takes a while to run the first time, because it will download the docker image containing Keras and Jupyter. Once download is complete, the docker image will run, which launches a Jupyter notebook server.