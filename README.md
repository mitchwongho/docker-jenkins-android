docker-jenkins
==============

A Jenkins CI Docker Container

*Build*

``$ docker pull oreomitch/docker-jenkins-android``

*Usage*

To run the container and map the host port 8080 to the container port 8080

``$ docker run -d -p 8080:8080 oreomitch/docker-jenkins-android``

You can include ``--name <name>`` to label the container for example:

``$ docker run -d -p 8080:8080 --name myjenkins oreomitch/docker-jenkins-android``

By default the container is run as ``jenkins`` user.  This can be changed at runtime using ``-u=<user>``, e.g:

``$ docker run -d -p -u=root 8080:8080 --name myjenkins oreomitch/docker-jenkins-android``

To install the Android SDK, run the container as ``root`` (see above) and the run the following set of commands:

``$ docker exec <container-id> wget --progress=dot:giga http://dl.google.com/android/android-sdk_r23.0.2-linux.tgz``

``$ docker exec <container-id> mkdir /opt/android``

``$ docker exec <container-id> tar -C /opt/android -xzvf ./android-sdk_r23.0.2-linux.tgz``

To update the Android SDK, tools, build-tools, system-images

``$ docker exec <container-id>|<container-name> /bin/sh -c "( sleep 3 && while [ 1 ]; do sleep 1; echo y; done ) | /opt/android/android-sdk-linux/android sdk update --no-ui --all"``

The android tools are 32 bit and if you're on 64 bit it will not be able to find them unless you have the 32 bit emulation layers:

``$ docker exec <container-id>|<container-name> /bin/sh -c "apt-get install -y lib32stdc++6 lib32z1 libc6-i386"``
