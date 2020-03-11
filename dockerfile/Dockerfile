FROM gitlab/gitlab-runner
MAINTAINER xianyuli

RUN echo 'deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse' > /etc/apt/source.list && \
	echo 'deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse' > /etc/apt/source.list && \
	echo 'deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse' > /etc/apt/source.list && \
	echo 'deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse' > /etc/apt/source.list && \
	apt-get update -y && \
	apt-get clean
	
RUN apt-get -y install apt-transport-https ca-certificates curl gnupg-agent software-properties-common && \
	curl -fsSL https://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | apt-key add - && \
	add-apt-repository "deb [arch=amd64] https://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable" && \
	apt-get update -y && \
	apt-get install -y docker-ce 
COPY daemon.json /etc/docker/daemon.json

RUN curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
chmod +x /usr/local/bin/docker-compose

RUN mkdir -p /usr/local/java
WORKDIR /usr/local/java
COPY jdk-8u241-linux-x64.tar.gz /usr/local/java
RUN tar -zxvf jdk-8u241-linux-x64.tar.gz && \
	rm -rf jdk-8u241-linux-x64.tar.gz
	
RUN mkdir -p /usr/local/maven
WORKDIR /usr/local/maven
COPY apache-maven-3.6.3-bin.tar.gz /usr/local/maven
RUN tar -zxvf apache-maven-3.6.3-bin.tar.gz && \
	rm -rf apache-maven-3.6.3-bin.tar.gz
	
# 切换用户避免环境变量无法使用
USER gitlab-runner
ENV JAVA_HOME /usr/local/java/jdk1.8.0_241
ENV MAVEN_HOME /usr/local/maven/apache-maven-3.6.3
ENV PATH $PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin

WORKDIR /







