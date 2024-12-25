FROM docker.io/library/archlinux:base-devel@sha256:6112d42cc02db807bc8aeb512331d22be93f678ba68a4e4cafefa152da97c0ce

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
