FROM archlinux:latest

RUN pacman --noconfirm -Syu

# https://docs.astral.sh/uv/guides/integration/docker
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /usr/local/bin/

# compilers and tools
RUN pacman --noconfirm -S \
    ccache \
    gcc \
    git \
    libffi \
    python

# for 3rd-parties
RUN pacman --noconfirm -S \
    autoconf \
    automake \
    cmake \
    gawk \
    grep \
    intltool \
    libtool \
    m4 \
    make \
    pkgconf \
    util-linux-libs

# for roc
RUN pacman --noconfirm -S \
    alsa-lib \
    benchmark \
    cpputest \
    doxygen \
    gengetopt \
    graphviz \
    gsm \
    libpulse \
    libsndfile \
    libunwind \
    libuv \
    openssl \
    ragel \
    scons \
    sox \
    speexdsp

# for pipewire
RUN pacman --noconfirm -S \
    pipewire \
    pipewire-audio \
    wireplumber \
    dbus \
    meson \
    ninja

# for fontconfig
ENV HOME=/home
RUN chmod a+wx /home
