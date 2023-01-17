FROM ros:noetic

SHELL ["/bin/bash", "-c"]

WORKDIR /skiros_ws/src

RUN apt-get update \
    && apt-get install -y \
        git \
        python3-pip  \
        wget \
    && source /opt/ros/noetic/setup.bash \
    && catkin_init_workspace \
    && git clone https://github.com/RVMI/skiros2 \
    && git clone https://github.com/RVMI/skiros2_std_lib \
    && git clone https://github.com/RVMI/skiros2_examples \
    && apt-get update \
    && rosdep install --from-paths . --ignore-src --rosdistro=$ROS_DISTRO -y \
    && rm -rf /var/lib/apt/lists/* \
    && pip install -r skiros2/requirements.txt \
    && ./skiros2/skiros2/scripts/install_fd_task_planner.sh

WORKDIR /skiros_ws

RUN source /opt/ros/noetic/setup.bash \
    && catkin_make