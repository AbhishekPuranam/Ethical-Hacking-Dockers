FROM kalilinux/kali-rolling:latest
RUN apt-get update
RUN apt-get install -y devscripts
RUN git clone https://gitlab.com/kalilinux/packages/kali-meta.git
WORKDIR /kali-meta
COPY control /kali-meta/debian/control
RUN dch --local dookie -m "recon"
RUN dpkg-buildpackage -us -uc -b
RUN apt-get install -y  ../kali-linux-webhacking-recon_2020.3.11dookie1_amd64.deb
WORKDIR /

