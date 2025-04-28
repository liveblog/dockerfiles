# Use official Ubuntu 20.04 base
FROM ubuntu:20.04

# Prevent tzdata interactive prompts
ENV DEBIAN_FRONTEND=noninteractive
ENV VOLTA_HOME=/root/.volta
ENV PATH=$VOLTA_HOME/bin:$PATH

# Update and install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    software-properties-common \
    sudo \
    curl \
    gnupg \
    wget \
    unzip \
    xdg-utils \
    lsb-release \
    build-essential \
    libgconf-2-4 \
    libnss3 \
    libxss1 \
    libappindicator1 \
    libasound2 \
    fonts-liberation \
    xvfb \
    tzdata \
    git \
    chromium-browser \
    chromium-chromedriver

# Set timezone to UTC
RUN ln -fs /usr/share/zoneinfo/Etc/UTC /etc/localtime && dpkg-reconfigure --frontend noninteractive tzdata

# Install Python 3.6 and pip
RUN add-apt-repository ppa:deadsnakes/ppa && \
    apt-get update && \
    apt-get install -y python3.6 python3.6-venv python3.6-dev && \
    ln -s /usr/bin/python3.6 /usr/bin/python && \
    curl https://bootstrap.pypa.io/pip/3.6/get-pip.py | python

# Install Volta and Node.js 10
RUN curl https://get.volta.sh | bash && \
    export VOLTA_HOME=/root/.volta && \
    export PATH=$VOLTA_HOME/bin:$PATH && \
    $VOLTA_HOME/bin/volta install node@10

# Create a workspace directory
WORKDIR /workspace

# Default command
CMD ["/bin/bash"]
