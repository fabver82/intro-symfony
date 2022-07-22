## Login system

We have a login form to handle, so let's create our user model and make that thing work.
Because we are lazy, we will let symfony do it for us.

Checkout the doc about it and follow the steps : [https://symfony.com/doc/current/security.html#the-user](https://symfony.com/doc/current/security.html#the-user)

- delete the previous operations in the db to avoid conflict.
- create user entity via CLI (I will choose username instead of email for login)
- our operations need to refer to a user. So we will add a property to the operation model.

```
php bin/console make:entity Operation
```

- add a new property called "user" and tell symfony that it is a relation ( not an integer). Follow the steps

- make migration and migrate to database

At this point, you just create a new table in your DB and a model (check it out in src/entity and src/repository), but we don't have any user yet.

Let's create one by using fixtures : a bundle that will help us create "fake datas" in our DB.(without having to do it manually via phpmyadmin )
[https://symfony.com/bundles/DoctrineFixturesBundle/current/index.html](https://symfony.com/bundles/DoctrineFixturesBundle/current/index.html)

Intall it by typing :

```
composer require --dev orm-fixtures
```

Then, follow the doc :

- Create a user in src/DataFixtures/AppFixtures
- Remember to hash your password. checkout this [link](https://symfony.com/doc/current/security/passwords.html)
- then finally load the datas via the fixtures bundle

```
php bin/console doctrine:fixtures:load
```

Now we have a user in our database. Let's setup the login form:

- Enable form_login into security.yaml as explained [here](https://symfony.com/doc/current/security.html#form-login)
- Edit the HomeController and View
- test it and check if you are log in with debug bar.

BONUS : add the logout function !

"But hey ? nothing else is happening ? "
Of course ! We need to tell symfony what to show/ not show when a user is logged.

Modify the twig files so that the login form disapear when user is logged in, and that the content doesn't shows up if nobody is logged.

- TIPS : look for "is_granted" and "path" method in Twig
