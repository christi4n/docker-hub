FROM alpine:3.20.3

ARG USER=default
ENV HOME="/home/$USER"

RUN apk update --no-cache && apk upgrade --no-cache

# Required libraries
RUN apk add sudo gettext curl unzip gcompat jq yq

# add new user
RUN adduser -D $USER \
        && echo "$USER ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$USER \
        && chmod 0440 /etc/sudoers.d/$USER

USER $USER
WORKDIR $HOME
CMD ["echo", "User $(whoami) running from $PWD with premissions: $(sudo -l)"]

ENTRYPOINT ["/bin/sh", "-c"]