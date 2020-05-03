# Transformer

## Setup

### Base Image
We are going to use the continuum io anaconda 3 2020.02 base image.
This one comes with Anaconda already installed and will give us enough tools to
mess around.

* https://github.com/ContinuumIO/docker-images

If you want to have an environment with Tensorflow (or something else) already
install checkout the images from 

* https://github.com/jupyter/docker-stacks

### Getting Started

All youneed to do to get a Jupyter notebook up and running is to run the
following command
```
docker build -t lab . && docker run --rm -it -v "$PWD:/lab" -p 8888:8888 lab
```

If you check the [Dockerfile](./Dockerfile), this is the command we are running
behind the scenes:
```
jupyter notebook --allow-root --ip=0.0.0.0
```
Notice that we are using the `--allow-root` flag.
We are intentionally leaving the container to run as root in order to allow
people to do things.

If you want to distribute something like this to other people, you can always
do something like
```
USER nobody
```
Most Linux-based ysstems will have a `nobody` user.

Anyhhot, the previous docker run command will give a lot of output but the last
part is the thing that matters the most.
You should see some urls being thrown around, copy and paste into your browser
the one that makes use of localhost - it will haave something like
http://127.0.0.1:8888 or http://0.0.0.0:8888.

Some other useful flag to use is `--cpus` this will prevent your container from
taking your machine over.
For example,

```
docker build -t lab .

docker run --rm -it -v "$PWD:/lab" -p 8888:8888 --cpus="6.5" lab
```

There is also an `-m` flag for setting a memory limit (i.e., `-m 4g`).

### Requirements

In order to get the for this writeup working we had to install the following
dependencies:
```
conda install tensorflow-datasets
```

For the full list of dependencies see [requirements.txt](./requirements.txt).
## References
* Attention Is All You Need https://arxiv.org/abs/1706.03762
