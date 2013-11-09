# docker_ros

To build all of the docker images
```
cd images
make
```

To run `rostopic list` in a docker container
```bash
docker run -e ROS_MASTER_URI=<master URI> ros_hydro_precise /src/rostopic list
```

To run `rostopic pub` in a docker container (has to be run interactively, since it doesn't terminate
on its own)
```bash
docker run -i -t -e ROS_MASTER_URI=<master URI> hydro_precise /src/rostopic pub foo std_msgs/String hi
```