# slam-docker
Dockerfiles for various SLAM frameworks.


## ORBSLAM2

Docker image for running ORBSLAM2 based on Ubuntu 16.04 and ROS Kinetic with OpenCV3

Build and tag: `docker build - < Dockerfile -t orbslam2:latest`

Run without network isolation between container and host so host can see ROS nodes. Also, mount a volume (e.g. containing datasets) by editing fields after -v flag:

```
docker run -it --rm -e DISPLAY=$DISPLAY --network host -v /host/path:/container/path orbslam2:latest
```


Note: this does not currently work with Pangolin Viewer due to some X11 issue. Giving docker access to x-server via `xhost +local:docker` does not work, nor do any of the fixes in the Pangolin Github issue tracker. Only works with ROS for now.
