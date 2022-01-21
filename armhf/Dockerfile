# this image should be created with name cuberite/ci-armhf
FROM debian:bullseye

# Install required software
RUN apt-get update && apt-get install -y --no-install-recommends \
	cmake \
	git \
	lua5.1 \
	make \
	openssh-server \
	wget \
	zip \
	openjdk-11-jre-headless \
	ca-certificates-java \
	python3 \
	gcc-aarch64-linux-gnu \
	g++-aarch64-linux-gnu

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
