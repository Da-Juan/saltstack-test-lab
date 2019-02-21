FROM saltstack-lab-core

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        salt-minion \
    && rm -rf /var/lib/apt/lists/*

CMD ["/usr/bin/salt-minion"]
