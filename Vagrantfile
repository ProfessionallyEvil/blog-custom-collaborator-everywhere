Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-24.04"
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = 2048
  end
  config.vm.provider "libvirt" do |lv,override|
    lv.cpus = 2
    lv.memory = 2048
    override.vm.synced_folder ".", "/vagrant", type: "nfs", nfs_version: "4"
  end
  config.vm.provision "shell", inline: <<-SHELL
    curl -fsSL https://get.docker.com | bash -xs - 2> ~vagrant/docker_install.log
    usermod -aG docker vagrant
  SHELL
end
