ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

Vagrant.configure("2") do |config|

  config.vm.define "my-desktop-base-container" do |m|
  
    m.vm.provider "docker" do |master|
        master.build_dir = "./docker"
		master.cmd=["tail", "--f", "/dev/null"] ## to keep container running - see http://stackoverflow.com/questions/30209776/docker-container-will-automatically-stop-after-docker-run-d 		
	    master.name = 'my-desktop-base-container'
        master.vagrant_machine = "dockerdesktophostvm"
        master.vagrant_vagrantfile = "DockerDesktopHostVagrantfile" 
    end
    m.vm.hostname  = "my-desktop.host"
    m.vm.synced_folder "files", "/stage"
    m.vm.synced_folder "puppet", "/puppet"
  end

end

# steps:
# puppet/manifests/base.pp contains Puppet manifest
# files contains installation files
# vagrant up my-desktop-base-container
# vagrant ssh into dockerdesktophostvm
# add desktop: see http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/
# sudo apt-get install --no-install-recommends lubuntu-desktop
# docker ps -a  to find container id
# docker start container id

#  docker exec -it container id bash 
# to have Java configured through Puppet:
#  puppet apply --debug --modulepath=/puppet/modules /puppet/manifests/base.pp

# docker commit containerId  me/java-gui:1.0
# vagrant halt dockerdesktophostvm

# restart dockerdesktophostvm from VirtualBox GUI

# docker run -ti -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY me/java-gui:1.0 /bin/bash

# docker run -ti  -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix bash

## see http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/ on GUI in Docker Containers
