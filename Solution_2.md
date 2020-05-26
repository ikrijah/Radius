# Authentification Radius avec l'AD

## I. Introduction
### a. Explications des termes utilisés
### b. Prérequis

## II. Installation 

## III. Configuration

## IV. Test / Troubleshooting 


## I. Introduction

### a. Explications des termes utilisés

Afin de s'authentifier à l'aide des identifiants fournis lors de la connexion sur les workstations, nous avons besoin de plusieurs modules que je détaillerai ci-après.

**Radius** : serveur qui permet l'authentification des utilisateurs. C'est le serveur sur lequel nous allons travailler.     
**Active Directory (AD)** : serveur qui store toutes les données des utilisateurs ; identifiants et mot de passe salt hashés.       
**Samba (AD DC)**: Module qui agit comme DC (Domain Controller), c'est en fait un serveur informatique hébergeant l'annuaire Active Directory. Il est le centre des requêtes d'authentification.       
**Kerberos** : Kerberos est un protocole d'authentification réseau qui repose sur un mécanisme de clés secrètes (chiffrement symétrique) et l'utilisation de tickets, et non de mots de passe en clair.    
**Winbind** : Module qui récupère les comptes utilisateurs et les groupes présents dans l'Active Directory.    
**NTP** : Serveur de temps qui permet au serveur proxy de synchroniser son horloge sur celui de l'Active Directory.


### b. Prérequis

Il vous faut un accès au radius en tant que root. Il vous faut aussi le compte administrateur et le mot de passe de l'Active Directory. 



## II. Installation 

Installons tous les paquets nécessaires. 

```
apt-get install freeradius freeradius-utils samba libnss-winbind krb5-admin-server krb5-config ntp ntpdate
```

Lors de l'installation, krb5 devrait vous demander certaines choses. Pour le REALM, entrez '**CYBER.ISEN.FR**'. Pour le Kerberos server et l'Admin server, entrez '**workstations.cyber.isen.fr**'. Nous allons tout de même modifier ces configurations dans le fichier /etc/krb5.conf un peu plus tard.

Pas de problèmes jusque là !

## Configuration

#### Configuration de Samba

#### Configuration de Kerberos

#### Configuration de NTP

#### Configuration de Winbind


## IV. Test / Troubleshooting 

Nous avons rencontré énormément d'erreurs. Pour cela, nous vous ferons une liste exhaustive de ces erreurs ainsi que les pistes pour les supprimer. C'est pour cela que nous vous guiderons pour trouver l'origine de ces erreurs. 

Le moyen qui a été le plus efficace pour nous pour retracer ces erreurs était 'systemctl status'. Ceci nous permet de voir si un module est actif ou non et les erreurs qui sont en rouge expliquent parfois clairement où est le problème. Si vous avez modifié un fichier de configuration, il ne faut pas oublier de restart le service pour prendre en compte les modifications avec 'systemctl restart <nom_service>'. Exemples !

```
systemctl restart smbd 
systemctl status smbd 
systemctl restart freeradius
systemctl status freeradius
systemctl status winbind
systemctl status krb5-kdc
```

Vous pouvez utiliser cela pour à peu près tous les services se trouvant sous /etc/init.d.
