**Concept et théorique de Docker**

<img src="https://cloud.githubusercontent.com/assets/6421175/18341385/080cecc4-75aa-11e6-8392-7efbb01320e5.png" width="200">


Docker est un logiciel libre (sous licence Apache 2.0) à mi-chemin entre la virtualisation applicative et l'automatisation. Il permet de manipuler des conteneurs de logiciels. Il complète le conteneur Linux LXC (il n'utilise plus LXC depuis peu) en isolant les processus les uns des autres pour créer une virtualisation de haut niveau. 

Dans l'esprit docker: un processus = un conteneur.

Contrairement aux autres systèmes de (para) virtualisation, Docker n’embarque pas un système d’exploitation invité mais ne s’occupe que de la partie haut niveau. Il utilise le noyau de l'hôte et ne fait fonctionner que le strict nécessaire sur les invités.

Voici une vue du fonctionnement de Docker vs virtualisation :

<img src="https://cloud.githubusercontent.com/assets/6421175/18342656/298c074e-75b0-11e6-8b6c-9598b0569881.jpeg" width="800">

Docker c'est aussi un dépôt d'images à partir duquel vous pouvez télécharger et partager des applications sans avoir à réinventer la roue. 

Voici par exemple  l'architecture d'un serveur complet sous Docker:

Nous pouvons voir que notre hôte héberge quelques services, Docker et les fichiers de données persistantes (vos données en résumé). L'ensemble des applications sont "containerisées", permettant une souplesse, une facilité et une rapidité d'installation. Et si c'est cassé, ce n'est pas grave, on reconstruit avec 1 lignes de commandes.















source:

https://doc.ubuntu-fr.org/docker
