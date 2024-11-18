FROM docker.io/library/archlinux:base-devel@sha256:b8906906ba3fc092362810f44a46e2efdd9bea0b86a075cf6d464301fe766fc7

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
