# this image should be created with name cuberite/docker-ci/minimal
FROM debian:buster

RUN echo 'deb http://deb.debian.org/debian buster-backports main' > /etc/apt/sources.list.d/backports.list

# Install required software
RUN apt-get update && apt-get install -y --no-install-recommends \
	clang \
	clang-tidy-11 \
	gcc-multilib \
	g++-multilib \
	cmake \
	git \
	lua5.1 \
	make \
	openssh-server \
	wget \
	zip \
	openjdk-11-jre-headless \
	ca-certificates-java

RUN update-alternatives --install /usr/bin/run-clang-tidy run-clang-tidy /usr/bin/run-clang-tidy-11 900

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
