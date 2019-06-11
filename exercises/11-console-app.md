# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Symfony Console

Podczas wcześniejszych ćwiczeń w tym semestrze aplikacje uruchamiane z poziomu linii poleceń wykorzystywały wbudowane w PHP mechanizmy zmiennych `$argc` oraz `$argv`, za pomocą których pobierane były parametry potrzebne do uruchomienia.

Aplikacje konsolowe można także implementować w inny sposób, z wykorzystaniem dostępnych komponentów np. z ekosystemu Symfony. Symfony Console (https://symfony.com/doc/current/components/console.html) pozwala na implementację rozbudowanych aplikacji CLI, dodatkowo integrując się z innymi elementami ekosystemu, takimi jak np. kontener Dependency Injection.

Przykładowy kod:

```php
<?php
// application.php

require __DIR__.'/vendor/autoload.php';

use Symfony\Component\Console\Application;
use Symfony\Component\Console\Command\Command;

class FooCommand extends Command { 
    // ...
}

$application = new Application();

// ... register commands
$application->add(new FooCommand());
$application->run();
```

Uruchomienie:

```php
php application.php 
```

### Zadanie

Bazując na twojej implementacji zadania [Cipher](./01-cipher.md) lub [Numbers](./02-numbers.md), uruchom je w formie aplikacji konsolowej z użyciem Symfony Console. 

Przygotuj skrypt `application.php` rejestrujący komendę uruchamiającą kod twojego zadania oraz samą komendę, uwzględniając jej parametry wywołań.

Zapoznaj się z komunikatami generowanymi przez twoją aplikację przed i po zarejestrowaniu komendy.

### Dodatkowe informacje

Dokumentację do komponentu Symfony Console można znaleźć tu:

- https://symfony.com/doc/current/components/console.html
- https://symfony.com/doc/current/console.html