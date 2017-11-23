# PulseAudio section adapted from @TheBiggerGuy: docker-pulseaudio-example repository

# This Dockerfile generate the following pulseaudio error when run like a container:

# Opening a playback stream with sample specification 's16le 2ch 44100Hz' and channel map 'front-left,front-right'.
# Connection failure: Connection refused
# pa_context_connect() failed: Connection refused

# Run container in Desktop:

# xhost +local:docker;

# docker run --rm --name firefox54 \
#     -v /tmp/.X11-unix:/tmp/.X11-unix \
#     -e DISPLAY \
#     -v ~/Desktop:/home/fireuser/Desktop \
#     -v /run/user/1000/pulse:/run/user/1000/pulse \
#     -v /dev/shm:/dev/shm \
#     platao/firefox54;

# xhost -local:docker;

FROM ubuntu:16.10

# Replace 1000/100 with your user/group id
ENV app=firefox user=fireuser uid=1000 gid=100

RUN apt-get update && DEBIAN_FRONTEND=noninteractive \
    apt-get install -y \
            $app \
            pulseaudio-utils

RUN mkdir -p /home/$user && \
    echo "$user:x:$uid:$gid:$user User,,,:/home/$user:/bin/bash" >> /etc/passwd && \
    echo "$user:x:$uid:" >> /etc/group && \
    mkdir -p /etc/sudoers.d && \
    echo "$user ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$user && \
    chmod 0440 /etc/sudoers.d/$user && \
    chown $uid:$gid -R /home/$user && \
    gpasswd -a $user audio

COPY pulse-client.conf /etc/pulse/client.conf

USER $user
ENV HOME /home/$user
CMD ["pacat", "-vvvv", "/usr/bin/firefox"]
