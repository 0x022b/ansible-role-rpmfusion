# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes = [
  { :name => "centos-7", :box => "centos/7", :box_version => "1905.1" },
  { :name => "centos-8", :box => "centos/8", :box_version => "1905.1" },
]

provisioner = ARGV.length == 1 ? boxes.last[:name] \
  : ARGV.drop(1).select { |a| !a.start_with?("--") }.last

Vagrant.configure("2") do |config|
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
