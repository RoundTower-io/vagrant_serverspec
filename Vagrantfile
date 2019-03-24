# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.box = 'hashicorp/precise64'

  config.vm.provision :shell, inline: <<-EOF
    sudo ufw allow 22
    yes | sudo ufw enable
    python -m SimpleHTTPServer 8000 &
  EOF

  config.vm.provision :serverspec do |spec|
    spec.pattern = '*_spec.rb'
    spec.error_no_spec_files = false
    spec.html_output = true
  end
end
