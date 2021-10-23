FROM medzik/archlinux:latest

WORKDIR /home/build

# Instapp dependencies
RUN sudo pacman -Sy \
      jdk-openjdk \
 && sudo pacman -Scc

# Install cmdline tools
RUN git clone https://aur.archlinux.org/android-sdk-cmdline-tools-latest.git \
 && cd android-sdk-cmdline-tools-latest \
 && makepkg -sr \
 && sudo pacman -U ./*.pkg.tar* \
 && cd .. \
 && rm -rf android-sdk-cmdline-tools-latest \
 && sudo pacman -Scc
