FROM ubuntu:14.04

ENV ADMIN_PASSWORD oracle

RUN mkdir /u01 && \ 
    chmod a+xr /u01 

RUN useradd -b /u01 -m -s /bin/bash oracle && \ 
    echo oracle:$ADMIN_PASSWORD | chpasswd

## to enable Puppet

 RUN apt-get install -q -y wget
 RUN wget https://apt.puppetlabs.com/puppetlabs-release-trusty.deb
 RUN dpkg -i puppetlabs-release-trusty.deb
 RUN apt-get update
 RUN  apt-get install -q -y puppet

 # this next line in order to have x-term support in container
RUN apt-get install -q -y libxrender-dev libxtst-dev

