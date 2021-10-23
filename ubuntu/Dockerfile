FROM medzik/android-sdk:archlinux AS sdk

FROM ubuntu:focal

USER root

ENV DEBIAN_FRONTEND "noninteractive"

ENV ANDROID_HOME     "/opt/android-sdk-linux"
ENV ANDROID_SDK_ROOT "$ANDROID_HOME"
ENV LANG             "en_US.UTF-8"
ENV LC_ALL           "en_US.UTF-8"
ENV LANGUAGE         "en_US:en"
ENV PATH             "${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/emulator:${ANDROID_HOME}/platform-tools:${ANDROID_HOME}/tools:${ANDROID_HOME}/tools/bin:${PATH}"

RUN apt-get update \
 && apt-get install -qq -y --no-install-recommends \
      apt-transport-https \
      wget \
      bc \
      curl \
      file \
      gcc \
      git \
      g++ \
      gnupg2 \
      libc++1-10 \
      libgl1 \
      libtcmalloc-minimal4 \
      make \
      openjdk-11-jdk-headless \
      openssh-client \
      patch \
      python3 \
      python3-distutils \
      rsync \
      ruby \
      ruby-dev \
      tzdata \
      unzip \
      sudo \
      ninja-build \
      zip \
      locales \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

COPY --chown=root --from=sdk /opt/android-sdk ${ANDROID_HOME}

RUN set -o xtrace \
 && cd /opt \
 && sh -c 'echo "en_US.UTF-8 UTF-8" > /etc/locale.gen' \
 && locale-gen \
 && update-locale LANG=en_US.UTF-8 \
 && chown -R root:root $ANDROID_HOME \
 && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers \
 && yes | sdkmanager --licenses \
 && wget -O /usr/bin/android-wait-for-emulator https://raw.githubusercontent.com/travis-ci/travis-cookbooks/master/community-cookbooks/android-sdk/files/default/android-wait-for-emulator \
 && chmod +x /usr/bin/android-wait-for-emulator

RUN mkdir -p /root/.android \
 && touch /root/.android/repositories.cfg
