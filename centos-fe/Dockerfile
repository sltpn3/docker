# Use an official Python runtime as a parent image
FROM centos:6.8

# Set the working directory to /app
WORKDIR /home

COPY rpmforge.repo /etc/yum.repos.d/

# Install any needed packages specified in requirements.txt
RUN yum -y install epel-release
RUN yum -y install nginx
RUN yum -y install httpd
RUN yum -y install php-5.3.3 php-fpm-5.3.3 php-mcrypt-5.3.3 php-mbstring-5.3.3 php-mysql-5.3.3 php-pdo-5.3.3 php-xml-5.3.3 php-pear mod_fastcgi

COPY etc/httpd/conf.d/fastcgi.conf /etc/httpd/conf.d/
COPY etc/httpd/conf.d/php.conf /etc/httpd/conf.d/
COPY etc/php-fpm.conf /etc/
COPY etc/php-fpm.d/www.conf /etc/php-fpm.d/
COPY Auth_Yubico-2.5.tgz /home/

RUN cd /usr/lib && mkdir cgi-bin
RUN cd /home && pear install Auth_Yubico-2.5.tgz

# Make port 80 available to the world outside this container
EXPOSE 80
