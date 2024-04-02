ARG BASE_IMAGE=ghcr.io/ucsc-cse-210a/opam-base:local
FROM ${BASE_IMAGE}

ARG OPAM_VERSION=4.14.0
ARG COQ_VERSION=8.16.1


# Install opam
RUN opam init -y --disable-sandboxing --compiler=${OPAM_VERSION}
RUN opam switch ${OPAM_VERSION}


# Install coq
RUN opam repo add coq-released https://coq.inria.fr/opam/released
RUN opam pin add -n -k version coq ${COQ_VERSION}
RUN opam install -y coq
RUN eval `opam config env`

