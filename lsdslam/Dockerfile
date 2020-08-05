## Dockerfile for LSDSLAM on Ubuntu 14.04 with ROS Indigo 

# Ubuntu 14.04 base image with ROS Indigo
FROM ros:indigo-ros-core-trusty
MAINTAINER Antonella Wilby <awilby@eng.ucsd.edu>

RUN apt-get update && apt-get upgrade -

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    liblapack-dev \
    libblas-dev \
    freeglut3-dev \
    libqglviewer-dev \
    libsuitesparse-dev \
    libx11-dev


# Install ROS Indigo base
RUN apt-get update && apt-get install -y --no-install-recommends \
    ros-indigo-ros-base=1.1.6-0* \
    ros-indigo-libg2o \
    ros-indigo-cv-bridge \
    && rm -rf /var/lib/apt/lists/*


# Install LSD SLAM
