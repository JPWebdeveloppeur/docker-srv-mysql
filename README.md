# Docker environnement Php 7.2.34-apache for Symfony 4.4

Il s'agit d'une image Docker qui vous permet d'avoir un environnement de développement local avec PHP, MySQL et phpMyAdmin et d'utiliser la même image PHP dans votre application de production.

Outre l'image de base Apache PHP 7.2, il comprend également les modules suivants:

```
* apcu 			* mbstring 			* SimpleXML
* calendar 		* mysqlnd 			* soap
* Core 			* libxml 			* sodium
* ctype 		* openssl 			* SPL
* curl 			* mysqlnd 			* sqlite3
* date 			* openssl 			* SimpleXML
* dom 			* pcre 				* sodium
* fileinfo 		* PDO 				* SPL
* filter 		* pdo_mysql 		        * standard
* ftp 			* pdo_sqlite 			* tokenizer
* gd 			* Phar 		                * xml
* hash 			* posix 		        * xmlreader
* iconv 		* readline 			* xmlwriter
* json 			* Reflection		        * xsl
* libxml 		* Session			* Zend OPcache
* zip			* zlib
```

**Note:**  Vous pouvez si vous souhaitez rajouter des extensions via le [Dockerfile](docker/php/dockerfile)

### Comment ça marche ?

* Pendant que vous développez votre application, vous utilisez `docker-compose` qui utilise la base` Dockerfile` et monte votre dossier local . Cela signifie que vous pouvez développer votre application sans redémarrer le conteneur. Le `docker-compose` démarre également une base de données MySQL et un conteneur phpMyAdmin pour une administration facile. 

# Démarrage de l'environnement de développement avec PHP, MySQL et phpMyAdmin 

➔ Ouvrez un terminale type bash et placez-vous dans le répertoire ou se trouve le docker-compose puis saisir :

```
docker-compose up -d ou docker-compose up --build
```
➔ Pour accéder au shell dans un conteneur, il faut lancer la commande suivante :
```
  docker exec -it container_name zsh 
```
➔ Lancer l'installation de symfony : 
```
   composer create-project symfony/website-skeleton:"^4.4" my_project_name
```

➔ Voici l'url pour l'applicationweb :

    ► Application Web : 
        * http://localhost:8080/

    ► Phpmyadmin :
        * http://localhost:8181/


### Identifiants MySQL

➔ Une base de données MySQL avec le name que vous aurez saisie est configurée que vous pouvez utiliser dans votre application :

* MYSQL_ROOT_PASSWORD: `password`
* MYSQL_DATABASE: `name_bdd_projet`
* MYSQL_USER: `user`
* MYSQL_PASSWORD: `password`

➔ Un dump peut être placé dans le repertoire `docker/db/dump` pour la restore lorsque vous lancerez la création du conteneur. 

➔ Connexion bdd
```
mysql -u user -p name_db 
```
➔ Import bdd
```
mysql -u user -p name_db < chemin ou se trouve le backup
```


### Structure Dossier
```
- /docker # Repertoire parents
    - /docker/db/dump # Contient un dump de la config de la db
    - /docker/db/bdd  # Contient la base de donnée
    - /docker/php # Contient le dockerfile
    - /docker/php/config # Contient le php.ini
    - /docker/php/vhosts # Contient le vhost.conf pour la config apache
- /docker-compose.yml # Orchestrer vos conteneurs
```
# Installez Xdebug 3 dans le conteneur PHP
➔ [Procédure Xdebug ](README_xdebug.md)

# Cmd Docker
➔ https://labo-tech.fr/base-de-connaissance/quelles-sont-les-commandes-de-base-de-docker/

➔ https://wiki.maxcorp.org/docker-les-commandes-utiles/
