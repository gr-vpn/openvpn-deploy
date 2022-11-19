# openvpn-deploy

This repo contains an Ansible playbook to deploy an OpenVPN server to your remote machine

## Prerequisites

Here is a [guide]((https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)) on how to install Ansible to your local machine

### System requirements
* Python 3
* Ansible
* Linux/macOS/WSL on Windows
* SSH key for the remote machine

After the installation, make sure that `ansible --version` command works, if not, you need to add 

It's recommended to use WSL on Windows because Ansible requires some Python packages that are currently not available for Windows itself.

## Executing playbook

1. Clone this repo to your local machine or download its content.
2. Update `hosts.yml` file with an ip or domain name of the machine you need to install OpenVPN to. It should look like this:
```yaml
all:
  children:
    vpn:
      hosts:
        1.2.3.4:
```
3. Start playbook execution with the following command:

`ansible-playbook -i hosts.yml --private-key <path to your ssh key> start-vpn.yml`.

For example:

`ansible-playbook -i hosts.yml --private-key ~/.ssh/id_rsa start-vpn.yml`

4. Find `vpn-config.ovpn` file in the folder you executed the playbook from. You can use this file in any [OpenVPN client](https://openvpn.net/vpn-client/) to use your vpn. 