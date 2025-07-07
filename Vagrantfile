Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"
  config.vm.box_version = "4.3.12"
  config.vm.hostname = "dvwa"
  # Adapter 1: NAT (default, internet access for ansible configuratino of DVWA)
  # Adapter 2: Host-only (for static IP on internal lab network)
  config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.post_up_message = "The DVWA VM has been created. After the ansible post-install script runs, access at 192.168.56.10"
    # Run apt update before installing Ansible
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
  SHELL
  # Install Ansible and run the setup
  config.vm.provision "ansible_local" do |ansible|
    ansible.install_mode = "default"
    ansible.playbook = "/vagrant/ansible/playbook.yml"
  end
end