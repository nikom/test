FROM ubuntu:14.04
MAINTAINER Niko Mahle <niko.mahle@googlemail.com>

# Update
RUN sudo apt-get update \
# Install packages
    && sudo apt-get install -y \
		  build-essential \
			python-dev \
			libevent-dev \
			python-pip \
			liblzma-dev

# Install packages
RUN sudo apt-get install -y \
		  locate \
			ntp 

RUN sudo pip install docker-registry

#RUN gunicorn --access-logfile - --debug -k gevent -b 0.0.0.0:5000 -w 1 docker_registry.wsgi:application

RUN cp /usr/local/lib/python2.7/dist-packages/config/config_sample.yml /usr/local/lib/python2.7/dist-packages/config/config.yml

RUN sudo mkdir -p /var/log/docker-registry
COPY docker-registry.conf /etc/init/docker-registry.conf
RUN sudo service docker-registry start