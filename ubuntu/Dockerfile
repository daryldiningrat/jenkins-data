FROM ubuntu

# Install openssh-server

RUN apt update && \
    apt install openssh-server sudo -y && \ 
    apt-get install python3-pip -y
    

RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 remote_user

RUN  echo 'remote_user:remote_user' | chpasswd

RUN service ssh start

EXPOSE 22

WORKDIR /home/remote_user

RUN mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY remote-key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user -R /home/remote_user/.ssh/  && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

RUN ssh-keygen -A

RUN apt update -y && apt install mysql-server -y && apt install curl -y

RUN pip install awscli --upgrade

CMD ["/usr/sbin/sshd","-D"]

