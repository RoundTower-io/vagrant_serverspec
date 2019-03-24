# vagrant_serverspec
A simple vagrant configuration demonstrating the use of ServerSpec

# Overview
This demonstrates the concept of Test-Driven Infrastructure.

The Vagrantfile contains a call to the serverspec plugin. To quote the documentation, ServerSpec:
```
Serverspec tests your servers’ actual state by executing command locally, via SSH, 
via WinRM, via Docker API and so on. So you don’t need to install any agent softwares 
on your servers and can use any configuration management tools, Puppet, Ansible, 
CFEngine, Itamae and so on.

But the true aim of Serverspec is to help refactoring infrastructure code.
```

The file "vagrant_spec.rb" tells ServerSpec what to expect the vagrant server to have when it boots. The contents
are very English-like and easy to understand:

```
describe package('ufw') do
  it { should be_installed }
end

describe service('ufw') do
  it { should be_enabled }
  it { should be_running }
end

describe port(22) do
  it { should be_listening }
end

describe port(8000) do
  it { should be_listening }
end

```

So, when vagrant starts the image, it should have ufw installed and running, an ports 22 and 8000 should be listening.