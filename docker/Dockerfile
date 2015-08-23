# docker image to run pyinstaller and ldtree
# so that a python app can be packaged into a minimum docker container

FROM ubuntu:14.04
MAINTAINER auniyal@vmware.com

RUN apt-get update

# install python 2.7 (ubuntu comes with python3)
RUN apt-get install -y python2.7
RUN apt-get install -y curl unzip

# install pyinstaller
RUN curl https://bootstrap.pypa.io/get-pip.py|python2.7 -
# pyinstaller need python lib though on ubuntu it is statically linked
RUN apt-get install -y libpython2.7
# pyinstaller needs objdump
RUN apt-get install -y binutils
RUN pip install pyinstaller

# install UPX for compressed exe
RUN apt-get install -y upx-ucl

# ldtree.py needs elftools
RUN pip install pyelftools
RUN curl -o /usr/bin/ldtree.py https://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-projects/pax-utils/lddtree.py

# pyinstaller needs non root user
# set password =  openssl passwd -1 'ca$hc0w')
RUN useradd --password '$1$5pMzB03R$KWfweVHbEuffxx59YiLxP0' --home-dir /tmp maker
RUN adduser maker sudo

