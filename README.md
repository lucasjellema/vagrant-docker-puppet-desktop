# vagrant-docker-puppet-desktop
Configuration files to construct a Docker Container (with Puppet enabled) and an Ubuntu Docker Host VM (using Vagrant) and extend the Docker Host VM with a desktop, GUI enable the Docker Container and install Java JDK 7 into the container. Subsequently, GUI applications can be run inside the Docker Container.

Steps:
* vagrant up my-desktop-base-container
* vagrant ssh into dockerdesktophostvm
# add desktop: see http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/
* sudo apt-get install --no-install-recommends lubuntu-desktop
* docker ps -a  to find container id
* docker exec -it container id bash 
# to have Java configured through Puppet:
*  puppet apply --debug --modulepath=/puppet/modules /puppet/manifests/base.pp

* docker commit containerId  me/java-gui:1.0
* vagrant halt dockerdesktophostvm

* restart dockerdesktophostvm from VirtualBox GUI
* docker run -ti  -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix me/java-gui:1.0 bash

