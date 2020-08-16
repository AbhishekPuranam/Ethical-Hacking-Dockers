FROM kalilinux/kali-rolling:latest
RUN apt-get update && apt-cache show kali-tools-web | grep Depends
RUN apt-get install -y kali-tools-web
