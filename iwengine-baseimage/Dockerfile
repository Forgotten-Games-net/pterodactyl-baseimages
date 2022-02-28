# ----------------------------------------------------------------------
# Pterodactyl Dockerfile for IW Engine based Games like Call of Duty 4
# By FiSTWHO - Forgotten-Games.net
# Tested Panel Version: 1.7.0
# ----------------------------------------------------------------------
FROM ubuntu:focal

LABEL maintainer="fistwho@forgotten-games.net"

# Add i386 architecture support
RUN dpkg --add-architecture i386

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    binutils \
    lib32stdc++6:i386 \
    libstdc++6:i386

RUN adduser --disabled-password --home /home/container container

USER container
ENV  USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]