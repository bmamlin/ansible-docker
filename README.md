# Ansible via Docker

This is a little container I use to run ansible on my MacBook Pro without having to install ansible locally.

## Assumptions

* Your private key is in `~/.ssh/id_rsa` and likely (hopefully) passphrase encrypted, so you'll benefit from the use of ssh-agent in these scripts.
* You have docker installed and don't want to install ansible locally.

## Setup

Build the container:

```bash
$ docker build -t ansible .
```

Link to scripts (I have ~/bin in my path, so create soft links to them from there):

```bash
$ ln -s ansible ~/bin/ansible
$ ln -s ansible-playbook ~/bin/ansible-playbook
```

## Usage

Assuming you have the script on your path, the following command will run the `ansible-playbook` script, which invokes the ansible Docker image and runs the ansible-playbook command against the current directory on the host.

```bash
$ ansible-playbook -i production -u username -b site.yml
```
