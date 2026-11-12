FROM opensuse/leap:latest

# https://docs.astral.sh/uv/guides/integration/docker/
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /usr/local/bin/

# compilers and tools
RUN zypper -n install \
    ccache \
    gcc-c++ \
    git \
    gzip \
    python3

# for 3rd-parties
RUN zypper -n install \
    autoconf \
    automake \
    cmake \
    intltool \
    libtool \
    libuuid-devel \
    m4 \
    make \
    pkg-config

# for roc
RUN zypper -n install \
    alsa-devel \
    benchmark-devel \
    doxygen \
    gengetopt \
    graphviz \
    libopenssl-3-devel \
    libpulse-devel \
    libsndfile-devel \
    libunwind-devel \
    libuv-devel \
    ragel \
    scons \
    sox-devel \
    speexdsp-devel

# for pipewire
RUN zypper -n install \
    pipewire-devel \
    pipewire \
    wireplumber \
    dbus-1 \
    meson \
    ninja

# for fontconfig
ENV HOME=/home
RUN chmod a+wx /home
