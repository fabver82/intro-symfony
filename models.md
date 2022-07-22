## create our model

We will need a table that hold all operations made by the user. So the first step is to create an entity. Symofny will make it easy for us. just type:

```
php bin/console make:entity Operation
```

follow the steps by adding a few properties :

- amount
- Subject
- type (of operation => income or expense)
- createAt

Our model has just been create in src/entity.
But our database is still empty

Symfony recommend you to create a migration and then to migrate. This operation will first create a migration file that you can re-use later if you need to setup your database and models, then it will also create a table in our database. Try and check in phpmyadmin.

```
php bin/console make:migration
```

Got an error ? check your .env file.

```
php bin/console doctrine:migrations:migrate:migrate
```

Add some data in your table via phpmyadmin or...wait a minute...

## let's CRUD the model

```
php bin/console make:crud Operation
```

And check out the new files.

## BONUS : fixtures

If you are brave enought, you could use the fixtureBundle along with "faker". That way, you can ask symfony to create some fake datas for you.

[https://symfony.com/bundles/DoctrineFixturesBundle/current/index.html](https://symfony.com/bundles/DoctrineFixturesBundle/current/index.html)

Now let's show our data in our homepage, [follow me](populatetemplate.md)
