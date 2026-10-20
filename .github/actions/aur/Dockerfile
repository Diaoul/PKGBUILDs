FROM docker.io/library/archlinux:base-devel@sha256:0ccc8b2e55c0c26a6e501e892cc6b1cdea7cfdf77e432941320148b4dabd2bff

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
