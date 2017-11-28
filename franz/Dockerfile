# Run Franz desktop app in a container

# xhost +local:docker;

# docker run --rm --name franz \
#     -v /tmp/.X11-unix:/tmp/.X11-unix \
#     -e DISPLAY \
#     -v ~/Desktop:/home \
#     -v ~/.franz:/root/.config/Franz \
#     franz;

# xhost -local:docker;
    
FROM debian:stretch

ENV FRANZ_VERSION 4.0.4

RUN apt-get update && \
                apt-get install -y \
                wget \
                libgtk2.0-0 \
                libxtst6 \
                libxss1 \
                libgconf-2-4 \
                libnss3 \
                libasound2 \
                alsa-utils && \
    mkdir /opt/franz && cd /opt/franz && \
    wget https://github.com/meetfranz/franz-app/releases/download/$FRANZ_VERSION/Franz-linux-x64-$FRANZ_VERSION.tgz && \
    tar xf Franz*.tgz && rm Franz*.tgz

ENTRYPOINT ["/opt/franz/Franz"]
