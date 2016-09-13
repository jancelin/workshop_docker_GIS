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

<span style="font-size:5px;">
```
#docker-engine
  sudo apt-get update
  sudo apt-get install apt-transport-https ca-certificates
  sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
  sudo nano /etc/apt/sources.list.d/docker.list
		# add line
		deb https://apt.dockerproject.org/repo ubuntu-trusty main
		# ctrl o
  sudo apt-get update
  sudo apt-get purge lxc-docker
  apt-cache policy docker-engine
  sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual
  sudo apt-get update
  sudo apt-get install docker-engine
  sudo service docker start
  sudo groupadd docker
  sudo usermod -aG docker $USER
```

https://docs.docker.com/engine/installation/

https://docs.docker.com/docker-for-windows/


____________________________________________________________________

**Commandes essentielles de Docker**

```
$ docker
…
Commands:
    attach    Attach to a running container
    build     Build an image from a Dockerfile
    commit    Create a new image from a container's changes
    cp        Copy files/folders from a container's filesystem to the host path
    create    Create a new container
    diff      Inspect changes on a container's filesystem
    events    Get real time events from the server
    exec      Run a command in an existing container
    export    Stream the contents of a container as a tar archive
    history   Show the history of an image
    images    List images
    import    Create a new filesystem image from the contents of a tarball
    info      Display system-wide information
    inspect   Return low-level information on a container
    kill      Kill a running container
    load      Load an image from a tar archive
    login     Register or log in to a Docker registry server
    logout    Log out from a Docker registry server
    logs      Fetch the logs of a container
    port      Lookup the public-facing port that is NAT-ed to PRIVATE_PORT
    pause     Pause all processes within a container
    ps        List containers
    pull      Pull an image or a repository from a Docker registry server
    push      Push an image or a repository to a Docker registry server
    restart   Restart a running container
    rm        Remove one or more containers
    rmi       Remove one or more images
    run       Run a command in a new container
    save      Save an image to a tar archive
    search    Search for an image on the Docker Hub
    start     Start a stopped container
    stop      Stop a running container
    tag       Tag an image into a repository
    top       Lookup the running processes of a container
    unpause   Unpause a paused container
    version   Show the Docker version information
    wait      Block until a container stops, then print its exit code
…
```

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
