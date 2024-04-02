ARG BASE_IMAGE=ubuntu:22.04
FROM $BASE_IMAGE

ENV LANG=C.UTF-8

ARG DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update -y && \
	apt-get install build-essential -y && \
	apt-get install libgmp-dev -y && \
	apt-get install software-properties-common -y && \
	apt-get install nano -y && \
	apt-get install wget -y && \
	apt-get install unzip -y && \
	apt-get install git -y && \
	apt-get autoremove -y && apt-get clean -y


# Install opam and make
# RUN add-apt-repository -y ppa:avsm/ppa
RUN apt-get update -y &&\
	apt-get install -y opam && \
	apt-get autoremove -y && apt-get clean -y

