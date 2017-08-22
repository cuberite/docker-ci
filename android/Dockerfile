# this image should be created with name cuberite/ci-android
FROM debian:jessie

# Install testing repository for later version of cmake
RUN echo "deb http://ftp.debian.org/debian testing main" >> /etc/apt/sources.list &&\
	echo "APT::Default-Release \"stable\";" /etc/apt/apt.conf.d/99defaultrelease

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
	openssh-server \
	unzip \
	wget \
	zip

RUN apt-get install -y --no-install-recommends -t jessie-backports \
	openjdk-8-jre-headless \
	ca-certificates-java

# Install cmake
RUN apt-get install -y --no-install-recommends -t testing cmake

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Install NDK
RUN wget https://dl.google.com/android/repository/android-ndk-r13b-linux-x86_64.zip -O /home/jenkins/android-ndk.zip &&\
	cd /home/jenkins &&\
	unzip android-ndk.zip &&\
	rm /home/jenkins/android-ndk.zip

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
