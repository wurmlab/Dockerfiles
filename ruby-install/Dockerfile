# Provides base image for installing different Ruby versions using
# gh:postmodern/ruby-install.

FROM        wurmlab/debian
MAINTAINER  Anurag Priyam <anurag08priyam@gmail.com>

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
      apt-get install -y zlib1g-dev libyaml-dev libssl-dev libgdbm-dev \
        libreadline-dev libncurses5-dev libffi-dev && \
    \
    cd /tmp/ && \
    curl -o ruby-install-0.6.0.tar.gz -L \
      https://github.com/postmodern/ruby-install/archive/v0.6.0.tar.gz && \
    tar xvf ruby-install-0.6.0.tar.gz && \
    cd ruby-install-0.6.0/ && \
    make install && \
    \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
