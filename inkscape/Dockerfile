# Run container in Desktop:

# xhost +local:;

# docker run --rm \
#     -v /tmp/.X11-unix:/tmp/.X11-unix \
#     -v $HOME/Desktop:/home \
#     -e DISPLAY \
#     --name inkscape \
#     platao/inkscape;

# xhost -local:;

FROM ubuntu:16.10

RUN echo "deb http://ppa.launchpad.net/inkscape.dev/stable/ubuntu yakkety main" > /etc/apt/sources.list.d/inkscape && \
    echo "deb-src http://ppa.launchpad.net/inkscape.dev/stable/ubuntu yakkety main" >  /etc/apt/sources.list.d/inkscape && \
    apt-get update && \
    apt-get install -y inkscape --no-install-recommends && \
    rm -rf /var/cache/* && \
    rm -rf /var/lib/apt/lists/*

VOLUME /home
WORKDIR /home

ENTRYPOINT ["inkscape"]
