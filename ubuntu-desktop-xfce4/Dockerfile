FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive
ENV container=docker
# https://forum.xfce.org/viewtopic.php?id=14108
RUN apt update -y \
    && apt install -y \
        sudo \
        systemd \
        openssh-server \
        xubuntu-desktop-minimal \
        xrdp \
    && apt-get clean \
    && rm -rf /var/cache/apt/archives/* \
    && rm -rf /var/lib/apt/lists/*
RUN adduser xrdp ssl-cert \
    && update-alternatives --set x-session-manager /usr/bin/startxfce4
    # && echo "startxfce4" > /home/ubuntu/.xsession
    # && chmod +x /home/ubuntu/.xsession
    # && echo password | passwd --stdin ubuntu
EXPOSE 22 3389

CMD ["/usr/lib/systemd/systemd"]
