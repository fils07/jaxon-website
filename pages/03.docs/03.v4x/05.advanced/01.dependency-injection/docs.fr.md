---
title: L'injection de dépendance
menu: L'injection de dépendance
template: jaxon
---

La librairie Jaxon permet d'ajouter des classes ou des interfaces en paramètres des constructeurs des classes Jaxon.

```php
class HelloWorld
{
    protected $service;

    public function __construct(ExampleInterface $service)
    {
        $this->service = $service;
    }
}
```

Les dépendances sont déclarées lors de la configuration de la librairie.

```php
jaxon()->di()->set(ExampleInterface::class, function($di){
    return new Example();
});
```

Elles seront alors instanciées par la librairie en même temps que les classes Jaxon, lors du traitement des requêtes.
