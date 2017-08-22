# this image should be created with name cuberite/ci-minimal
FROM debian:jessie

RUN echo "deb http://ftp.debian.org/debian/ jessie-backports main non-free contrib" >> /etc/apt/sources.list

# Install required software
RUN apt-get update && apt-get install -y --no-install-recommends \
	clang \
	gcc \
	g++ \
	cmake \
	git \
	lua5.1 \
	make \
	openssh-server

RUN apt-get install -y --no-install-recommends -t jessie-backports \
	openjdk-8-jre-headless \
	ca-certificates-java

# Required for 32 bit builds
RUN dpkg --add-architecture i386 &&\
	apt-get update &&\
	apt-get install -y --no-install-recommends \
	libc6-dev-i386 \
	libstdc++6:i386 \
	libgcc1:i386 zlib1g:i386 \
	zlib1g-dev:i386 \
	linux-libc-dev:i386 \
	g++-multilib

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
