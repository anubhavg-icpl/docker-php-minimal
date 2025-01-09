FROM docker.io/anubhavgicpl/anubhavfinal-php

LABEL maintainer="Anubhav Gain <iamanubhavgain@gmail.com>"

COPY php/PKGBUILD php/*.patch /package/

RUN makepkg --force

USER root

RUN pacman --upgrade --noconfirm --noprogressbar php-*-x86_64.pkg.tar.xz

COPY php.ini /etc/php/php.ini

USER build

CMD ["php"]
