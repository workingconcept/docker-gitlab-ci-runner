FROM bobey/docker-gitlab-ci-runner-php
MAINTAINER  Matt Stein "matt@workingconcept.com"

ENV PHP_VERSION 5.6.6

COPY files/ci-runner.ini /root/.phpenv/versions/$PHP_VERSION/etc/conf.d/ci-runner.ini

RUN phpenv install $PHP_VERSION \
    phpenv rehash && \
    phpenv global $PHP_VERSION

# Install PHP PECL extensions
RUN yes '' | pecl install \
	mongo \
	redis \
	memcache \
	ssh2-0.12

RUN apt-get update && apt-get install -y firefox xvfb
RUN sudo a2enmod rewrite headers php5 suexec expires
RUN sudo service apache2 restart