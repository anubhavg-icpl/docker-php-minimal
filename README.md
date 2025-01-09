# docker-php-minimal
A collection of Dockerfiles for different versions of a very barebones PHP.

## Purpose
These docker images provide a minimalistic version of PHP for a large number
of PHP versions.  The built PHP is not your typical PHP as it is built as
follows:

* All optional extensions are not built or included.
* The following functions are disabled from running: `system`, `shell_exec`,
  `passthru`, `proc_open`, `popen`, and `ini_set`.
* Error display is turned off but errors are logged instead.
* A 1MB memory limit is enforced.
* URL and file opening is disabled.

This provides a locked down PHP that should be unable to escape and do
anything nasty on the system, especially if combined with limits on CPU usage,
execution time, etc.  Most of these restrictions can be easily modified via
modifying the `php.ini`.

## Usage
Building a docker image with any PHP version is simple.  For example, to build
php 5.6.0:

```bash
docker build --tag php-5.6.0 php-5.6.0
docker run -i -t --rm php-5.6.0 php -i
```

### Using docker-compose
Alternatively, if you have docker-compose installed, you can run the above
steps like this instead:

```bash
docker-compose run php560 php -i
```

## Permissions
Because the container runs as a non-root user, you may run into permission
problems when using volume mounts to your host.  The build user used in the
container is uid/gid 1000, so you may need to provide write access to that
user to any files/directories that need to be written to.  For example:

```bash
chgrp 1000 .
chmod g+w .
```

## License
docker-php-minimal is licensed under the MIT license.  See [LICENSE](LICENSE)
for the full license text.

[docker.io/anubhavgicpl/anubhavfinal-php]: https://github.com/docker.io/anubhavgicpl/anubhavfinal-php
