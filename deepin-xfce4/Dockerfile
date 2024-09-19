FROM linuxdeepin/deepin:23

ENV DEBIAN_FRONTEND=noninteractive
ENV container=docker
# https://forum.xfce.org/viewtopic.php?id=14108
# deepin-desktop-environment-core \
# store.spark-app.wechat-linux-spark \
RUN echo "deb https://com-store-packages.uniontech.com/appstorev23 beige appstore" > /etc/apt/sources.list.d/appstore.list \
    && apt update -y \
    && apt install -y \
        sudo \
        htop \
        systemd \
        openssh-server \
        xfce4 \
        fonts-noto \
        fonts-noto-cjk \
        fonts-noto-cjk-extra \
        fcitx5 \
        fcitx5-chinese-addons \
        deepin-app-store \
        xrdp \
        libatomic1 \
        deepin-terminal \
    && apt-get clean \
    && rm -rf /var/cache/apt/archives/* \
    && rm -rf /var/lib/apt/lists/*
# update-alternatives --set x-session-manager /usr/bin/startdde
RUN adduser xrdp ssl-cert \
    && update-alternatives --set x-session-manager /usr/bin/startxfce4 \
    && groupadd -g 1000 deepin \
    && useradd -m -g deepin -G sudo -s /bin/bash -u 1000 deepin
    # && echo "startxfce4" > /home/deepin/.xsession
    # && chmod +x /home/deepin/.xsession
    # && echo password | passwd --stdin deepin
EXPOSE 22 3389

# systemd
CMD ["/sbin/init"]
