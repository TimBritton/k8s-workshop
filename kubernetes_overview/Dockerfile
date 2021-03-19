FROM robertdebock/docker-centos-openssh
RUN yum install -y \
       java-1.8.0-openjdk \
       java-1.8.0-openjdk-devel

ENV JAVA_HOME /etc/alternatives/jre

RUN yum install -y maven
RUN yum install -y git
RUN yum install -y sudo



