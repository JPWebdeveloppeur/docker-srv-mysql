# Remise en route d'un projet sous instance docker :

➔ Recuperer :

```
https://github.com/JPWebdeveloppeur/docker-environnement-srv-mysql.git
```

➔ Dans le .env de votre projet SF4 saisir :
    
```
DATABASE_NOSSE_URL=mysql://user:passwordnosse@name_instance_bdd:3306/name_database
```

Ici le name_instance_bdd c'est l'instance de votre container_name de votre docker-compose ex:db_docker

➔ lancer une l'invite de commande et sur votre hote docker :
	
```
cd /var/www (accede au projet sur votre hote)
```
```
php bin/console doctrine:database:create (lance la création de votre bdd)
```

➔ Lorsque nous sommes sur une remise en route les entity sont en principe déja créer donc ils vous reste juste à saisir
```
php bin/console make:migration
```
puis 
```
php bin/console doctrine:migrations:migrate
```
➔ Si vous avez des fixtures d'exemple vous pouvez saisir :
```
php bin/console doctrine:fixtures:load
```
