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


Après avoir installé Freeradius, nous pouvons commencer. Vous pouvez très bien utiliser nano pour ouvrir les fichiers. Il faut maintenant vérifier que tous les 'files' sont bien **commentés** dans le fichier default et inner-tunnel.

```
cd /etc/freeradius/3.0/sites-enabled/
vim default 
vim inner-tunnel
```

![alt text](images/Screenshot1.JPG)

Dans ces mêmes fichiers, il faut vérifier que le module ldap soit bien **décommenté**.

![alt text](images/Screenshot2.JPG)



Configurons le fichier dictionary.

```
cd ..
vim dictionary
```

A la fin du fichier, ajoutez la ligne suivante :

```
VALUE Auth-Type LDAP 5
```



Le module ldap peut ne pas être installé. Pour cela, installez-le :

```
apt install freeradius-ldap
```



Passons maintenant à la configuration du fihcier ldap :

```
cd mods-available/
vim ldap
```

![alt text](images/Screenshot3.JPG)

