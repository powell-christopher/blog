# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.network "forwarded_port", guest: 4000, host: 4000, host_ip: "127.0.0.1", id: "hexo"

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
      su ubuntu
      sudo apt-get update
      sudo apt-get install build-essential libssl-dev
      curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
      export NVM_DIR="$HOME/.nvm"
      [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
      [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
      nvm install node
      nvm use node
      npm install -g hexo-cli
  SHELL
end
