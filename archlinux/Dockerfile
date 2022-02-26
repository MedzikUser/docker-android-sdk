FROM medzik/archlinux:latest

WORKDIR /home/build

# Install dependencies
RUN pacman -Sy --noconfirm \
      android-platform \
      android-sdk-platform-tools \
      android-sdk-cmdline-tools-latest \
      android-sdk-build-tools && \
 yes | pacman -Scc
