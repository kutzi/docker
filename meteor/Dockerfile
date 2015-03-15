FROM node:0.12-wheezy

RUN apt-get update && apt-get install -y less procps vim openssh-server

RUN mkdir /var/run/sshd
RUN echo 'root:screencast' | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

RUN curl https://install.meteor.com/ | sh
RUN npm install -g meteorite

ENV PORT 3000
EXPOSE 3000
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
