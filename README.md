# openvpn-deploy

This repo contains an Ansible playbook to deploy an OpenVPN server to your remote machine with Debian-based OS.

## Prerequisites

Here is a [guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) on how to install Ansible to your local machine

### System requirements
* Linux/macOS/WSL on Windows
* Python 3
* Ansible
* Remote machine with Debian-based OS
* SSH key for the remote machine

After the installation, make sure that `ansible --version` command works, if not, [you need to add Ansible to the PATH environment variable](https://stackoverflow.com/questions/45821068/why-cant-i-find-ansible-when-i-install-it-using-setup-py).

It's recommended to use WSL on Windows because Ansible requires some Python packages that are currently not available for Windows itself.

## Executing playbook

1. Clone this repo to your local machine or download its content.
2. Start playbook execution with the following command:

`ansible-playbook -i <IP of the machine to install VPN to>, --private-key <path to your ssh key> start-vpn.yml`.

For example:

`ansible-playbook -i 1.2.3.4, --private-key ~/.ssh/id_rsa start-vpn.yml`

3. Find `vpn-config.ovpn` file in the folder you executed the playbook from. You can use this file in any [OpenVPN client](https://openvpn.net/vpn-client/) to use your vpn. 
