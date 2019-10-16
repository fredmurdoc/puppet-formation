# JOUR03

[TOC]


## define vs. class

## Utilisation de hiera



## reports

### Sur l'agent

/opt/puppetlabs/puppet/cache/state/last_run_report.yaml


### Sur le serveur


/opt/puppetlabs/server/data/puppetserver/reports



## environnements


On pointe vers un env particulier
```bash
puppet agent -t --environnement=test
```

### simulation de facts

```bash
FACTER_cle=valeur puppet agent -t --environnement=test
```
on l'a recupere via

```puppet
$facts['cle']
```


## arborescence de projet de reference

Cible:  architecture n-tiers web - app - bdd


Les machine

 - web01 : 
 - srv01
 - bdd01

Les rôles
 - web : pour les app web, il utilise les profils base, web
 - app : pour les serveur d'app
 - db : pour les applicatio base de données


Les profiles
 - base 
 - web
 - tomcat
 - db




créer une arboresence : 

 - hiera.yml
 - data
 - manifests
   + site.pp
 - modules
 - site
   + role (via pdk)
   + profile (via pdk)
     * base
     * db

```bash
cd site
pdk new module role
pdk new module profile
cd profile/
pdk new class base
pdk new class db
pdk new class web
pdk new class app
cd ../role
pdk new class base
pdk new class web
pdk new class app
pdk new class db
```


### Chargement de modules tiers

Installer bolt pour disposer de r10k


```bash
apt install puppet-bolt
```
#### utilisation de r10k

r10k permet d'installer des deploiements ?

/opt/puppetlabs/bolt/bin/r10k


faire un fichier de conf


Rechercher mysql sur puppet forge
https://forge.puppet.com/puppetlabs/mysql


Ajouter ce qui est recommande via r10k

Puis aller dans l'obglet dependace et les ajouter aussi

̀```Puppetfile
mod 'puppetlabs-mysql', '10.2.0'
mod 'puppetlabs-stdlib', '6.1.0'
mod 'puppetlabs-translate', '2.0.0'*
```
```bash
/opt/puppetlabs/bolt/bin/r10k puppetfile install -v
```

Par convention ca ajoute rles modules dans le repoertoire `modules`





srv01 -> app
srv02 -> db 
web01 -> rpapache