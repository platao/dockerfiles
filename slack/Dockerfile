# Run slack desktop app in a container

# xhost +local:docker;

# docker run --rm --name slack \
#     -v /etc/localtime:/etc/localtime:ro \
#     -v /tmp/.X11-unix:/tmp/.X11-unix \
#     -e DISPLAY \
#     --device /dev/snd \
#     --device /dev/dri \
#     --device /dev/video0 \
#     --group-add audio \
#     --group-add video \
#     -v ~/.slack:/root/.config/Slack \
#     --ipc="host" \
#     platao/slack "$@";

# xhost -local:docker;

FROM debian:stretch

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    locales \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

RUN echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen en_US.utf8 && \
    /usr/sbin/update-locale LANG=en_US.UTF-8

# Add the slack debian repo
RUN curl -sSL https://packagecloud.io/slacktechnologies/slack/gpgkey | apt-key add -
RUN echo "deb https://packagecloud.io/slacktechnologies/slack/debian/ jessie main" > /etc/apt/sources.list.d/slacktechnologies_slack.list

RUN apt-get update && apt-get -y install \
    libasound2 \
    libx11-xcb1 \
    libxkbfile1 \
    slack-desktop \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/usr/lib/slack/slack"]
