# multi-dev

The purpose of multi-dev is to provide a linux dev environment for MacOS,
and in association with that purpose has the following goals:
  * utilize a multitude of secure VMs
  * support fast filesystem mounts
  * minimize time to development and testing

## background

Multi-dev utilizes images from [roboxes.org](https://roboxes.org/),
the images are maintained by Ladar Levison with infrastructure provided by Lavabit.

## basic usage

Ensure that `vagrant` is installed:
```sh
brew install vagrant
```

The [Vagrantfile](Vagrantfile) provides a template for launching
virtual machines where the Home directory is mounted inside the VM.

Clone and enter this repo:
```sh
cd ~
git clone https://github.com/erikwilson-rc/multi-dev.git
cd multi-dev
```

We can ensure that our timezone is setup correctly within our VMs by installing
a vagrant plugin:
```sh
vagrant plugin install vagrant-timezone
```

And use default settings to quickly bring up a new dev enivornment:
```sh
# destroy an existing VM
vagrant destroy -f
# bring up a new VM (by default Ubuntu)
vagrant up
# access VM (root in VM -> User space HOME access)
vagrant ssh
```

Or modify enivornment variables to change how vagrant provisions:
```sh
# destroy any existing clustered VMs
NUM_NODES=2 vagrant destroy -f
# bring up two new VMs (using Alpine 3.16)
NUM_NODES=2 DISTRO=alpine316 vagrant up
# access first VM (root in VM -> User space HOME access)
NUM_NODES=2 vagrant ssh .1
```
