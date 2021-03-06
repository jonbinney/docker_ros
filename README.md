# docker_ros

### Installation

Install dependencies
```bash
sudo apt-get install python-yaml
```

### Building the ROS Docker images

```
cd containers
make
```

### Running ROS commands

This assumes that you already have a ROS master running container
somewhere. For the moment, commands which publish from within the
container won't work (see "Publishing" below).

To run `rostopic list` in a docker container:
```bash
docker run -e ROS_MASTER_URI=<master URI> hydro_precise rostopic list
```

The `-e` option passes and environment variable into the
container. Replace `<master URI>` with the ROS master URI you want to
connect to, and replace `rostopic list` with the ROS command that you
want to run.

### Running a roscore

You can also run a roscore inside of a container:
```bash
docker run -d -p 11311:11311 hydro_precise roscore
```

The `-d` tells docker to detach and run the command in the
background. To kill it you'll need to use `docker ps` to find the
container ID, and then `docker kill <container_id>`. The `-p
11311:11311` tells docker to forward port 11311 inside the container
to port 11311 on the host machine.

### Publishing

For the moment, ROS nodes inside of a container cannot publish to
nodes which are outside the container. This is because tcpros binds to
random ports, and so we don't know ahead of time which ports to
forward from the container to the host.

To run `rostopic pub` in a docker container:

```bash
docker run -i -t -e ROS_MASTER_URI=<master URI> hydro_precise rostopic pub foo std_msgs/String hi
```

This has to be run interactively, since it doesn't terminate on its
own.