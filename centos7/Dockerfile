FROM centos

# Install openssh-server
RUN yum -y install openssh-server

RUN useradd remote_user && \
    echo "admin" | 