ARG BASE_IMAGE=ghcr.io/ucsc-cse-210a/opam-base:local
FROM ${BASE_IMAGE}

ARG OPAM_VERSION=4.14.0
ARG COQ_VERSION=8.16.1

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ARG USER_SHELL=/bin/bash

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME -s ${USER_SHELL} \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME

# initialize opam and install coq under the specified user

# Install opam
RUN opam init -y --disable-sandboxing --compiler=${OPAM_VERSION}
RUN opam switch ${OPAM_VERSION}


# Install coq
RUN opam repo add coq-released https://coq.inria.fr/opam/released
RUN opam pin add -n -k version coq ${COQ_VERSION}
RUN opam install -y coq
RUN eval `opam config env`

# set the environment variables on shell startup
RUN echo 'eval `opam config env`' >> $HOME/.bashrc
RUN echo 'eval `opam config env`' >> $HOME/.profile

