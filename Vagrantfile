# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Prevent TTY Errors (copied from laravel/homestead: "homestead.rb" file)... By default this is "bash -l".
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
 
  # OS selection
  config.vm.box = "debian/stretch64"
  # config.vm.box = "centos/7"

  # disable NFS share
  # config.vm.synced_folder ".", "/vagrant", type: "nfs", nfs_version: "4", nfs_udp: false, disabled: true
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provision 'Initial setup', type: 'shell', path: "provisioning/scripts/setup.sh"
  config.vm.provision 'Wait for unattended-upgrades', type: 'shell', path: "provisioning/scripts/wait_unattended_upgrades.sh", args: %w( dpkg apt unattended-upgrade )

  config.vm.define "peer1", primary: true do |peer|
    peer.vm.hostname = "peer1"
    peer.vm.network :private_network, ip: '192.168.120.11', lxc__bridge_name: 'lxcbr0'
  end
  
  config.vm.define "peer2" do |peer|
    peer.vm.hostname = "peer2"
    peer.vm.network :private_network, ip: '192.168.120.12', lxc__bridge_name: 'lxcbr0'
  end
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    # ansible.verbose = 'vvv'

    ansible.groups = {
      "web-group" => ["peer1", "peer2"],
    }
  end
end

