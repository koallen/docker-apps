# Anaconda v4.0.0

This is a docker container for anaconda and jupyter (ipython).

## Building the container
To build the container, simply type
```bash
$ docker build -t koallen/anaconda:cpu .
```

## Running the container
To run the container, simply type
```bash
$ docker run -d -p 8888:8888 --name anaconda \
             -v ~/workspace:/root/workspace \
             koallen/anaconda:cpu
```

This will open the Jupyter port to the host, and mount a host directory into the container.

## Adding a password for Jupyter
If you want to run this container in a remote environment, you may want to protect your
Jupyter with a password. To do so, pass your password into the container as the environment
variable `PASSWORD`. For example, you may run the following command to add a password `1234`:
```bash
$ docker run -d -p 8888:8888 --name anaconda \
             -v ~/workspace:/root/workspace \
             -e PASSWORD=1234
             koallen/anaconda:cpu
```
