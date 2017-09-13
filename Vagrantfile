Vagrant.configure(2) do |config|
  config.vm.define "devops-box" do |devbox|
    devbox.vm.box = 'bento/ubuntu-16.04'
    devbox.vm.network "private_network", ip: "192.168.199.9"
    devbox.vm.synced_folder '..', '/projects'
    devbox.vm.provision "shell", path: "scripts/install.sh"
  end
end
