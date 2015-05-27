docker-jenkins
==============

A Jenkins CI Docker Container

*Build*

``$ docker pull oreomitch/docker-jenkins``

*Usage*

To run the container and map the host port 8080 to the container port 8080

``$ docker run -d -p 8080:8080 oreomitch/docker-jenkins``

You can include ``--name <name>`` to label the container for example:

``$ docker run -d -p 8080:8080 --name myjenkins oreomitch/docker-jenkins``

By default the container is run as ``jenkins`` user.  This can be changed at runtime using ``-u=<user>``, e.g:

``$ docker run -d -p -u=root 8080:8080 --name myjenkins oreomitch/docker-jenkins``

To install the Android SDK, run the container as ``root`` (see above) and the run the following set of commands:

``$ docker exec <container-id> wget --progress=dot:giga http://dl.google.com/android/android-sdk_r23.0.2-linux.tgz``

``$ docker exec <container-id> mkdir /opt/android``

``$ docker exec <container-id> tar -C /opt/android -xzvf ./android-sdk_r23.0.2-linux.tgz``
