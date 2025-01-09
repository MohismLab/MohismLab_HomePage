# 使用 osrf/ros:humble-desktop-full 作为基础镜像
FROM osrf/ros:humble-desktop-full

# 设置维护者信息
LABEL maintainer="mc45197@um.edu.mo"

# 更新包列表并安装必要的软件包
RUN apt-get update && apt-get install -y \
    build-essential \
    python3-pip \
    python3-venv \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*




# 设置工作目录
WORKDIR /home/robot_repo

RUN git clone https://github.com/isaac-sim/IsaacSim-ros_workspaces.git && \
    cp -r IsaacSim-ros_workspaces/humble_ws /home/robot_repo/humble_ws


# 编译 ROS 包
RUN /bin/bash -c "source /opt/ros/humble/setup.bash && \
    cd /home/robot_repo/humble_ws && \
    colcon build"

# 设置环境变量
ENV ROS_DOMAIN_ID=0 \
    FASTRTPS_DEFAULT_PROFILES_FILE=/home/robot_repo/humble_ws/fastdds.xml


