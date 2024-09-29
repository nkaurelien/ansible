
# Installer les dependences

````shell script
ansible-galaxy install -r requirements.yml
````

# Installer les pré-requis (si necessaire)

````shell script
ansible-playbook initial-setup.yml --limit=web_staging # staging or preprod environment
ansible-playbook initial-setup.yml --limit=web_test # test or dev environment

# ou
ansible-playbook initial-fullstack-setup.yml --limit=web_staging
ansible-playbook initial-fullstack-setup.yml --limit=web_test
````

# Creer la structure de dossier du projet web pour le nom de damaine

````shell script
ansible-playbook setup.yml --limit=web_staging --tags=iptables
````

# Deployer

````shell script
ansible-playbook deploy.yml --limit=web_staging
````

# Installer  nginx et le virtual host du domain

````shell script
ansible-playbook setup.yml --tags=nginx --limit=web_staging
````

# Installer certbot host et générer le certificat ssl pour le nom de domaine

````shell script
ansible-playbook setup.yml --tags=certbot --limit=web_staging
````
