# this image should be created with name cuberite/docker-ci/users-manual
FROM debian:buster

# Install required software
RUN apt-get update && apt-get install -y --no-install-recommends \
	python3 \
	python3-pip\
	git \
	openssh-server \
	openjdk-11-jre-headless \
	ca-certificates-java

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Install NDK
RUN pip3 install html5validator

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
