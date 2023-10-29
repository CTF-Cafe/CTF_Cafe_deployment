[![StackShare](http://img.shields.io/badge/tech-stack-0690fa.svg?style=flat)](https://stackshare.io/ctfcafe/ctfcafe)

This is the repo which contains deployement strategies for CTFCafe.

# Deployement Strategies

## Ansible
- 1 Server
- Difficulty : Easy

### Config the file [inventory.yaml](./ansible/inventory.yaml)
Change the `ansible_host` to the reachable IP Address of your server. 

If you would like a domain with https enabled, specify the `domain` property inside of `webserver01` like so :

```yaml
webserver:
  hosts:
    webserver01:
      ansible_host: xxx.xxx.xxx.xxx
      http_port: 80
      https_port: 443
      domain: dev.ctf.cafe
  vars:
    ansible_user: root
```

else just do not add the domain property and it will deploy on http reachable by ip.

Make sure to be able to ssh as root on the machine with your ssh key.

Launch command : `ansible-playbook -i inventory.yaml playbooks/setup.yml && ansible-playbook -i inventory.yaml playbooks/config.yml && ansible-playbook -i inventory.yaml playbooks/launch.yml`