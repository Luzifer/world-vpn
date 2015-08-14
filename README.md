# Luzifer / World-VPN

You don't trust anyone to host an OpenVPN server for you to get around those YouTube "not available in your country" things and don't want to have one box running all the time for this? This repo might contain the solution for you if you trust it enough…

## Requirements

- A [DigitalOcean account](https://www.digitalocean.com/?refcode=9de366d7b61c)  
  (ref-link, you will get $10 start credit to play with)
- Python (install using `pip install -r requirements.txt`)
  - Ansible 1.9.x
  - Dopy 3.6.0
- OpenVPN module from Ansible Galaxy  
  (install using `ansible-galaxy install Stouts.openvpn`)
- OSX
  - [Tunnelblick](https://tunnelblick.net/)

## Configuration

Move the `vars/secret.yml.dist` to `vars/secret.yml` and configure all the variables provided there.

## Setup

Install Tunnelblick and ensure it's running (Ansible will create the VPN connection for you while execution). After you've installed Ansible and Tunnelblick you can create the VPN node using this command:

```
ansible-playbook -i inventories/localhost create.yml
```

You will get a fully configured Droplet at DigitalOcean containing an OpenVPN server ready for tunneling all your traffic via NewYork. If you're asked for username and password you need to use the password you specified before and the user `vpn`.

To remove all the things and ensure no more cost are generated, disconnect using Tunnelblick and execute this command:

```
ansible-playbook -i inventories/localhost destroy.yml
```
