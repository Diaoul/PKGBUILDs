FROM docker.io/library/archlinux:base-devel@sha256:c84ad63503efc5d386e30a5f44945fa8eee10fcb21b3d5fceda260783de394ff

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
