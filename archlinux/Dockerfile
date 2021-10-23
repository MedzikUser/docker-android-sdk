FROM medzik/archlinux:latest

WORKDIR /home/build

# Install dependencies
RUN sudo pacman -Sy --noconfirm \
      jdk11-openjdk \
 && yes | sudo pacman -Scc

# Install cmdline tools
RUN git clone https://aur.archlinux.org/android-sdk-cmdline-tools-latest.git \
 && cd android-sdk-cmdline-tools-latest \
 && makepkg -sr --noconfirm \
 && sudo pacman -U ./*.pkg.tar* --noconfirm \
 && cd .. \
 && rm -rf android-sdk-cmdline-tools-latest \
 && yes | sudo pacman -Scc

# Install platform tools
RUN git clone https://aur.archlinux.org/android-sdk-platform-tools.git \
 && cd android-sdk-platform-tools \
 && makepkg -sr --noconfirm \
 && sudo pacman -U ./*.pkg.tar* --noconfirm \
 && cd .. \
 && rm -rf android-sdk-platform-tools \
 && yes | sudo pacman -Scc

# Install platform
RUN git clone https://aur.archlinux.org/android-platform.git \
 && cd android-platform \
 && makepkg -sr --noconfirm \
 && sudo pacman -U ./*.pkg.tar* --noconfirm \
 && cd .. \
 && rm -rf android-platform \
 && yes | sudo pacman -Scc

# Install build tools
RUN git clone https://aur.archlinux.org/android-sdk-build-tools.git \
 && cd android-sdk-build-tools \
 && makepkg -sr --noconfirm \
 && sudo pacman -U ./*.pkg.tar* --noconfirm \
 && cd .. \
 && rm -rf android-sdk-build-tools \
 && yes | sudo pacman -Scc
