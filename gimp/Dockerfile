# Run container in Desktop:

# xhost +local:docker;

# docker run --rm --name gimp \
#     -v /tmp/.X11-unix:/tmp/.X11-unix \
#     -v $HOME/Desktop:/home \
#     -e DISPLAY \
#     platao/gimp;

# xhost -local:docker;

FROM debian:stretch

RUN apt-get update && apt-get install -y \
	gimp \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

VOLUME /home
WORKDIR /home

ENTRYPOINT ["gimp"] 
