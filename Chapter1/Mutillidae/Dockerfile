# Pull base image
FROM ubuntu:16.04

# Working Directory
WORKDIR /root

# Install
RUN \
    apt-get update && \
    apt-get -y install wget && \
    apt-get install unzip && \
    apt-get -y install supervisor && \
    wget -O xampp.run https://www.apachefriends.org/xampp-files/5.6.30/xampp-linux-x64-5.6.30-0-installer.run && \
    chmod +x ./xampp.run && \
    ./xampp.run --mode unattended && \
    wget -O mutillidae.zip https://sourceforge.net/projects/mutillidae/files/latest/download && \
    unzip mutillidae.zip && \
    cp -r mutillidae /opt/lampp/htdocs/ && \
    sed -i 's/Deny/Allow/g' /opt/lampp/htdocs/mutillidae/.htaccess && \
    sed -i -E 's/,Allow/,Deny/' /opt/lampp/htdocs/mutillidae/.htaccess && \
    echo "[supervisord]" > /etc/supervisor/conf.d/supervisord.conf && \
    echo "nodaemon=true" >> /etc/supervisor/conf.d/supervisord.conf && \
    echo "[program:xampp]" >> /etc/supervisor/conf.d/supervisord.conf && \
    echo "command=/bin/bash -c '/opt/lampp/xampp start'" >> /etc/supervisor/conf.d/supervisord.conf

EXPOSE 80 443 3306

CMD ["/usr/bin/supervisord"]
