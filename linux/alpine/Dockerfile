FROM alpine:3.20.3

ARG USER=default
ENV HOME="/home/$USER"

# install sudo as root
RUN apk update

# Required libraries
RUN apk add --no-cache sudo && \
    apk add --no-cache gettext && \
    apk add --no-cache jq && \
    apk add --no-cache curl

# add new user
RUN adduser -D $USER \
        && echo "$USER ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$USER \
        && chmod 0440 /etc/sudoers.d/$USER

USER $USER
WORKDIR $HOME
CMD ["echo", "User $(whoami) running from $PWD with premissions: $(sudo -l)"]

ENTRYPOINT ["/bin/sh", "-c"]