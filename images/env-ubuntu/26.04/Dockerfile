FROM ubuntu:26.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update

# compilers and tools
RUN apt-get install -y \
    ccache \
    clang \
    clang-format \
    g++ \
    git \
    python3 \
    valgrind

# for 3rd-parties
RUN apt-get install -y \
    autoconf \
    automake \
    cmake \
    intltool \
    libtool \
    m4 \
    make \
    meson \
    pkg-config \
    uuid-dev

# for roc
RUN apt-get install -y \
    doxygen \
    gengetopt \
    graphviz \
    libasound2-dev \
    libbenchmark-dev \
    libcpputest-dev \
    libpulse-dev \
    libsndfile-dev \
    libsox-dev \
    libspeexdsp-dev \
    libssl-dev \
    libunwind-dev \
    libuv1-dev \
    pulseaudio \
    ragel \
    scons

# for pipewire
RUN apt-get install -y \
    libpipewire-0.3-dev \
    libspa-0.2-dev \
    pipewire \
    pipewire-bin \
    wireplumber \
    dbus
