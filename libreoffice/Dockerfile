# Run Libreoffice in a container

# xhost +local:docker;

# docker run -d --rm --name libreoffice \
#     -v /etc/localtime:/etc/localtime:ro \
#     -v /tmp/.X11-unix:/tmp/.X11-unix \
#     -e DISPLAY \
#     -v ~/slides:/root/slides \
#     -e GDK_SCALE \
#     -e GDK_DPI_SCALE \
#     libreoffice;

# xhost -local:docker;

FROM alpine

RUN apk --no-cache add \
    --repository https://dl-3.alpinelinux.org/alpine/edge/testing \
    libreoffice \
    ttf-dejavu

ENTRYPOINT ["libreoffice"]
