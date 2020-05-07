# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes = [
  { :name => "centos-7", :box => "centos/7", :box_version => "1905.1" },
  { :name => "centos-8", :box => "centos/8", :box_version => "1905.1" },
  { :name => "fedora-31", :box => "fedora/31-cloud-base", :box_version => "31.20191023.0" },
  { :name => "fedora-32", :box => "fedora/32-cloud-base", :box_version => "32.20200422.0" },
]

provisioner = ARGV.length == 1 ? boxes.last[:name] \
  : ARGV.drop(1).select { |a| !a.start_with?("--") }.last

Vagrant.configure("2") do |config|
  config.vm.provider "libvirt" do |libvirt|
    libvirt.cpus = 2
    libvirt.memory = 1024
  end

  boxes.each do |opts|
    config.vm.define opts[:name] do |machine|
      machine.vm.box = opts[:box]
      machine.vm.box_version = opts[:box_version]

      if opts[:name] == provisioner
        machine.vm.provision "ansible" do |ansible|
          ansible.compatibility_mode = "2.0"
          ansible.playbook = "tests/test.yml"
          ansible.limit = "all"
        end
      end
    end
  end
end
