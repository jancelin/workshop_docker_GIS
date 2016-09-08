**Concept et théorique de Docker**

<img src="https://cloud.githubusercontent.com/assets/6421175/18341385/080cecc4-75aa-11e6-8392-7efbb01320e5.png" width="200">


Docker est un logiciel libre (sous licence Apache 2.0) à mi-chemin entre la virtualisation applicative et l'automatisation. Il permet de manipuler des conteneurs de logiciels. Il complète le conteneur Linux LXC en isolant les processus les uns des autres pour créer une virtualisation de haut niveau. 

Dans l'esprit docker: un processus = un conteneur.

Contrairement aux autres systèmes de (para) virtualisation, Docker n’embarque pas un système d’exploitation invité mais ne s’occupe que de la partie haut niveau. Il utilise le noyau de l'hôte et ne fait fonctionner que le strict nécessaire sur les invités.

Voici une vue du fonctionnement de Docker vs virtualisation :

<img src="https://cloud.githubusercontent.com/assets/6421175/18343006/bf153dd4-75b1-11e6-83e5-4189e3018ad6.png" width="800">

Docker c'est aussi un dépôt d'images à partir duquel vous pouvez télécharger et partager des applications sans avoir à réinventer la roue. 

Voici par exemple  l'architecture d'un serveur complet sous Docker:

Nous pouvons voir que notre hôte héberge quelques services, Docker et les fichiers de données persistantes (vos données en résumé). L'ensemble des applications sont "containerisées", permettant une souplesse, une facilité et une rapidité d'installation. Et si c'est cassé, ce n'est pas grave, on reconstruit avec 1 lignes de commandes.

<img src="https://cloud.githubusercontent.com/assets/6421175/18342843/ffbebfb4-75b0-11e6-82f1-3689d2c35825.jpg" width="800">

____________________________________________________________________

Installation de docker:

```
#docker-engine
  sudo apt-get update
  sudo apt-get install apt-transport-https ca-certificates
  sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
  sudo nano /etc/apt/sources.list.d/docker.list

		# add
		deb https://apt.dockerproject.org/repo ubuntu-trusty main
		#ctrl o

  sudo apt-get update
  sudo apt-get purge lxc-docker
  apt-cache policy docker-engine
  sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual
  sudo apt-get update
  sudo apt-get install docker-engine
  sudo service docker start
  sudo groupadd docker
  sudo usermod -aG docker $USER
  
#docker-compose
  apt-get install pip
  pip install docker-compose
  curl -L https://github.com/docker/compose/releases/download/1.8.0/run.sh > /usr/local/bin/docker-compose
  chmod +x /usr/local/bin/docker-compose
```

https://docs.docker.com/engine/installation/


____________________________________________________________________

**Commandes essentielles de Docker**

* ```docker pull jancelin/docker-lizmap``` --> construit l'image venant de dockerhub.
* ```docker docker build -t jancelin/docker-lizmap git://github.com/jancelin/docker-lizmap ```--> construit l'image via mon dépôt github, permet de voir toute l'installation.
* ```docker images``` --> Voir les images disponible dans son docker
* ```docker rmi name_of_image --> supprime l'image```.
* ```docker run --restart="always" --name "websig-lizmap" -p 8081:80 -d -t -v /your_qgis_folder:/home:ro -v /your_config_folder:/home2 jancelin/docker-lizmap ```--> démarre lizmap container
* ```docker ps -a ```--> liste des container et status.
* ```docker start name_container``` --> démarre container.
* ```docker stop name_container``` --> arrête container.
* ```docker rm name_container``` --> supprime le container (Possibilité de : docker stop name_container && docker rm name_container)
* ```docker exec -it name_container bash ```--> rentre dans le container avec une session root shell.
* ```docker cp name_container:/file/path/within/container /host/path/target``` ---> copie des fichier du container vers l'hôte. 
* ```docker exec -i moncontainer /bin/bash -c 'cat > /inside-container-file' < fichier-exterieur``` ---> copie des fichiers de l'hôte vers le container 
* ```docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)``` ---> arrête et supprime tout les containers
* ```docker stats `docker ps | awk '{print $NF}' | grep -v NAMES```` ---> voir les stats des containers
* .... ---> https://docs.docker.com/userguide/ 

**Docker-compose**

```
Define and run multi-container applications with Docker.

Usage:
  docker-compose [-f=<arg>...] [options] [COMMAND] [ARGS...]
  docker-compose -h|--help

Options:
  -f, --file FILE             Specify an alternate compose file (default: docker-compose.yml)
  -p, --project-name NAME     Specify an alternate project name (default: directory name)
  --verbose                   Show more output
  -v, --version               Print version and exit
  -H, --host HOST             Daemon socket to connect to

  --tls                       Use TLS; implied by --tlsverify
  --tlscacert CA_PATH         Trust certs signed only by this CA
  --tlscert CLIENT_CERT_PATH  Path to TLS certificate file
  --tlskey TLS_KEY_PATH       Path to TLS key file
  --tlsverify                 Use TLS and verify the remote
  --skip-hostname-check       Don't check the daemon's hostname against the name specified
                              in the client certificate (for example if your docker host
                              is an IP address)

Commands:
  build              Build or rebuild services
  config             Validate and view the compose file
  create             Create services
  down               Stop and remove containers, networks, images, and volumes
  events             Receive real time events from containers
  help               Get help on a command
  kill               Kill containers
  logs               View output from containers
  pause              Pause services
  port               Print the public port for a port binding
  ps                 List containers
  pull               Pulls service images
  restart            Restart services
  rm                 Remove stopped containers
  run                Run a one-off command
  scale              Set number of containers for a service
  start              Start services
  stop               Stop services
  unpause            Unpause services
  up                 Create and start containers
  version            Show the Docker-Compose version information
```
source: https://docs.docker.com/compose/reference/overview/
