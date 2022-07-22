# Introduction To Symfony Framework

So you want to try Symfony ?! You have made the right choice !
Are you scared about it ? if yes, relax... The most difficult part is to set it up ! You will need a few packages before starting. Make sure you have installed the following dependencies before attending the workshop.

## Prerequisites

- Docker - You should already have an intro about it. I will be using Docker Compose V2.
- [PHP 8 linux](https://linuxhint.com/install-php-8-ubuntu-22-04/) or [PHP 8 windows](https://www.educative.io/answers/how-to-install-php-8-on-windows) MAC? Who is still using this?
- [Composer](https://getcomposer.org/)
- [Symfony CLI](https://symfony.com/download) - It will be useful to quickly create symfony project with the terminal.

## Check Requirements

Now that you have installed all depedencies, let's check if you are ready to start a symfony project. If you had correcly installed Symfony CLI, you should be able to check the requirements with the following command :

```
symfony check:requirements
```

You should read a message with a green background saying : 'Your system is ready to run Symfony projects".

Congratulations !!!

## Our Project

We will create a wallet manager. This app will show all the operations that the user has done. He will be able to check his balance, add incomes, and add expenses.

Now let's get started :

1. [Setup Environnement](setupEnv.md)
2. [Controller and view](controllerAndView.md)
3. [create the operations model](models.md)
4. [show datas in the view](populatetemplate.md)
5. [create the forms](forms.md)
6. [login system](loginsystem.md) => if we have time !
