Let's have a look at how forms can be build and handle in symfony : [https://symfony.com/doc/current/forms.html](https://symfony.com/doc/current/forms.html)

There are many ways. But the most efficient would be to have a dedicated form type. Are you lazy ? I guess!

You could use the maker bundle in order to create this file!

```
php bin/console make:form OperationType
```

and checkout the newly created file.

We actually already have it if you had create a crud, checkout src/form/operationType.php and comment the createAt property and the type property as well. We won't ask the user to enter it.

### render the form and handle the form

In Symfony, It's recommended to render and handle the form in the same controller. So we will create a method for this in our OperationController. Remember to import entity and formtype into your controller.

but actually, we already have it : check out the new method in OperationController. We can definetely use that method !

Then in the main view (that we render from HomeController) we will render the form via our method in OperationController.

in Base or index.html.twig

```
{{ render(controller('App\\Controller\\OperationController::income')) }}
```

we will use the createForm method and we will pass it the view :

```
$incomeForm = $this->createForm(OperationType::class, $operation)->createView();
```

Then we will simply use the form method in twig to render it

```
{{ form(incomeForm) }}

```

But now, our frontender is angry at us...
Check out how we can customize the form rendering [here](https://symfony.com/doc/current/form/form_customization.html)
easy isn't it ?

In the end, it should look like this:
The Controller

```
use Symfony\Component\HttpFoundation\Request;
use Doctrine\Persistence\ManagerRegistry;
use App\Entity\Operation;
use App\Form\OperationType;


class OperationController extends AbstractController
{
    #[Route('/operation/income', name: 'app_operation')]
    public function income(Request $request, ManagerRegistry $doctrine): Response
    {
        $operation = new Operation();
        $operation->setType('in');
        $incomeForm = $this->createForm(OperationType::class, $operation);
        //handle the form submission(
        $incomeForm->handleRequest($request);
        if ($incomeForm->isSubmitted() && $incomeForm->isValid()) {
            $operation->setCreateAt(new \DateTime());
            //post to DB
            $entityManager = $doctrine->getManager();
            $entityManager->persist($operation);
            $entityManager->persist($user);
            $entityManager->flush();
            return $this->redirectToRoute('app_home');
        }
        return $this->renderForm('home/incomeForm.html.twig', [
            'incomeForm' => $incomeForm,
        ]);
    }
```

The View

```
<div class="operation operation--income">
  <h2>Add Income</h2>
  {{ form_start(incomeForm,{'action': path('app_operation'),'method': 'POST','attr': {'class': 'form form--movement'}}) }}
  {{ form_widget(incomeForm.amount,{'attr': {'class': 'form__input form__input--movement-amount'}}) }}
  {{ form_widget(incomeForm.subject,{'attr': {'class': 'form__input' }}) }}
  <button class="form__btn form__btn--movement" type='submit'>&rarr;</button>
  <label class="form__label form__label--movement">Amount</label>
  <label class="form__label">Subject</label>
  {# <form class="form form--movement">
    <input type="number" class="form__input form__input--movement-amount" />
    <input type="text" class="form__input" />
    <button class="form__btn form__btn--movement">&rarr;</button>
    <label class="form__label form__label--movement">Amount</label>
    <label class="form__label">Subject</label>
  </form> #}
  {{ form_end(incomeForm) }}
</div>
```

I am sure that you can to the same for the expense form.

Now we need to handle our users. Folow me [here](loginsystem.md)
