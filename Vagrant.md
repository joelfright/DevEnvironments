# Vagrant Dev Environment

## Prior information

In order to install a vagrant client you must first need vagrant, vm virtual box and ruby installed.
See [here](https://github.com/khanmaster/vb_vagrant_installtion) for information on how to do this.

## Setting up the virtual machine

1) The first step is to find a folder in which you would like to install your vagrant.
2) Within this file you must open git bash as admin and enter `vagrant init`. This will make a file by which you can enter key information.
3) Once completing `vagrant init` you must open `Vagrantfile` and replace the predetermined data with the following:
```
Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

 config.vm.box = "ubuntu/xenial64"
 # creating a virtual machine ubuntu 
 config.vm.network "private_network", ip: "192.168.10.100"
 
end
```
4) Once this has been saved you are able to open up the git bash and type `vagrant up`. This will boot up your virtual machine.
5) Next you have to enter your virtual machine by using `vagrant ssh`.
6) Then upon completion you must update to the current version of linux with `sudo apt-get update -y`.
7) After this has been completed, you must install nginx with `sudo apt-get install nginx -y`.
8) You are then finally able to nagivate to your locally hosted virtual machine by typing the ip `192.168.10.100` into your browser url.

## Other useful commands

- To suspend the vagrant `vagrant suspend`.
- To reload vagrant `vagrant reload`.
- To destroy vagrant `vagrant destroy`.
- To exit out of vagrant `exit`.
