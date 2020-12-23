# Ansible CIS Benchmark for CentOS Linux 7

[Ansible](https://www.ansible.com/) role for auditing and hardening [CentOS Linux](https://www.centos.org/) 7 Vagrant VM (virtual machine) based on the [Center for Internet Security (CIS)](https://www.cisecurity.org/) [Benchmark](https://www.cisecurity.org/benchmark/centos_linux/).

## Prerequisites

1. [Vagrant](https://www.vagrantup.com/docs/installation)
2. [CentOS Linux 7 Vagrant box](https://app.vagrantup.com/centos/boxes/7)
3. [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Usage

1. Clone Git repository.
```sh
$ git clone git@github.com:adhipras/ansible-cis-benchmark-centos-7.git
```

2. Go to `ansible-cis-benchmark-centos-7` directory.
```sh
$ cd ansible-cis-benchmark-centos-7
```

3. Create and configure virtual machine.
```sh
$ vagrant up
```

## Disclaimer

There are some sections I didn't include because I think it would be better to be handled manually, such as disk partition.
