# Provides UTF-8 debian:sid base image.
#
# Packages:
# locales, build-essential, curl, openssl, ca-certificates

FROM  debian:sid
MAINTAINER  Anurag Priyam <anurag08priyam@gmail.com>

RUN echo 'APT::Install-Recommends "false";' >> /etc/apt/apt.conf && \
    echo 'APT::Install-Suggests "false";' >> /etc/apt/apt.conf && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
      apt-get install -y \
      locales build-essential curl openssl ca-certificates && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    locale-gen en_US.UTF-8

ENV LANG en_US.utf8
