# slam-docker
Dockerfiles for various SLAM frameworks.


## ORB_SLAM2

Docker image for running ORB_SLAM2 based on Ubuntu 16.04 and ROS Kinetic with OpenCV3

Pull from dockerhub: `docker pull awilby/orbslam2`

Or, build from Dockerfile: `docker build - < Dockerfile -t orbslam2:latest`

Run without network isolation between container and host so host can see ROS nodes. Also, mount a volume (e.g. containing datasets) by editing fields after -v flag:

```
docker run -it --rm -e DISPLAY=$DISPLAY --network host -v /host/path:/container/path orbslam2:latest
```


Note: this does not currently work with Pangolin Viewer due to some X11 issue. Giving docker access to x-server via `xhost +local:docker` does not work, nor do any of the fixes in the Pangolin Github issue tracker. Only works with ROS for now.


## LSD SLAM

Docker image for running LSD SLAM based on Ubuntu 14.04 and ROS Indigo

Build and tag: `docker build - < Dockerfile -t lsdslam:latest`

Run: todo
