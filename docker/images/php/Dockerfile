FROM php:7-alpine

RUN apk --no-cache add openssh-server

RUN apk add --update python

RUN apk add --update coreutils

RUN sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config

RUN echo "root:root" | chpasswd


COPY authorized_keys /root/.ssh/authorized_keys

COPY entrypoint.sh /entrypoint.sh

#ENTRYPOINT ["sh", "/entrypoint.sh"]

RUN ssh-keygen -A

#RUN "nohup php -S localhost:8080 -t /var/www > phpd.log 2>&1 &"

CMD ["/usr/sbin/sshd", "-D"]



