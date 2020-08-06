# this image should be created with name cuberite/ci-minimal
FROM debian:buster

# Install required software
RUN apt-get update && apt-get install -y --no-install-recommends \
	clang \
	gcc-multilib \
	g++-multilib \
	gcc-arm-linux-gnueabihf \
	g++-arm-linux-gnueabihf \
	cmake \
	git \
	lua5.1 \
	make \
	openssh-server \
	wget \
	zip \
	openjdk-11-jre-headless \
	ca-certificates-java

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
