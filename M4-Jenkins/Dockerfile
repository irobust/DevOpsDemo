FROM jenkins/jenkins:lts

USER root
RUN yum install -y yum-utils && \
    yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo && \
    yum install -y docker-ce-cli

USER jenkins
