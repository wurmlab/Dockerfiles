# On Mac

## Setup

    # Install.
    brew install docker
    brew install boot2docker

    # Docker on Mac runs within a VM. We will need to create a VM first.
    #
    # The VM can only use as much hard drive space allocated to it, which is 10
    # GB by default. If you think that's enough, skip the -s switch in the line
    # below. Otherwise, tweak as per free space on your hard drive.
    #
    # See boot2docker -h for more options to customise the VM.
    #
    # Create VM with 100 GB hard disk space.
    boot2docker -s 102400 init

    # Launch on login and now.
    #
    # May not work on older boot2docker. Will work for 1.4.1 and above.
    ln -sfv /usr/local/opt/boot2docker/homebrew.mxcl.boot2docker.plist ~/Library/LaunchAgents
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.boot2docker.plist

    # Optionally forward ports you want accessible in browser as localhost:port.
    #
    # Relevant if you are doing web development.
    #
    # general format:
    # VBoxManage modifyvm "boot2docker-vm" --natpf1 "tcp-port<port-number>,tcp,,<port-number>,,<port-number>"
    #
    # For Sinatra.
    VBoxManage modifyvm "boot2docker-vm" --natpf1 "tcp-port4567,tcp,,4567,,4567"
    #
    # For Rackup.
    VBoxManage modifyvm "boot2docker-vm" --natpf1 "tcp-port9292,tcp,,9292,,9292"

## Usage

    # Run docker commands.
    # ...
    # To test docker installation.
    docker run learn/tutorial echo "hello world"

    # Remove all stopped containers.
    docker rm `docker ps --no-trunc -aq`

    # Remove all untagged images.
    docker rmi `docker images | grep "^<none>" | awk '{print $3}'`

    # VM status.
    boot2docker status

    # Start VM.
    boot2docker up

    # Shutdown VM.
    boot2docker down

    # Delete VM so I can create new.
    boot2docker delete

## Upgrade

    brew update
    brew upgrade docker
    brew upgrade boot2docker
    boot2docker upgrade

## Running a web app in a Docker container.

    # Running a project with Dockerfile
    cd <project-dir>
    docker build -t <project-name> .
    docker run -t -i -p 9292:9292 <project-name>
