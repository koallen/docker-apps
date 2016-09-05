# Anaconda v4.0.0

This is a docker container for Anaconda and Jupyter (IPython).

## Running the container
To run the container, simply type
```bash
$ docker run -d -p <your port>:8888 --name anaconda \
             -v <your directory>:/root/workspace \
             koallen/anaconda:cpu
```
Some explanation for the flags:
- `-d` is to run the container as a daemon
- `-p` is to map port 8888 of the container to a port on your machine (Jupyter is running on port 8888)
- `-v` is to mount a directory on your machine to the container

## Adding a password for Jupyter
If you want to run this container in a remote environment, you may want to protect your
Jupyter with a password. To do so, pass your password into the container as the environment
variable `PASSWORD`:
```bash
$ docker run -d -p <your port>:8888 --name anaconda \
             -v <your directory>:/root/workspace \
             -e PASSWORD=<your password>
             koallen/anaconda:cpu
```
