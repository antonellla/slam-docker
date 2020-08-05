## Dockerfile for ORB_SLAM2 on Ubuntu 18.04 with ROS Kinetic

# Ubuntu 16.04 base image with ROS Kinetic
FROM ros:kinetic-ros-base-xenial
MAINTAINER Antonella Wilby <awilby@eng.ucsd.edu>


RUN apt-get update && apt-get upgrade -y

# Install bootstrap tools & other dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
	build-essential \
	python-rosdep \
	python-rosinstall \
	python-vcstools \
	wget \
	git \
	vim \
	tmux \
	unzip \
	cmake \
	libopencv-dev \
	libgl1-mesa-dev \
	libglew-dev=1.13.0-2* \
	libpython2.7-dev \
	&& rm -rf /var/lib/apt/lists/*


# Install ROS Kinetic base and perception packages
RUN apt-get update && apt-get install -y --no-install-recommends \
	ros-kinetic-ros-base=1.3.2-0* \
	ros-kinetic-perception=1.3.2-0* \
	&& rm -rf /var/lib/apt/lists/*


# Install Pangolin
RUN git clone https://github.com/stevenlovegrove/Pangolin.git
RUN cd Pangolin \
	&& mkdir build && cd build \
	&& cmake .. -DCMAKE_BUILD_TYPE=Release \
	&& make -j$(nproc) && make install


# Install Eigen
RUN wget https://gitlab.com/libeigen/eigen/-/archive/3.3.7/eigen-3.3.7.tar.gz
RUN mkdir /usr/include/eigen \
	&& tar -xf eigen-3.3.7.tar.gz --strip-components=1 -C /usr/include/eigen \
	&& rm eigen-3.3.7.tar.gz


# Build & install ORBSLAM2 and orbslam2 ROS package
RUN git clone https://github.com/awilby/ORB_SLAM2.git ORB_SLAM2			# Repo with fix for boost error when building orb_slam2 ROS package
RUN cd ORB_SLAM2 \
	&& chmod +x build.sh \
	&& ./build.sh
RUN cd ORB_SLAM2 \
	&& . /opt/ros/kinetic/setup.sh \
 	&& export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:/ORB_SLAM2/Examples/ROS \
	&& chmod +x build_ros.sh \
	&& ./build_ros.sh
