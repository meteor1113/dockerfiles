# https://github.com/trfore/docker-ubuntu2404-systemd/blob/main/Dockerfile

ARG BASE_TAG=latest
FROM ubuntu:${BASE_TAG}

# ENV DEBIAN_FRONTEND=noninteractive
# ENV container=docker

RUN DEBIAN_FRONTEND=noninteractive \
    apt update -y \
    && apt install -y \
        systemd \
        openssh-server \
        sudo \
        htop \
        lxqt \
        fonts-noto \
        xrdp \
        xorg \
        xorgxrdp \
    && apt-get clean \
    && rm -rf /var/cache/apt/archives/* \
    && rm -rf /var/lib/apt/lists/*

# https://forum.xfce.org/viewtopic.php?id=14108
ARG USER=ubuntu
RUN echo "${USER} ALL=(ALL) NOPASSWD:ALL" > "/etc/sudoers.d/${USER}" \
    && chmod 440 "/etc/sudoers.d/${USER}" \
    && adduser xrdp ssl-cert \
    && update-alternatives --set x-session-manager /usr/bin/startlxqt
    # && echo "startlxqt" > /home/ubuntu/.xsession
    # && chmod +x /home/ubuntu/.xsession
    # && echo password | passwd --stdin ubuntu
# # https://bugzilla.redhat.com/show_bug.cgi?id=1046469#c11
# # https://github.com/ansible-community/molecule/issues/1104
# RUN rm -f /lib/systemd/system/systemd*udev* \
#     && rm -f /lib/systemd/system/getty.target

EXPOSE 22 3389

# CMD ["/lib/systemd/systemd"]
CMD ["/sbin/init"]
