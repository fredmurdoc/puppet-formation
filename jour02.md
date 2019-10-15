# JOUR 2
[TOC]

## les classes

On  définit et on déclare des classes.

On ne peut déclarer qu'une classe une seule fois

```puppet
# Class: bootstrap
#
#

class maclasse (
  
  $packages = {
    sshserver => 'openssh-server'
  },
  $services = {
    ssh => 'sshd'
  }
) {
  # declaration des ressources
  ## declaration de la classes avec include
  include manage_ssh
  ## declaration de la classes via le mode resource, afin de spécifier des parametres
  class {'manage_users':}
}

```


### directive Include

Permet d'inclure la definition d'une autre classes dans le catalogue.
Cette classe sera instanciée une seul fois au total

### utilisation de la ressource class

Ce type de déclaration n'est tolérée qu'une seule fois

```puppet
class {'manage_users':}
```

utilisation des variables
```puppet
include maclasse
notice($maclasse::packages['sshserver'])

```


## les modules

/etc/puppet/modules
classes du meme nom que le module 

Utilisation de PDK outil de developpement Puppet

̀`̀``puppet
cd production/modules
pdk new module apache
cd apache
pdk new class apache
̀``
Cela crée le module apache et le manifest manifests/init.pp


tests apres avoir créé un vhost www.example.com:80
```bash
curl -H 'Host: www.example.com' http://localhost:80/
```

```bash
ip a add  172.16.8.5  dev enp0s31f6
```