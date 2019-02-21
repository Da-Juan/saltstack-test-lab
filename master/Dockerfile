FROM saltstack-lab-core

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        salt-master \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /srv/salt
RUN mkdir /srv/pillar

CMD ["/usr/bin/salt-master"]
