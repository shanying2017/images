FROM ros:kinetic-ros-base-xenial

COPY ./ros-latest.list /etc/apt/sources.list.d/
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
COPY ./sources.list /etc/apt/sources.list

RUN apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
RUN apt-get update -y 
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install keyboard-configuration
RUN apt-get install -y ros-kinetic-desktop-full

COPY ./sedros.sh ./
RUN ./sedros.sh

RUN rm //etc/ros/rosdep/sources.list.d/20-default.list -f
RUN rosdep init
RUN rosdep update 

RUN echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
CMD ["bash"]
