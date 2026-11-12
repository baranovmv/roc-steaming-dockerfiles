FROM alpine:latest

RUN apk update

# https://docs.astral.sh/uv/guides/integration/docker/
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /usr/local/bin/

# compilers and tools
RUN apk add \
    bash \
    ccache \
    g++ \
    git \
    python3

# for 3rd-parties
RUN apk add \
    autoconf \
    automake \
    cmake \
    intltool \
    libtool \
    m4 \
    make \
    pkgconfig \
    util-linux-dev

# for roc
RUN apk add \
    alsa-lib-dev \
    benchmark \
    cpputest \
    doxygen \
    gengetopt \
    graphviz \
    libsndfile-dev \
    libunwind-dev \
    libuv-dev \
    openssl-dev \
    pulseaudio-dev \
    ragel \
    scons \
    sox-dev \
    speexdsp-dev

# for pipewire
RUN apk add \
    pipewire-dev \
    pipewire \
    wireplumber \
    dbus \
    meson \
    ninja

