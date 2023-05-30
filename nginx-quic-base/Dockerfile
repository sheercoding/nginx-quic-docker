FROM ubuntu:22.04


# DEB_DEPENDS from VPP's Makefile, added here to be cached
# This must be updated when the list of VPP dependencies change
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y \
	build-essential python3 autotools-dev \
	libdumbnet-dev libluajit-5.1-dev libpcap-dev \
	libpcre3 libpcre3-dev \
	zlib1g-dev pkg-config libhwloc-dev \
	cmake liblzma-dev openssl \
	libssl-dev cpputest libsqlite3-dev \
	libtool uuid-dev git \
	mercurial golang \
	autoconf bison flex \
	libcmocka-dev libnetfilter-queue-dev libunwind-dev \
	libmnl-dev ethtool wget \
	net-tools iputils-ping vim && \
	apt-get clean && \
	echo 'export TERM=xterm-256color' >> ~/.bashrc && \
	echo 'export LD_LIBRARY_PATH=/usr/local/lib:/usr/lib' >> ~/.bashrc \
	echo 'PATH=/usr/local/nginx/sbin:$PATH' >> ~/.bashrc 
