# Ansible role for Wireguard

[Wireguard](https://wireguard.com/) is an extremely simple yet fast and modern VPN that utilizes state-of-the-art cryptography. It aims to be faster, simpler, leaner, and more useful than IPsec, while avoiding the massive headache.

And this ansible role for deploy wireguard for hosts in your inventory.

## Configure & Install

Place role directory in your Ansible installation, then create playbook and change host_vars for each hosts

There is playbook file for wireguard role:
```
- name: Deploy Wireguard
  hosts: "*"
  vars:
    # Wireguard routing networks
    wireguard_nets: "10.111.0.0/24,172.16.0.0/24"
	# Public keys from disabled hosts
	wireguard_revoked:
	  - Ih7pTd8Ee2J7KFNDANkNrCM9Yd4g7gMtCHPr37aoIxU=

  roles:
    - role: wireguard
```

### host_vars variables
```
wireguard:
  ip: "10.111.0.1"
  port: "51420"
```
For Wireguard server you must set `external_addr` parameter which is public IP address of the server.

### Example run
You must use `-e wireguard_server` ansible variable which is hostname of your Wireguard server, for example: `-e wireguard_server=server_host`

[MIT License](https://github.com/tobishua/ansible-wireguard/blob/master/LICENCE).
