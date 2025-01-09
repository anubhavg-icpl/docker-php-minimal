FROM docker.io/anubhavgicpl/anubhavfinal-php

LABEL maintainer="Anubhav Gain <iamanubhavgain@gmail.com>"

# Set the working directory to /package
WORKDIR /package

# Copy PKGBUILD and any patch files to /package
COPY php/PKGBUILD php/*.patch /package/

# Build the package
RUN makepkg --force

# Switch to root user to install the package
USER root

# Install the newly built PHP package
# Use -U to install a local package and specify the correct path
RUN pacman -U --noconfirm --noprogressbar php-*-x86_64.pkg.tar.xz

# Copy the php.ini configuration file
COPY php.ini /etc/php/php.ini

# Switch back to the build user
USER build

# Set the default command to run PHP
CMD ["php"]
