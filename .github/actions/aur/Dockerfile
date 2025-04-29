FROM docker.io/library/archlinux:base-devel@sha256:d53a6f8e38e34d617d6da3635fa8be86568d7792838251cbb2d84d899dc8d752

RUN pacman -Syu --needed --noconfirm pacman-contrib namcap git sudo && \
  useradd -m builder && \
  echo 'builder ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

WORKDIR /home/builder
USER builder

# Install paru
RUN git clone https://aur.archlinux.org/paru-bin.git
WORKDIR /home/builder/paru-bin
RUN makepkg -si --noconfirm

COPY entrypoint.sh /entrypoint.sh

ENTRYPOINT [ "/entrypoint.sh" ]
