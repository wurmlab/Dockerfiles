# Provides debian:sid base image.

FROM  debian:sid
MAINTAINER  Anurag Priyam <anurag08priyam@gmail.com>

RUN echo 'APT::Install-Recommends "false";' >> /etc/apt/apt.conf
RUN echo 'APT::Install-Suggests "false";' >> /etc/apt/apt.conf

RUN apt-get update && \
    apt-get install -y \
      apt-utils locales build-essential git curl openssl ca-certificates && \
    rm -rf /var/lib/apt/lists/*

RUN localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG en_US.utf8
