# JOUR 1
[TOC]

## Objectifs

Utilisation de Puppet et son amdinistration.

Langage et ses règles.

## Mes Objectifs

 - Ce que l'on peut Puppetiser ou pas.
 - Tests unitaires ?
 - Automatisation
 - mieux cerner nos besoins de production
 - envisager la cible idéale pour la refonte Puppet



## Description générale

Puppet gère un état d'un noeud.

L'agent Puppet peut être lancé en daemon ou de façon manuelle

L'agent puppet peut être exécuté en autonomie (sans master) en utilisant la commande 

```bash 
puppet apply mon_manifest.pp
```

### les facts

Collecte les informations d'un noeuds et les formatte dans un format Ruby

```bash
facter 
```


On peut interroger les données via facter


```bash
facter os 
```
Interoggerune sous structure 

```bash
facter os.architecture 
```


avoir la liste total des elements interrogeables

```bash
facter --list-block-groups --list-cache-groups
```

### les manifests

Code Puppet qui décrit la cible.

C'est à ce code d'assurer l'étanchéité entre les noeuds

### les modules

## Le langage

Tout est `resource` dans Puppet

Pour connaitre la liste des resources possibles

```bash
puppet describe --list
```

Pour générer du code puppet à partir d'une ressource existante

```bash
puppet resource <type> <args...>
```

Pour connaitre la liste des ressoucrs que l'on peut générer

```bash
puppet resources types
```



### les variables

```puppet
## types de variables 

$var = 'mavariables'

$tableau = [ 'test', $var ]

$dictionnaire = {
  cle => 'valeur',

}

$complexe = [
  {
    'prenom' => 'frédéric',
    'nom'    => 'Gontier',
  },
  'machaine',
]

## recupère les valeurs

$test = $dictionnaire[cle]

Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds d'affichage
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 secondsmon debug') ## necessite l'option --debug
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds"ma variable test : ${test}")
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds"tableau premier indice : ${tableau[0]}")
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds"dictionnaire index cle : ${dictionnaire['cle']}")
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds
notice("utilisation des facts os.architecture : ${os[architecture]}")

warning("utilisation des facts os.family : ${facts['os']['family']}")

err('mon erreur 1 == 0')

## utilisation des notifications pour afficher que sur les agents
notify{'montitre' :
  message  => "complexe : Bonjour ${complexe[0]['prenom']} ${complexe[0]['nom']}, voila ton message : '${complexe[1]}'",
  withpath => true,
}


```

```bash
puppet apply vars.pp 
```

```sysout
Notice: Scope(Class[main]): ma variable test : valeur
Notice: Scope(Class[main]): tableau premier indice : test
Notice: Scope(Class[main]): dictionnaire index cle : valeur
Notice: Scope(Class[main]): utilisation des facts os.architecture : amd64
Warning: Scope(Class[main]): utilisation des facts os.family : Debian
Error: Scope(Class[main]): mon erreur 1 == 0
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Notify[montitre]/message: complexe : Bonjour frédéric Gontier, voila ton message : 'machaine'
Notice: /Stage[main]/Main/Notify[montitre]/message: defined 'message' as 'complexe : Bonjour frédéric Gontier, voila ton message : \'machaine\''
Notice: Applied catalog in 0.01 seconds
```

### Les conditions

```puppet
if $facts['kernel'] == 'windows' {
  warning('code not implemented')
}
elsif $facts['kernel'] == 'linux' {
  notice('linux is there !!!')
}
else {
  error('system not supported')
}


if $facts['os']['family'] =~ '^[a-zA-Z]+ian' {
  warning("OS Family (${facts['os']['family']}) is Debian family!!!!")
}

if $facts['hostname'] =~ '^srv\d+.+' {
  notify{'Real client' :
    message => "your server hostname (${facts['hostname']}) is not an master !!! "
    }
}

case $facts['hostname']{
  /master/ : {warning('master side!!!!')}
  /srv(\d+)/ : {warning("client side!!!! ${1}")}
  /web(\d+)/ : {warning("web side!!!! ${1}")}
  default: { err('unknown')}
}


$packages = $facts['os']['family'] ? {
  'Debian' => ['apache2'],
  'RedHat' => ['httpd'],
}

notice("apache packages : ${packages}"")

```

```bash
puppet apply conditions.pp 
```

```sysout
Notice: Scope(Class[main]): linux is there !!!
Warning: Scope(Class[main]): OS Family (Debian) is Debian family!!!!
Warning: Scope(Class[main]): client side!!!! 01
Notice: Scope(Class[main]): apache packages : [apache2]"
Notice: Compiled catalog for srv01.formation.lan in environment production in 0.02 seconds
Notice: your server hostname (srv01) is not an master !!! 
Notice: /Stage[main]/Main/Notify[Real client]/message: defined 'message' as 'your server hostname (srv01) is not an master !!! '
```

## Configuration Puppet Master

```/etc/puppetlabs/puppet/puppet.conf

[server] # conf master
....
[main] # conf agents
server = master #alias réseau du master

```

On peut demander de la doc sur les sections de configuration par exemple

```bash
puppet config print --section master autosign
```
On peut modifier la config via la commande

```bash
puppet config set --section master autosign /etc/puppetlabs/puppet/autosign.conf
```


#### test de l'agent
```puppetagent
puppet agent -t 
```

```sysout
Info: csr_attributes file loading from /etc/puppetlabs/puppet/csr_attributes.yaml
Info: Creating a new SSL certificate request for srv01.formation.lan
Info: Certificate Request fingerprint (SHA256): E5:E6:F0:B5:21:E0:D0:A4:E4:0F:D9:1C:55:BE:C4:FD:2F:B2:51:A9:CB:6F:D2:E7:83:B1:E8:36:A0:87:5E:7F
Info: Certificate for srv01.formation.lan has not been signed yet
Couldn't fetch certificate from CA server; you might still need to sign this agent's certificate (srv01.formation.lan).
Exiting now because the waitforcert setting is set to 0.
```

#### Signature de larequest de l'agent

```bash
puppetserver ca list
puppetserver ca sign --certname srv01.formation.lan
```

> On peut elaborer un script de validatio  via l'entrée `autosign`
>> La CSR est validée si ce script a un code retour = 0

### /etc/puppetlabs/puppet/ssl

Contient tous les certificats


## Organisation du code

### répertoire `/etc/puppetlabs/code`

#### repertoire `environments`

Contient les différents environnnements suivis par les agents

#### repertoire `environments/production/manifests`

Contient la base de code des manifests