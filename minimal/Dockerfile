# this image should be created with name cuberite/ci-minimal
FROM debian:jessie

# Install requirements from debian repositories.
RUN apt-get update && apt-get install -y --no-install-recommends \
	clang \
	cmake \
	git \
	lua5.1 \
	make \
	openjdk-7-jre-headless \
	openssh-server

# Required for SSHD.
RUN mkdir /var/run/sshd

# Add the jenkins user.
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
