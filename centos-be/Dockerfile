# Use an official Python runtime as a parent image
FROM centos:6.8

# Set the working directory to /app
WORKDIR /home

COPY python2.7/ /opt/python2.7
COPY etc/ld.so.conf /etc/

ENV LD_LIBRARY_PATH=/opt/python2.7/lib

# Install any needed packages specified in requirements.txt
RUN yum -y -v install epel-release
RUN rpm --import http://li.nux.ro/download/nux/RPM-GPG-KEY-nux.ro
RUN rpm -Uvh http://li.nux.ro/download/nux/dextop/el6/x86_64/nux-dextop-release-0-2.el6.nux.noarch.rpm

#RUN yum -y install nginx
RUN yum -y  install ntp vixie-cron libxslt ffmpeg ffmpeg-devel postfix libevent


RUN mv /etc/localtime /etc/localtime.backup && ln -s /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
#RUN ln -s /usr/share/zoneinfo/Asia/Jakarta /etc/localtime

COPY etc/pam.d/crond /etc/pam.d/

RUN /etc/init.d/ntpd start && /etc/init.d/rsyslog start && /etc/init.d/postfix start && /etc/init.d/crond start

# Make port 80 available to the world outside this container
EXPOSE 80