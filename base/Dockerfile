ARG ubuntu_release=focal
FROM ubuntu:${ubuntu_release}

# create user (assuming that there is only one user with same uid:gid on host)
## install sudo
RUN apt update && apt install --no-install-recommends -y \
    sudo \
    && rm -rf /var/lib/apt/lists/*

ENV USERNAME=devops
ENV USERHOME=/home/${USERNAME}

RUN adduser --disabled-password -gecos "" ${USERNAME} && \
    usermod -aG sudo ${USERNAME}

RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# set default shell
ENV SHELL /bin/bash

CMD [ "bash" ]