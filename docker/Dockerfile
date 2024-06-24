FROM nvidia/cuda:12.4.1-cudnn-devel-ubuntu20.04

RUN echo 'Etc/UTC' > /etc/timezone && \
    ln -sf /usr/share/zoneinfo/Asia/Singapore /etc/localtime && \
    apt-get update && \
    apt-get install -q -y --no-install-recommends tzdata

# install packages
RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get install -q -y --no-install-recommends \
    dirmngr \
    gnupg2 \
    curl \
    ca-certificates \
    sudo \
    git \
    bzip2 \
    libx11-6 \
    tmux \
    wget \
    vim \
    netcat \
    iproute2 \
    iputils-ping \
    build-essential \
    software-properties-common \
    gdb \
    libc6-dbg \
    valgrind \
    python3.8 \
    python3-pip \
    && update-alternatives --install /usr/bin/python python /usr/bin/python3.8 10 

# setup environment
ENV DEBIAN_FRONTEND=noninteractive
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
ENV ROS_DISTRO noetic

# Env vars for the nvidia-container-runtime.
ENV NVIDIA_VISIBLE_DEVICES all
ENV NVIDIA_DRIVER_CAPABILITIES graphics,utility,compute

# Install zsh related
RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.2/zsh-in-docker.sh)" -- \
    -t ys \
    -p git \
	-p z \
    -p https://github.com/zsh-users/zsh-autosuggestions \
    -p https://github.com/zsh-users/zsh-syntax-highlighting \
    && echo "set-option -g default-shell /bin/zsh" >> ~/.tmux.conf \
    && chsh -s /bin/zsh

RUN apt-get install -y qt5-default qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools libgl1-mesa-glx \
    && rm -rf /var/lib/apt/lists/*
RUN pip install --upgrade pip setuptools wheel
RUN pip install 'protobuf<4,>=3.20.2'

RUN pip install --default-timeout=100 anylabeling-gpu \
    labelme PyQt5==5.15.7

CMD zsh