Dockerfiles
===========
Trusted Builds also available in the [Docker registry](https://index.docker.io/u/wurmlab/).
Each folders contains a README with more information about the respective Dockerfile.
Sections below provide info on installing and using docker.

Installing docker on Mac
------------------------
Install with the Docker Toolbox - https://www.docker.com/docker-toolbox. Then
add the following to your `.bashrc` or `.zshrc` and open a new terminal:

```
eval "$(docker-machine env default)"
```

Installing docker on Ubuntu
---------------------------
Follow instructions here - https://docs.docker.com/installation/ubuntulinux/.
Then, add yourself to docker group so you can run docker client without sudo.
To do so, run the command below and logout and login again:

```shell
$ sudo usermod -aG docker `whoami`
```

Installing docker on CentOS
---------------------------
Follow instructions here - https://docs.docker.com/installation/centos/. Then,
add yourself to docker group so you can run docker client without sudo and
disable SELinux as it gets in the way of mounting volumes within the
container. To do so, run the commands below and reboot your system.

```shell
    $ sudo usermod -aG docker `whoami`

    # Creates back up of the original file at `/etc/selinux/config.bak`.
    $ sed -i .bak 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config
```

Test that docker is correctly installed
---------------------------------------

The following should give an encouraging message:

    $ docker run hello-world

Useful docker commands
----------------------

```bash
# Stop all containers
docker stop (docker ps -a -q)
# Remove all containers
docker rm (docker ps -a -q)
# Remove all images
docker rmi (docker images -a -q)
```

Run containers without Docker
-----------------------------
Docker has great features, however in most HPC it cannot be used due to [security issues](https://docs.docker.com/articles/security/).
However, the OS can be extracted from a container and run with chroot or in a VM.
Example:
```bash
docker ps -a 
# CONTAINER ID        IMAGE                    COMMAND             CREATED             STATUS                           PORTS               NAMES
# d555fe341045        busybox                  "/bin/sh"           About an hour ago   Exited (139) About an hour ago                       elegant_poitras
docker export elegant_poitras > elegant_poitras.tar
tar xf elegant_poitras.tar
npm install -g mini-container
sudo mini-container bin/sh
```
