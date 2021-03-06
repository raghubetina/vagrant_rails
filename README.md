# Setting up a Vagrant Box with Ruby 2 and Rails 4

## Steps

 - `vagrant init precise64 http://files.vagrantup.com/precise64.box`
 - Edit Vagrantfile; change `# config.vm.network :forwarded_port, guest: 80, host: 8080` to `config.vm.network :forwarded_port, guest: 3000, host: 4000`
 - `vagrant up`
 - `vagrant ssh`
 - `sudo apt-get update`
 - `sudo apt-get install curl`
 - `\curl -L https://get.rvm.io | bash -s stable`
 - `nano ~/.bash_profile`
 - Add `source ~/.profile` to top of file, save, exit nano
 - `source ~/.bash_profile`
 - `source ~/.rvm/scripts/rvm`
 - `rvm autolibs packages`
 - `rvm install --autolibs=packages ruby`
 - `gem update --system`
 - `sudo apt-get install nodejs`
 - `sudo apt-get install openssl`
 - `gem install rails --no-ri --no-rdoc`
 - `cd /vagrant`
 - `rails new test_app` -- Ensure bundle completes
 - `cd test_app; rails server` -- Ensure server starts up. Test http://localhost:4000
 - `cd ..; rm -rf test_app`
 - `exit`
 - `vagrant package`

## Other

Useful alias to shutdown all VMs:

    alias shutdown-vms="VBoxManage list vms | cut -f 1 -d ' ' | xargs -I NAME sh -c 'VBoxManage controlvm NAME poweroff ; VBoxManage unregistervm NAME' ; rm -rf ~/VirtualBox\ VMs/*"

## TODO

  - Put this all into some kind of automated provisioning.
  - Make it drop you into the shared folder when you vagrant ssh.
