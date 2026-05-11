# syntax=docker/dockerfile:1
#
# env-rpios-trixie — Raspberry Pi OS Trixie (arm64) build environment.
#
# This image uses rpi-image-gen to bootstrap a minimal Debian Trixie arm64
# rootfs with build dependencies pre-installed.  It requires:
#   --platform linux/arm64
#   --allow security.insecure   (for debootstrap inside the build)
#
# Build:
#   docker buildx build \
#       --platform linux/arm64 \
#       --allow security.insecure \
#       -t tarabah/env-rpios-trixie:latest .

FROM debian:trixie AS bootstrap

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    autoconf \
    automake \
    autopoint \
    btrfs-progs \
    build-essential \
    ca-certificates \
    cryptsetup \
    curl \
    dbus-user-session \
    dctrl-tools \
    debootstrap \
    debian-archive-keyring \
    dosfstools \
    dpkg-dev \
    e2fsprogs \
    fdisk \
    flex \
    gettext \
    git \
    libtool \
    mmdebstrap \
    mtools \
    pkgconf \
    podman \
    pv \
    python3 \
    python3-debian \
    python3-jsonschema \
    python3-pip \
    python3-yaml \
    rsync \
    uidmap \
    uuid-runtime \
    zip \
    && rm -rf /var/lib/apt/lists/*

# Clone rpi-image-gen
RUN git clone --depth 1 https://github.com/raspberrypi/rpi-image-gen.git /rpi-image-gen

# Copy our layer and config
COPY pw-roc-builddeps.yaml /rpi-image-gen/layer/pw-roc-builddeps.yaml
COPY pw-roc-arm64.yaml /rpi-image-gen/config/pw-roc-arm64.yaml

# Build the rootfs
# IGconf_image_outputdir must be set (even empty) to avoid unbound variable
# error in rpi-image-gen's customize50-cryptroot hook when using -f mode.
RUN --security=insecure \
    mkdir -p /rootfs && \
    cd /rpi-image-gen && \
    export IGconf_image_outputdir="" && \
    export IGconf_image_pmap_schema="" && \
    ./rpi-image-gen build -f -c pw-roc-arm64.yaml && \
    tar -xzf work/pw-roc-arm64/rootfs.tgz -C /rootfs

# Final image from the rootfs
FROM scratch
COPY --from=bootstrap /rootfs /

ENV DEBIAN_FRONTEND=noninteractive
ENV HOME=/home
