# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

MASTER_MEMORY=1024
AGENT_MEMORY=1024

RANCH_MASTER_ADDRESS="172.19.8.100"
# Boxes are configured at 101, 102 and so on
RANCH_SUBNET="172.19.8"


RSERVER_DOMAIN_NAME="rserver.skynet.io"
CB="couchbase.skynet.io"
CADVISOR="cadvisor.skynet.io"
RCLIENT2="rclient2.skynet.io"


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

        config.vm.define "rserver" do |rserver|
                rserver.vm.box = "ubuntu/trusty64"
                rserver.vm.network "private_network", ip: "#{RANCH_MASTER_ADDRESS}"
                rserver.vm.hostname = "#{RSERVER_DOMAIN_NAME}"
                rserver.vm.provider :virtualbox do |vba|
                        vba.customize ["modifyvm", :id, "--memory", MASTER_MEMORY]
                end
                rserver.vm.provision "shell", inline: "wget -qO- https://get.docker.com/ | sh"
                rserver.vm.provision "shell", inline: "sudo docker run -d --restart=always -p 8080:8080 rancher/server"
        end

        config.vm.define "couchbase" do |couchbase|
                couchbase.vm.box = "ubuntu/trusty64"
                couchbase.vm.network "private_network", ip: "#{RANCH_SUBNET}.101"
                couchbase.vm.hostname = "#{CB}"
                couchbase.vm.provider :virtualbox do |vba|
                        vba.customize ["modifyvm", :id, "--memory", MASTER_MEMORY]
                end
                couchbase.vm.provision "shell", inline: "wget -qO- https://get.docker.com/ | sh"
                couchbase.vm.provision "shell", inline: "docker run -d -p 8091-8093:8091-8093 -p 11210:11210 --name couchbase arungupta/couchbase"
                
        end

        config.vm.define "cadvisor" do |cadvisor|
                cadvisor.vm.box = "ubuntu/trusty64"
                cadvisor.vm.network "private_network", ip: "#{RANCH_SUBNET}.102"
                cadvisor.vm.hostname = "#{CADVISOR}"
                cadvisor.vm.provider :virtualbox do |vba|
                        vba.customize ["modifyvm", :id, "--memory", MASTER_MEMORY]
                end
                cadvisor.vm.provision "shell", inline: "wget -qO- https://get.docker.com/ | sh"
        end

        config.vm.define "rclient2" do |rclient2|
                rclient2.vm.box = "ubuntu/trusty64"
                rclient2.vm.network "private_network", ip: "#{RANCH_SUBNET}.103"
                rclient2.vm.hostname = "#{RCLIENT2}"
                rclient2.vm.provider :virtualbox do |vba|
                        vba.customize ["modifyvm", :id, "--memory", MASTER_MEMORY]
                end
                rclient2.vm.provision "shell", inline: "wget -qO- https://get.docker.com/ | sh"

        end
end
