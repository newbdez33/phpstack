FROM jenkins

MAINTAINER Jacky<newbdez33@gmail.com>

USER jenkins
RUN mkdir /var/jenkins_home/db

USER root
RUN apt-get update
RUN apt-get install -y mysql-client

