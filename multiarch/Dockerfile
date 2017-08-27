# this image should be created with name cuberite/ci-minimal
FROM multiarch/crossbuild

RUN echo "deb http://ftp.debian.org/debian/ jessie-backports main non-free contrib" >> /etc/apt/sources.list

# Install required software
RUN apt-get update && apt-get install -y --no-install-recommends \
	lua5.1 \
	openssh-server

RUN apt-get install -y --no-install-recommends -t jessie-backports \
	openjdk-8-jre-headless \
	ca-certificates-java

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Standard SSH port
EXPOSE 22

# Default command
ENTRYPOINT [""]
CMD ["/usr/sbin/sshd", "-D"]

