# this image should be created with name cuberite/ci-android
FROM debian:buster

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
	zip \
	openjdk-11-jre-headless \
	ca-certificates-java

# Required for SSHD
RUN mkdir /var/run/sshd

# Add the jenkins user
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# Install NDK
RUN wget https://dl.google.com/android/repository/android-ndk-r20b-linux-x86_64.zip -O /home/jenkins/android-ndk.zip &&\
	cd /home/jenkins &&\
	unzip android-ndk.zip &&\
	rm /home/jenkins/android-ndk.zip

# Standard SSH port
EXPOSE 22

# Default command
CMD ["/usr/sbin/sshd", "-D"]
