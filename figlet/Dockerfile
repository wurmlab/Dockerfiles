# Provides figlet software for fun and for testing docker setup.

FROM  debian:sid
MAINTAINER  Anurag Priyam <anurag08priyam@gmail.com>

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
      apt-get install -y figlet && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENTRYPOINT ["/usr/bin/figlet"]
CMD ["hello world"]
