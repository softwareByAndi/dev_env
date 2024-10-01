FROM mcr.microsoft.com/devcontainers/base:debian

# RUN apt-get update && apt-get install -y xz-utils

# This is a Frakenstein piece that takes in a build argument called HOST_USER
# and creates a new user with that name that is supposed to mimic the users logged
# in user.
ARG HOST_USER

# Install sudo and xz-utils
RUN apt-get update \
&& apt-get install -y sudo \
&& apt-get install -y xz-utils

# Create new user and add to sudo group
RUN adduser --disabled-password --gecos '' $HOST_USER \
&& usermod -aG sudo $HOST_USER \
&& echo $HOST_USER ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$HOST_USER \
&& chmod 0440 /etc/sudoers.d/$HOST_USER


# Set the default user
USER $HOST_USER
