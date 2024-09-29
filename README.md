
# Install ansible on deployer machine

Login the admin console and run this in cloudshell

````shell script
$ gcloud compute ssh  ansible-deployer-instance-1 --zone=europe-west1-b
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible
````

## Install

### Inventory file

Create `inventory` file in project root. You should specify ip address of your
server in this file.

```
[web]
46.101.210.137
```

### Install dependencies

```bash
ansible-galaxy install -r requirements.yml
```

### Environment variables

Copy `vars/main.yml.example` to `vars/main.yml` and change variable values for
your needs. For security reasons you may want to encrypt this file using
ansible-vault:
```bash
ansible-vault encrypt vars/main.yml
```
And then edit this file
with
```bash
ansible-vault edit vars/main.yml
```
