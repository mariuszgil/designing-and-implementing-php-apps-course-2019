# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Wykład 10: Bazy danych

### Zakres:

- PHP Data Objects
    - Nawiązywanie połączenia
        - Struktura DSN
        - Wyjątki
    - Zapis danych
    - Odczyt danych
        - Mapowanie na tablicę
        - Mapowanie na obiekt
    - Prepare Statements 
    - Wymagane moduły
        - PDO
        - pdo_mysql
        - pdo_pgsql
        - pdo_sqlite
        - ...
  - Zarządzanie zmianami w schemacie bazy danych
      - Ewolucja bazy danych powinna podlegać śledzeniu, np. w repozytorium kodu
      - Rozwiązania
          - Doctrine Migrations
          - PHINX
          - Liquibase
              - Rozwiązanie niezależne od technologii wykorzystywanej w projekcie
  - Mapowanie relacyjno obiektowe
      - ORM pozwala przyśpieszy pracę nad systemem, poprzez wprowadzenie warstw abstrakcji ponad bazą danych
      - ORM pozwala zbudować mapowanie pomiędzy strukturą obiektu i grafu jego właściwości na tabelę (lub zestaw tabel) znajdujących się w bazie danych
      - ORM często optymalizuje komunikację zapisu z użyciem wzorca Unit of Work, starając się wyliczyć changeset zmiany i zbudować mininalne zapytanie SQL
      - Wybrane annotacje Doctrine
          - @Entity
          - @Table
          - @Id
          - @Column
          - @ManyToOne
          - @OneToMany
      - Przykładowe problemy wynikające z zastosowania ORM
          - Wydajność na warstwie odczytu
          - Jednoczesne operacje na tym samym obikecie w różnych częściach aplikacji i wprowadzenie obiektu w niepoprawny stan po obu zapisach
          - Brak domyślnego wsparcia dla wersjonowania obiektów
      - Rozdzielanie konfiguracji infrastrukturalnych od pozostałej części aplikacji
          - Mapowanie obiektu na tabele zawsze warto umieścić w części infrastrukturalnej projektu
      - Rozwiązania
          - Doctrine ORM
          - Propel ORM
      

### Przykładowe programy

#### Nawiązywanie połączenia z użyciem PDO

```php
$dsn = 'mysql:dbname=testdb;host=127.0.0.1';
$user = 'dbuser';
$password = 'dbpass';

try {
    $dbh = new PDO($dsn, $user, $password);
} catch (PDOException $e) {
    echo 'Connection failed: ' . $e->getMessage();
}
```

#### Komunikacja z bazą danych

```php
$sth = $dbh->prepare("SELECT name, colour FROM fruit");

$sth->execute();

$result = $sth->fetchAll();
```

```php
$calories = 150;
$colour = 'gre';

$sth = $dbh->prepare('
    SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour LIKE :colour
');

$sth->bindParam(':calories', $calories, PDO::PARAM_INT);
$sth->bindValue(':colour', "%{$colour}%");
$sth->execute();
```

#### Migracja Doctrine Migrations

```php
declare(strict_types=1);

namespace MyProject\Migrations;

use Doctrine\DBAL\Schema\Schema;
use Doctrine\Migrations\AbstractMigration;

/**
 * Auto-generated Migration: Please modify to your needs!
 */
final class Version20180601193057 extends AbstractMigration
{
    public function getDescription() : string
    {
        return '';
    }

    public function up(Schema $schema) : void
    {
        // kod wprowadzający zmianę w strukturze
    }

    public function down(Schema $schema) : void
    {
        // kod usuwający zmianę w strukturze
    }
}
```

#### Przykładowe encje Doctrine

```php
// src/Bug.php
/**
 * @Entity @Table(name="bugs")
 **/
class Bug
{
    /**
     * @Id @Column(type="integer") @GeneratedValue
     **/
    protected $id;
    /**
     * @Column(type="string")
     **/
    protected $description;
    /**
     * @Column(type="datetime")
     **/
    protected $created;
    /**
     * @Column(type="string")
     **/
    protected $status;

    /**
     * @ManyToOne(targetEntity="User", inversedBy="assignedBugs")
     **/
    protected $engineer;

    /**
     * @ManyToOne(targetEntity="User", inversedBy="reportedBugs")
     **/
    protected $reporter;

    /**
     * @ManyToMany(targetEntity="Product")
     **/
    protected $products;

    // ... (other code)
}

// src/User.php
/**
 * @Entity @Table(name="users")
 **/
class User
{
    /**
     * @Id @GeneratedValue @Column(type="integer")
     * @var int
     **/
    protected $id;

    /**
     * @Column(type="string")
     * @var string
     **/
    protected $name;

    /**
     * @OneToMany(targetEntity="Bug", mappedBy="reporter")
     * @var Bug[] An ArrayCollection of Bug objects.
     **/
    protected $reportedBugs = null;

    /**
     * @OneToMany(targetEntity="Bug", mappedBy="engineer")
     * @var Bug[] An ArrayCollection of Bug objects.
     **/
    protected $assignedBugs = null;

    // .. (other code)
}
```

Więcej przykładów znajduje się na stronie [Doctrine Getting Started](https://www.doctrine-project.org/projects/doctrine-orm/en/current/tutorials/getting-started.html().