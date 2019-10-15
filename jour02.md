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
