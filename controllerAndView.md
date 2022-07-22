## Our home page

### the controller

Let's create our first page. We need a controller and a view...and we are very lazy!

- create a controller by using the maker bundle :

```
php bin/console make:controller HomeController
```

What just happens ? Symfony create a controller and a view ! Check it out !
Our route is defined right above the index function, yes as a comment! That is working because we already have the "annotations" bundle implemented by default when we create the project for a webapp.
Edit the controller so our homepage link to the root of our website and test it...

Amazing ! Our controller and our view is already working.

Now let's implement the template that I ve share with you in this repository.

### the view

Symfony use Twig as a template engine ( But I guess you could use other template engine like Pug or Blade).
More about it [here](https://symfony.com/doc/current/templates.html)

- Copy the content of our index.html into templates/base.html.twig file and copy all the other file (css and images) into the public folder.
- test it !

We are loading home/index.html.twig which extend the base.html.twig that we just edit.
If we want to add specific data for this page, we need to add "blocks" in the base file, that wil be overwritten in the template that we load for this controller. You can also use partials for header, footer, or anything else.
if we want to add a link to a specific route, we only need to use "path" with the route name in our twig file. Example :

```
{{ path('app_home')}}
```

Your template is ready ? Let's create our model [here](models.md)
