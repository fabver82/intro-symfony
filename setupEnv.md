## Let's get started !

The first thing to do is to create a symfony project that will contain all the base files. Symfony is a set of packages. Basically, you take the packages that you need but here we will install the most common packages needed for a webapp.

You should run the following command:

```
symfony new my_project_directory --webapp
```

Let's check if everything is working well: symfony has his own local server.
type:

```
symfony serve -d
```

it will start the local server and you should now see a "welcome to Symfony" page.

stop the local server by typing:

```
symfony server:stop
```

check out the documentation if you need more informations: [https://symfony.com/doc/current/setup.html](https://symfony.com/doc/current/setup.html)

## setup our environnement

Right, we have a local server but we don't have a database. Let symfony take care of that, type:

```
symfony console make:docker:database
```

- choose MySql (0) and defaults value.

You have just setup your docker-compose file for MySql.

IMPORTANT: modify the port to '3306:3306'. If you don't do it, the port will be random everytime you run docker and you will need to edit the .env file often.

For testing puprose, we will ad phpmyadmin to docker
Add the folllowing under 'service'

```
phpmyadmin:
    depends_on:
      - database
    image: phpmyadmin
    restart: always
    ports:
      - 8080:80
    environment:
      PMA_HOST: database
```

Symfony need to know how to connect to your database. You need to modify it into the .env file :

- comment the postgresql line if it still here
- uncomment the one for mysql.
- Edit it with the db name and password to you setup.
- run docker compose up -d

Everything ok ?
Let's start coding...no I'm kidding, we only need the console.
Follow me [here](controllerAndView.md)
