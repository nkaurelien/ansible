
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
gcloud compute ssh  ansible-deployer-instance-1 --zone=europe-west1-b
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
sudo nano .ssh/authorized_keys
cat .ssh/authorized_keys
````

Simple way to add public key to ~/.ssh/authorized_keys file on remote host, using ssh-copy-id command.

````shell script
ssh-copy-id -i ~/.ssh/id_rsa.pub linuxtechi@192.168.10.10
ls .ssh/
cat .ssh/authorized_keys
````
