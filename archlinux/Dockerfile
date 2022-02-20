FROM medzik/archlinux:latest

WORKDIR /home/build

# Install dependencies
RUN sudo pacman -Sy --noconfirm \
      android-sdk-platform-tools \
      android-sdk-cmdline-tools-latest \
      android-sdk-build-tools && \
 yes | sudo pacman -Scc
