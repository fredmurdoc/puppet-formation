# JOUR 1

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

