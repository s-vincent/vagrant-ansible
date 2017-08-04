# vagrant-ansible

Sandbox and demo for Vagrant/ansible.

This project demonstrates some usages of vagrant together with ansible.

## Pre-requisites

You need at least one of the following packages:
* Virtualbox
* libvirtd
* lxc

Please note that not all vagrant boxes have a LXC version.

## Usage

To create and provision the peers defined in Vagrantfile:

`vagrant up`

Connect to peer1:

`vagrant ssh peer1`

Connect to peer2:

`vagrant ssh peer2`

To destroy everything:

`vagrant destroy`

## Limitations

For the moment only Debian-like (Debian, Ubuntu...) and RedHat-like (RedHat,
CentOS, Fedora...) boxes are supported for provisioning.

## License

All modules are under BSD-3 license.

## Links

* https://www.vagrantup.com/docs/index.html
* https://app.vagrantup.com/boxes/search
* http://docs.ansible.com/ansible/latest/index.html

