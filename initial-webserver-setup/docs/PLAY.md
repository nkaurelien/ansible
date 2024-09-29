
# Tester la connexion

 ````shell script
ansible all -i inventory -m ping  -u root
ansible all -i inventory -m setup  -u root

# Options:
# -i (optionnel) pour choisir le fichier d'inventaire des serveurs
# -m le module a executer sur les hotes de l'inventaires
````
### Install dependencies

````shell script
ansible-galaxy install -r requirements.yml
````

### Excecuter en local en local
````shell script

ansible-playbook \
--connection=local \
--inventory 127.0.0.1, \
--extra-vars "ansible_user=nkaurelien ansible_become_pass=you_passwd ansible_password=you_passwd" \
--limit 127.0.0.1  -i inventory setup.yml  --tags=php,redis,memcached
````
Here

--connection – tells ansible to run the file locally.

-- inventory – tells ansible to consider this host name as an inventory [ Comma at the end is IMPORTANT]

-- limit – Limiting to only this host.

ansible_become_pass est le mot de passe sudo  
ansible_password est le mot de passe utilisateur  

#  Lancer un command Ad-Hoc (optionel)

````shell script
ansible all -a "df -h" -u root
ansible all -m apt -a "name=vim state=latest" -u root
````

# INstaller les pré-requis

````shell script
ansible-playbook initial-setup.yml

#pour le serveur local du developpeur
ansible-playbook \
--connection=local \
--inventory 127.0.0.1, \
--limit 127.0.0.1 initial-setup.yml -i inventory
````

# Creer la structure de dossier du projet web

````shell script
ansible-playbook setup.yml --tags=setup_deploy
````

# Installer les composant du runtime

````shell script
ansible-playbook setup.yml --skip-tags=setup_deploy,cerbot,
ansible-playbook setup.yml --tags=redis,memcached

# Installation selective des composants
#ansible-playbook setup.yml --tags=php,nginx
````

# Deployer

````shell script
ansible-playbook deploy.yml
````

# Credit
[Digital Occean: How To Install and Configure Ansible on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-20-04)
