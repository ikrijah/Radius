# Configuration de Freeradius avec LDAP
## I. Freeradius
### a. Installation de Freeradius
### b. Configuration de ldap dans Freeradius
## II. LDAP


## I. Freeradius

### a. Installation de Freeradius 
``` 
apt-get install freeradius freeradius-utils
```

### b. Configuration de ldap dans Freeradius

Il vous faut d'abord quelques prérequis. 

L'adresse IP du LDAP : 10.10.5.1 
Le port par défaut : 389 
Domaine Name : cn=admin,dc=cyber,dc=isen,dc=fr
Il faut aussi le mot de passe du LDAP. Celui-ci devrait vous être fournit par un administrateur.


Après avoir installé Freeradius, nous pouvons commencer.

```
cd /home/radius/etc/freeradius/3.0/sites-enabled
vim default 
vim inner-tunnel
```

Vous pouvez très bien utiliser nano pour ouvrir les fichiers.
Il faut maintenant vérifier que tous les 'files' sont bien commentés dans le fichier default et inner-tunnel.

