FROM jenkins/jenkins:2.315-rhel-ubi8-jdk11

USER root
RUN yum install -y yum-utils && \
    yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo && \
    yum install -y docker-ce-cli

USER jenkins
