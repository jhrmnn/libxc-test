FROM mcr.microsoft.com/devcontainers/base:ubuntu

ARG DEBIAN_FRONTEND=noninteractive
ARG LIBXC_VER=5.1.7

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential gfortran \
    autoconf automake libtool pkg-config \
    ca-certificates wget cmake \
 && rm -rf /var/lib/apt/lists/*

# Build + install LibXC (Autotools path; includes Fortran interface)
RUN mkdir -p /tmp/libxc && cd /tmp/libxc \
 && wget -q https://gitlab.com/libxc/libxc/-/archive/${LIBXC_VER}/libxc-${LIBXC_VER}.tar.bz2 \
 && tar -xjf libxc-${LIBXC_VER}.tar.bz2 \
 && cd libxc-${LIBXC_VER} \
 && cmake -B build -DENABLE_FORTRAN=ON \
 && cmake --build build -j \
 && sudo cmake --install build \
 && rm -rf /tmp/libxc