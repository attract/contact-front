Dokerfile
FROM centos:7

MAINTAINER AttractGroup

# Update the base system with latest patches
# and latest epel release NO NEED add epel repos!!!
RUN yum -y update && yum clean all
RUN yum install -y epel-release

# Install Main Programs
RUN yum install -y \
        git \
        curl \
        nginx \
        supervisor \
        npm \
        nodejs

RUN npm install -g bower && npm install -g gulp

ADD . /var/www/project/

CMD ["/var/www/project/docker/run.sh"]