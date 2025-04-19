FROM osrf/ros:noetic-desktop-full
ARG USERNAME=developer
ARG USER_UID=1000
ARG USER_GID=$USER_UID

ENV DEBIAN_FRONTEND=noninteractive
ENV BAZEL_ENVIRONMENT="dev"

# installing some base & ROS packages
RUN apt update && \ 
    apt install --no-install-recommends -y \
    python3-pip \
    python3-catkin-tools \
    software-properties-common \
    net-tools \
    kmod \
    iproute2 \
    ros-noetic-moveit \
    ros-noetic-ddynamic-reconfigure \
    ros-noetic-teleop-twist-keyboard \
    ros-noetic-velodyne-description \
    ros-noetic-velodyne-gazebo-plugins \
    ros-noetic-joint-trajectory-controller \
    ros-noetic-slam-toolbox

# installing CAN Requirements
RUN pip install python-can canard cantools pyserial

# Installing Realsense Library
RUN sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE
RUN sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo $(lsb_release -cs) main" -u
RUN sudo apt-get install -y librealsense2-utils librealsense2-dev

# adding dev user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -ms /bin/bash $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER developer
