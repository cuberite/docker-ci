FROM debian:jessie

# Install testing repository for later version of cmake.
RUN echo "deb http://ftp.debian.org/debian testing main" >> /etc/apt/sources.list &&\
	echo "APT::Default-Release \"stable\";" /etc/apt/apt.conf.d/99defaultrelease

# Install requirements from debian repositories.
RUN apt-get update && apt-get install -y --no-install-recommends \
	clang \
	git \
	lua5.1 \
	lua5.2 \
	lua5.3 \
	make \
	openjdk-7-jre-headless \
	openssh-server \
	unzip \
	wget \
	zip

# Install cmake.
RUN apt-get install -y --no-install-recommends -t testing cmake

# Required for SSHD.	
RUN mkdir /var/run/sshd

# Add the jenkins user.
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
