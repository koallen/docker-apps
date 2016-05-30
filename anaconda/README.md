# Anaconda v4.0.0

This is a docker container for anaconda and jupyter (ipython).

## Building the container
To build the container, simply type
```
docker build -t koallen/anaconda .
```

## Running the container
To run the container, simply type
```
docker run -d -p 8888:8888 --name anaconda -v ~/workspace:/root/workspace koallen/anaconda
```

This will open the Jupyter port to the host, and mount a host directory into the container.

## Adding a password for Jupyter
If you want to run this container in a remote environment, you may want to protect your
Jupyter with a password. To do so, go to this [web page](http://online-code-generator.com/sha1-hash-with-optional-salt.php).
Choose your password and add a salt *after* your password. Then, edit `jupyter_notebook_config.py` accordingly. (You should
be able to find the password setting)
