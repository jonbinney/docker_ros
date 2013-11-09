FROM ubuntu:precise
MAINTAINER Jon Binney

# ubuntu precise image doesn't have universe repo
RUN     echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN     apt-get update
RUN apt-get install -y wget

# install ROS
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu precise main" > /etc/apt/sources.list.d/ros-latest.list'
RUN wget http://packages.ros.org/ros.key -O - | apt-key add -
RUN apt-get update
RUN apt-get install -y ros-hydro-desktop-full

# useful tools for debugging
RUN apt-get install -y iputils-ping dnsutils net-tools

# other useful packages for when we ssh in
RUN apt-get install -y tmux git openssh-server

# set password for root user
RUN echo "root:root"|chpasswd

# start ssh
RUN mkdir -p /var/run/sshd
CMD /usr/sbin/sshd

ADD . /src

CMD /src/rostopic
