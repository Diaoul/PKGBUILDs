FROM docker.io/library/archlinux:base-devel@sha256:f15064b187aea96308a0252d1eacf514a2ee89aad6d44811f52b733fa9a5e42b

RUN pacman -Syu --needed --noconfirm pacman-contrib namcap git sudo && \
  useradd -m builder && \
  echo 'builder ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

WORKDIR /home/builder
USER builder

# Install paru
RUN git clone https://aur.archlinux.org/paru.git
WORKDIR /home/builder/paru
RUN makepkg -si --noconfirm

COPY entrypoint.sh /entrypoint.sh

ENTRYPOINT [ "/entrypoint.sh" ]
