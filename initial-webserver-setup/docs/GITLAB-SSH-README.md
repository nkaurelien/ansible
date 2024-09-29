# livraison-express-iac

Copier les cles dans le dossier `~/.ssh/` sur le serveur cloud
ou alors generer une autre pair de clés 
````shell script
ssh-keygen -t rsa -b 2048 -f ~/.ssh/id_rsa_gitlab
# taper juste la touche entrer a chaque fois pour continuer
# ceci doit creer un clé sans passphrase(mot de passe) et avec le bon commentaire
````
 
####Installer la clé gitlab

Aller a https://gitlab.com/profile/keys

````shell script
sudo apt install xclip -y
xclip -sel clip < ~/.ssh/id_rsa_gitlab.pub 
````
[voir la suite ici](https://docs.gitlab.com/ee/ssh/#adding-an-ssh-key-to-your-gitlab-account)

1- Ajouter la cle a gitlab
````shell script
eval `ssh-agent -s`
ssh-add ~/.ssh/id_rsa_gitlab
````

On va editer le ficher `~/.ssh/config` pour eviter de faire a nouveau ssh-add
````shell script
sudo apt install nano
nano ~/.ssh/config
```` 
Ajouter le contenu suivant 

````text

# GitLab.com
Host gitlab.com
  Preferredauthentications publickey
  IdentityFile ~/.ssh/id_rsa_gitlab

````
Pour sauvegarder , faite CTRL + O, ENTER, CTRL + X

2- Tester la clé publique est accepter sur gitlab
````shell script
ssh -T git@gitlab.com
# affiche: Welcome to GitLab, @<username>!
# si aucun message ne s'affiche, essayez
ssh -Tvvv git@gitlab.com
````


2- Cloner le projet
````shell script
git clone git@gitlab.com:multicanalservices/livraison-express-iac.git
cd ./livraison-express-iac
# git pull origin master
# git reset --hard origin/master
````
