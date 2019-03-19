# Use an official Python runtime as a parent image
FROM centos:6.8

# Set the working directory to /app
WORKDIR /home

COPY python2.7/ /opt/python2.7
COPY etc/ld.so.conf /etc/

ENV LD_LIBRARY_PATH=/opt/python2.7/lib

# Install any needed packages specified in requirements.txt
RUN yum -y install epel-release
RUN yum -y install mysql postgresql geos blas lapack
#RUN yum -y install epel-release
#RUN yum -y install nginx
#RUN yum -y  install ntp vixie-cron libxslt

RUN mv /etc/localtime /etc/localtime.backup && ln -s /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
#RUN ln -s /usr/share/zoneinfo/Asia/Jakarta /etc/localtime

RUN ln -s /opt/python2.7/bin/python /usr/bin/python2.7

#COPY etc/pam.d/crond /etc/pam.d/

#RUN /etc/init.d/ntpd start && /etc/init.d/rsyslog start && /etc/init.d/postfix start && /etc/init.d/crond start

# Make port 80 available to the world outside this container
EXPOSE 80