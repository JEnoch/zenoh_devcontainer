FROM ubuntu:latest

ARG ZENOH_VERSION=1.3.3

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get upgrade -y && apt-get install -y ca-certificates && \
    # Add Zenoh Debian repository
    echo "deb [trusted=yes] https://download.eclipse.org/zenoh/debian-repo/ /" | tee -a /etc/apt/sources.list.d/zenoh.list > /dev/null && \
    apt-get update && \
    # Install Zenoh router, some APIs (C, pico) and some plugins (DDS, ROS2)
    apt-get install -y zenoh=$ZENOH_VERSION libzenohc-dev=$ZENOH_VERSION libzenohpico-dev=$ZENOH_VERSION zenoh-plugin-dds=$ZENOH_VERSION zenoh-plugin-ros2dds=$ZENOH_VERSION && \
    # Install other useful tools
    apt-get install -y build-essential cmake python3 python3-venv python3-pip curl less vim jq iputils-ping iproute2

# Install Python and a virtual environment
RUN python3 -m venv /zenoh-venv && echo ". /zenoh-venv/bin/activate" >> ~/.bashrc
# Install Zenoh Python API
RUN . /zenoh-venv/bin/activate && pip3 install eclipse-zenoh==$ZENOH_VERSION


ENV SHELL=/bin/bash
