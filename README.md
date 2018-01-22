# Vagrant Rancher Environment 

## Requirements

In order to use this repository you need the following:

- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](http://www.vagrantup.com/)

## Using Vagrant Rancher Environment

Clone or copy the repo and do the following:

    $ cd /path/to/repo
    $ vagrant up

Inspecting the servers & running the applications

    $ vagrant status
    $ vagrant ssh reserver or Browse to http://ranch-svr.infracloud.io:8080"
    $ vagrant ssh rclient1
    $ vagrant ssh rclient2
    
## Clearing the enviroment

    $ vagrant destroy
