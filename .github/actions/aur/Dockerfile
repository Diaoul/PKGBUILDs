FROM docker.io/library/archlinux:base-devel@sha256:25074821d28e54a0bbbd87a88d392f1489be9bd815ee5c60744be6e57fd500d8

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
