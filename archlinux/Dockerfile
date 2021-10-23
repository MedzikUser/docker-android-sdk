FROM medzik/archlinux:latest

WORKDIR /home/build

# Instapp dependencies
RUN sudo pacman -Sy --noconfirm \
      jdk-openjdk \
 && yes | sudo pacman -Scc

# Install cmdline tools
RUN git clone https://aur.archlinux.org/android-sdk-cmdline-tools-latest.git \
 && cd android-sdk-cmdline-tools-latest \
 && makepkg -sr --noconfirm \
 && sudo pacman -U ./*.pkg.tar* --noconfirm \
 && cd .. \
 && rm -rf android-sdk-cmdline-tools-latest \
 && yes | sudo pacman -Scc
