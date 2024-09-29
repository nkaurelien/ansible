INSTALL.m

### Préréquits
```text
python >= 2.6
requests >= 2.18.4
google-auth >= 1.3.0
```


```` shell script
$ sudo apt install build-essential
$ sudo apt install python-pip
$ pip install google-auth requests
````

### Lien utile

[Google Cloud Platform Guide](https://docs.ansible.com/ansible/latest/scenario_guides/guide_gce.html)

[gcp_compute_instance – Creates a GCP Instance]([https://link](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_module.html))

[gcp_compute_instance_template – Creates a GCP InstanceTemplate]([https://link](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_template_module.html))



# install ansible 

````shell script
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible
````

# Commandes de base

Vous devez a préalable ajouter installer le sdk gcloud, pour avoir l'outil de commande gcloud dans votre terminal, Ou tout simple utiliser le cloud shell etant connecter dans la console web

###

#### Lister les instances
```shell script
gcloud compute instances list
```

#### Creer une instance
On va creer deux instances installer en belgique

````shell script
 $ gcloud compute instances livraison-express-staging-instance-1 livraison-express-staging-instance-2  --zone=europe-west1-b --machine-type=n1-standard-1 --image=n1-standard-1 

 $ gcloud compute instances list
````

[voir plus](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create)


#### Ce connecter via ssh a une instance
```shell script
gcloud compute ssh  ansible-deployer-instance-1
```

La premiere connexion va generer des clés ssh dans votre dossier d'utilisateur de cloud shell.

````shell script
ls .ssh/
google_compute_engine  google_compute_engine.pub  google_compute_known_hosts
````
et aussi ajouter votre cle au metadonnées du projet afin que Toutes les instances de VM définies dans le projet disposeront de ces clés SSH. 

et aussi creer un compte  dans la machine virtuelle ansible-deployer-instance-1, si etes connecter au compte cloudshell multicanalservices@cloudshell par exemple , vous aurez aussi le compte multicanalservices@ansible-deployer-instance-1

et aussi ajouter la clé public dans le fichier `.ssh/authorized_keys` de la machine  ansible-deployer-instance-1

````shell script
ls .ssh/
cat .ssh/authorized_keys
````

# Install requirement

ansible-galaxy install -r requirements.yml


# create secret file

Then you'll need to create the secrets.yml file, you can use ansible vault:

````shell script
ansible-vault create secrets.yml
````
Then fill it with these pieces of information:

````text
github_user: your_username
github_token: your_github_access_token
````
To edit this file, you can use the following command

````shell script
ansible-vault edit secrets.yml
````