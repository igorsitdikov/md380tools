FROM debian:9.8

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    gcc-arm-none-eabi \
    binutils-arm-none-eabi \
    libnewlib-arm-none-eabi \
    libusb-1.0 \
    python-usb \
    python-requests \
    sox \
    make \
    git \
    zip \
    unzip \
    gcc-arm-linux-gnueabi \
    qemu-user \
    libc6-dev-armel-cross \
    libc6-dev \
    gcc-arm-linux-gnueabihf \
    curl && \
    rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 https://github.com/travisgoodspeed/md380tools.git /opt/codec-ambe
COPY ambe.c /opt/codec-ambe/emulator
RUN mkdir -p /etc/udev/rules.d/ && \
    cd /opt/codec-ambe && \
    make && \
    cp 99-md380.rules /etc/udev/rules.d/

RUN cd /opt/codec-ambe/emulator && \
    make clean all

WORKDIR /opt/codec-ambe/emulator