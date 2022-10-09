FROM ubuntu:22.04

ARG ssh_public_key

RUN apt update && apt install -y openssh-server
RUN useradd maintenance-user && \
  mkdir -p /home/maintenance-user/.ssh && \
  chmod 0700 /home/maintenance-user/.ssh && \
  echo "$ssh_public_key" > /home/maintenance-user/.ssh/authorized_keys && \
  echo "AllowUsers maintenance-user" >> /etc/ssh/sshd_config && \
  chown -R maintenance-user /home/maintenance-user && \
  mkdir /run/sshd 

EXPOSE 22

CMD /usr/sbin/sshd -D

