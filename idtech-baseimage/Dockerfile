# ----------------------------------
# Pterodactyl Dockerfile for idtech Engine based Games like Call of Duty
# By FiSTWHO - Forgotten-Games.net
# Tested Panel Version: 1.7.0
# ----------------------------------
FROM debian:buster-slim AS build

# Add i386 architecture support
RUN dpkg --add-architecture i386

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates=20200601~deb10u2 \
    libstdc++5:i386=1:3.3.6-30 \
    libc6-i386 \
    lib32z1 \
    zlib1g:i386 \
    g++-multilib=4:8.3.0-1 \
    libsqlite3-dev:i386

RUN wget http://ftp.de.debian.org/debian/pool/main/m/mysql-8.0/libmysqlclient21_8.0.23-3+b1_i386.deb -O /tmp/libmysqlclient21_8.0.23-3+b1_i386.deb \
   && dpkg -i /tmp/libmysqlclient21_8.0.23-3+b1_i386.deb

FROM alpine:latest

LABEL maintainer="fistwho@forgotten-games.net"

# Install dependencies
RUN apk add --no-cache --update wget bash curl ca-certificates openssl git tar fontconfig \
  && adduser --disabled-password --home /home/container container

# Copy needed libs from build stage
COPY --from=build /usr/lib/i386-linux-gnu/ /usr/lib/i386-linux-gnu/
COPY --from=build /lib/i386-linux-gnu/ /lib/i386-linux-gnu/
COPY --from=build /lib/ld-linux.so.2 /lib/ld-linux.so.2

USER container
ENV  USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/ash", "/entrypoint.sh"]