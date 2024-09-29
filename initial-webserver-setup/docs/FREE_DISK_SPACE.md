## Affiche espace disque
`df [options] [devices]`

````shell script
# Voir Espace occuper
df -H --o
df /dev/sda1
````

## Affiche espace d'un dossier

````shell script
# Voir Espace occuper
du -hs journal/*
# Voir Espace occuper par tout les fichiers
du -a journal/*
# top top des plus gros dossiers
du -a /etc/ | sort -n -r | head -n 10
````


## Nettoyer le journal

````shell script
# Voir Espace occuper
journalctl --disk-usage
# Nettoyer par jour
journalctl --vacuum-time=10d
# Nettoyer par taille
journalctl --vacuum-time=500M
````

