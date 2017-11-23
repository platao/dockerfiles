# Run container in Desktop:

# xhost +local:docker;

# docker run --rm --name atom \
#     -v /tmp/.X11-unix:/tmp/.X11-unix \
#     -e DISPLAY \
#     atom;

# xhost -local:docker;

FROM debian:stretch

# Install dependencies
RUN apt-get update && apt-get install -y \
    git \
    gconf2 \
    gconf-service \
    gvfs-bin \
    libasound2 \
    libcap2 \
    libgconf-2-4 \
    libgnome-keyring-dev \
    libgtk2.0-0 \
    libnotify4 \
    libnss3 \
    libxkbfile1 \
    libxss1 \
    libxtst6 \
    libx11-xcb-dev \
    xdg-utils \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

ENV ATOM_VERSION 1.22.0

# download the source
RUN buildDeps=' \
        ca-certificates \
        curl \
    ' && \
    set -x && \
    apt-get update && apt-get install -y $buildDeps --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* && \
    curl -sSL https://github.com/atom/atom/releases/download/v${ATOM_VERSION}/atom-amd64.deb -o /tmp/atom-amd64.deb && \
    dpkg -i /tmp/atom-amd64.deb && \
    rm -rf /tmp/*.deb && \
    apt-get purge -y --auto-remove $buildDeps

# Autorun atom
ENTRYPOINT ["atom", "--foreground"]
