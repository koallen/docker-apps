# Docker apps
A collection of applications running in docker containers

## List of applications
- Anaconda (koallen/anaconda:cpu)
- Anaconda with CUDA (koallen/anaconda:gpu)
- MXNet with CUDA
- MXNet with CUDA and Anaconda
- Caffe with CUDA and Anaconda

## Folder naming convention
The names of the folders reflect the inheritance relationship between docker images.

For example, `cuda-anaconda` indicates that the image inherits from a `nvidia/cuda` image (`7.5-cudnn5-devel` in this case), and adds Anaconda. And `cuda-anaconda-caffe` means that the image inherits from the `koallen/anaconda:gpu` image, and adds Caffe.

If the base image is very common such as `ubuntu:14.04`, it's omitted.
