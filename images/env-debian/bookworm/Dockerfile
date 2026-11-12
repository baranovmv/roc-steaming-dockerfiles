FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update

# https://docs.astral.sh/uv/guides/integration/docker/
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /usr/local/bin/

# compilers and tools
RUN apt-get install -y \
    ccache \
    g++ \
    git \
    python3

# for 3rd-parties
RUN apt-get install -y \
    autoconf \
    automake \
    cmake \
    intltool \
    libtool \
    m4 \
    make \
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
    libsndfile1-dev \
    libsox-dev \
    libspeexdsp-dev \
    libssl-dev \
    libunwind-dev \
    ragel \
    scons

# for pipewire
RUN apt-get install -y \
    libpipewire-0.3-dev \
    libspa-0.2-dev \
    pipewire \
    pipewire-bin \
    wireplumber \
    dbus \
    meson \
    ninja-build

# fix font cache
RUN chmod a+w \
    /var/cache/fontconfig
