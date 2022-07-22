## fill our table with datas

If you check the src/Repository/OperationRepository.php, you will find a few method that will help to you retrieve the datas.

We need to import our repository in our controller, then call the method that we need to get the datas.

```
use App\Repository\OperationRepository;

class HomeController extends AbstractController
{
    #[Route('/', name: 'app_home')]
    public function index(OperationRepository $operationRepository): Response
    {
        $operations = $operationRepository->findAll();
        return $this->render('home/index.html.twig', [
            'controller_name' => 'HomeController',
            'operations' => $operations,
        ]);
    }
}
```

Now in our twig file, we will use a for loop

```
{% for operation in operations %}
    <div class="movements__row">
        <div class="movements__type movements__type--{{operation.type}}">{{operation.type}}</div>
        <div class="movements__date">{{operation.createAt|date('Y-m-d')}}</div>
        <div class="movements__subject">{{operation.subject}}</div>
        <div class="movements__value">{{operation.amount}}€</div>
    </div>
{% endfor %}
```

that's it !
But our forms are not working yet. Let's do it [here](forms.md)
