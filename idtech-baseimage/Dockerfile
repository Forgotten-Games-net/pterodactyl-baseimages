# ----------------------------------
# Pterodactyl Dockerfile for idtech Engine based Games like Call of Duty
# By FiSTWHO - Forgotten-Games.net
# Tested Panel Version: 1.7.0
# ----------------------------------
FROM ubuntu:focal

LABEL maintainer="fistwho@forgotten-games.net"

# Add i386 architecture support
RUN dpkg --add-architecture i386

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    binutils \
    libstdc++5:i386 \
    libc6-i386 \
    lib32z1 \
    zlib1g:i386 \
    libmysqlclient-dev:i386 \
    libsqlite3-dev:i386

RUN adduser --disabled-password --home /home/container container

USER container
ENV  USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/ash", "/entrypoint.sh"]