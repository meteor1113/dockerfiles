# https://github.com/trfore/docker-ubuntu2404-systemd/blob/main/Dockerfile

ARG BASE_TAG=latest
FROM ubuntu:${BASE_TAG}

ENV DEBIAN_FRONTEND=noninteractive
ENV container=docker

RUN apt update -y \
    && apt install -y \
        systemd \
        openssh-server \
        sudo \
        htop \
        xfce4 \
        xfce4-goodies \
        fonts-noto \
        xrdp \
    && apt-get clean \
    && rm -rf /var/cache/apt/archives/* \
    && rm -rf /var/lib/apt/lists/*

# https://forum.xfce.org/viewtopic.php?id=14108
RUN adduser xrdp ssl-cert \
    && update-alternatives --set x-session-manager /usr/bin/startxfce4
    # && echo "startxfce4" > /home/ubuntu/.xsession
    # && chmod +x /home/ubuntu/.xsession
    # && echo password | passwd --stdin ubuntu
# # https://bugzilla.redhat.com/show_bug.cgi?id=1046469#c11
# # https://github.com/ansible-community/molecule/issues/1104
# RUN rm -f /lib/systemd/system/systemd*udev* \
#     && rm -f /lib/systemd/system/getty.target

EXPOSE 22 3389

# CMD ["/lib/systemd/systemd"]
CMD ["/sbin/init"]
