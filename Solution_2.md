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

Lorsque nous avons travaillé, nous avons rencontré énormément d'erreurs. Malheureusement, je ne me souviens pas de toutes les erreurs.

### b. Prérequis

Il vous faut un accès au radius en tant que root. Il vous faut aussi le compte administrateur et le mot de passe de l'Active Directory. 



## II. Installation 

Installons tous les paquets nécessaires. 

```
apt-get install freeradius freeradius-utils samba libnss-winbind krb5-admin-server krb5-config ntp ntpdate
```

Lors de l'installation, krb5 devrait vous demander certaines choses. Pour le REALM, entrez '**CYBER.ISEN.FR**'. 

