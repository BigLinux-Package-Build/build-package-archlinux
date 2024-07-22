FROM archlinux:latest

RUN echo -e '\n[multilib]\nInclude = /etc/pacman.d/mirrorlist' >> /etc/pacman.conf \
  && pacman -Sy git --needed --noconfirm \
  && echo -e '\n[biglinux-archlinux]\nSigLevel = PackageRequired\nServer = https://repo.biglinux.com.br/archlinux/$arch' >> /etc/pacman.conf \
  && git clone --depth 1 https://github.com/biglinux/biglinux-keyring.git \
  && cd biglinux-keyring \
  && install -m0644 biglinux.gpg /usr/share/pacman/keyrings/ \
  && install -m0644 biglinux-trusted /usr/share/pacman/keyrings/ \
  && cd .. \
  && rm -rf biglinux-keyring \
  && pacman-key --init \
  && pacman-key --populate archlinux biglinux \
  && pacman -Syu --needed --noconfirm \
    bash-completion \
    bc \
    curl \
    diffutils \
    findutils \
    glibc \
    gnupg \
    inetutils \
    keyutils \
    less \
    lsof \
    man-db \
    man-pages \
    mesa \
    mlocate \
    mtr \
    ncurses \
    nss-mdns \
    openssh \
    pigz \
    pinentry \
    procps-ng \
    rsync \
    shadow \
    sudo \
    tcpdump \
    time \
    traceroute \
    tree \
    tzdata \
    unzip \
    util-linux \
    util-linux-libs \
    vte-common \
    vulkan-intel \
    vulkan-radeon \
    wget \
    words \
    xorg-xauth \
    yay \
    zip \
  && rm -rf /var/cache/pacman/pkg/* \
  && rm -rf /var/lib/pacman/sync/*

CMD ["/usr/bin/bash"]
