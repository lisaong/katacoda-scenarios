### Install Keras

We will launch a docker container with a [keras image](https://hub.docker.com/r/gw000/keras-full/). The image is hosted on *Docker hub* and has already been downloaded to this environment. More details on this docker image can be found [here](http://gw.tnode.com/docker/keras-full/).

Run the following command in the Terminal:

`docker run -d -p=6006:6006 -p=8888:8888 -v=.:/srv gw000/keras-full`{{execute}}

This command takes a while to run the first time, because it will download the docker image containing Keras and Jupyter. Once download is complete, the docker image will run, which launches a Jupyter notebook server.

### Run tutorial in Jupyter

Click on the `Jupyter` tab. Enter `keras` as the password.

Double-click on `tutorial.ipynb` to run the tutorial.
