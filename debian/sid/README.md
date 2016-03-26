Debian Sid based base-image for building docker images.

Inherits from debian:sid. Configures apt to not install recommended and
suggested packages. Installs following packages often required for
development:

    locales, build-essential, curl, openssl, ca-certificates
