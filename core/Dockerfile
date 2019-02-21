FROM debian:9

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        ca-certificates gnupg wget \
    && rm -rf /var/lib/apt/lists/*

RUN wget -q https://repo.saltstack.com/apt/debian/9/amd64/latest/SALTSTACK-GPG-KEY.pub
RUN apt-key add SALTSTACK-GPG-KEY.pub
RUN echo "deb http://repo.saltstack.com/apt/debian/9/amd64/latest stretch main" > /etc/apt/sources.list.d/saltstack.list

RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        salt-common \
    && rm -rf /var/lib/apt/lists/*
