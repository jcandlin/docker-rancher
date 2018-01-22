# Vagrant Rancher Environment 

## Requirements

In order to use this repository you need the following:

- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](http://www.vagrantup.com/)

## Using Vagrant Rancher Environment

Clone or copy the repo and do the following:

    $ cd /path/to/repo
    $ vagrant up
    
## To access the Rancher GUI

    $ Browse to http://rserver.skynet.io:8080"

## To access the client servers

    $ vagrant ssh rclient1 - rclient1.skynet.io
    $ vagrant ssh rclient2 - rclient2.skynet.io
    
## Clearing the environment

    $ vagrant destroy
