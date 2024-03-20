## Usage

```
cookiecutter gh:Important-TakeAways/cookiecutter-vagrant-ansible
```

## Details
- This create a project foler with vagrantfile, ansible.cfg, inventory.txt, Readme.md, and roles folder


### Vagrant Information
1. "box_name", this is used to define the OS required to launch vm(s) used by Vagrantfile
- "debian/bookworm64" is debian 12
- "debian/bullseye64" is debian 11
- "debian/stretch64" is debian 10
- "debian/buster64" is debian 9
- "ubuntu/bionic64" is ubuntu 18.04
- "ubuntu/focal64" is ubuntu 20.04
- "ubuntu/jammy64" is ubuntu 22.04

2. "vm_count", this is used to define number os vm(s) to be launched by Vagrant
3. "vm_memory", this is used to define the memory/RAM for vm(s) to be launched by Vagrant
4. "network_type", this is used to define the network type used by vm(s) launched
        - Public: This helps to access anything in vm(s) to local host machine. Uses Bride network interface
        - Private: Well, this makes network private, Uses NAT interface