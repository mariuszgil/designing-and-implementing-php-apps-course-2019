# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Wykład 2: Obiektowość w języku PHP

### Zakres:

- Rys historyczny w kontekście:
    - PHP 4
    - PHP 5
    - PHP 7
- Obiektowość (część I)
    - Klasy i obiekty
    - Właściwości, properties
    - Metody, zachowania klas
    - Modyfikatory widoczności
        - private
        - protected
        - public
    - Konstruktory i destruktory
        - Konstruktor jest wywoływany w momencie instancjonowania obiektu
        - Destruktor jest wywoływany w momencie niszcenia instancji obiektu
    - Dziedziczenie i polimorfizm
    - Przeciążanie metod
    - Klasy i metody abstrakcyjne
        - Klasy, których nie można zinstancjonować, ze względu na brak implementacji metod
    - Klasy finalne
        - Klasy, których nie można rozszerzyć
    - Deklaracja typów argumentów metody
    - Deklaracja typu zwracanego przez metodę
    - Słowo kluczowe $this
    - Interfejsy
        - Definicja kontraktu do implementacji
        - Interfejs zawiera tylko deklaracje metod, bez implementacji
- Object-oriented Design
    - Reguły SOLID (wstęp)
        - Single Responsiblity Principles
            - Zasada pojedynczej odpowiedzialności
            - "The single responsibility principle is a computer programming principle that states that every module or class should have responsibility over a single part of the functionality provided by the software, and that responsibility should be entirely encapsulated by the class."
            - "A class should have only one reason to change", Robert C. Martin
        - Open-close Principle
        - Liskov Substitution Principle
        - Interface Segregation Principle
        - Dependency Inversion Principle
    - Antyworzec STUPID
        - Singleton
            - Ale nie każdy singleton jest zły z natury...
        - Tight Cohesion
        - Premature Optimization
        - Untestable Code
        - Indescriptive Naming
        - Duplicated Code
            - Czasem lepsza jest duplikacja kodu niż jego zła abstrakcja
    - Reguły GRASP (wstęp)
        - Controller
        - Creator
        - High cohesion
        - Indirection
        - Information Expert
        - Low coupling
        - Polymorphism
        - Protected variations
            - "The protected variations pattern protects elements from the variations on other elements (objects, systems, subsystems) by wrapping the focus of instability with an interface and using polymorphism to create various implementations of this interface."
        - Pure fabrication
     
### Przykładowe programy


```php
interface DataProvider {
    public function getData(array $params): array;
}

abstract class FileDataProvider implements DataProvider { /* ... */ }
final class LocalFileDataProvider extends FileDataProvider { /* ... */ }

class DBDataProvider implements DataProvider { /* ... */ }
class APIDataProvider implements DataProvider { /* ... */ }
class HadoopDataProvider implements DataProvider { /* ... */ }

interface Formatter {
    public function format(array $data): string;
}

class CSVFormatter implements Formatter { /* ... */ }
class ExcelFormatter implements Formatter { /* ... */ }
class JSONFormatter implements Formatter { /* ... */ }

interface Writer {
    public function write(string $data): void;
}

class LocalOutputWriter implements Writer {}

final class ReportingService {
    private $dataProvider;
    private $formatter;
    private $writer;

    /**
     * ReportFlow constructor.
     * @param DataProvider $dataProvider
     * @param Formatter $formatter
     * @param Writer $writer
     */
    public function __construct(
        DataProvider $dataProvider,
        Formatter $formatter,
        Writer $writer)
    {
        $this->dataProvider = $dataProvider;
        $this->formatter = $formatter;
        $this->writer = $writer;
    }

    public function run(array $arguments): void
    {
        $this->writer->write(
            $this->formatter->format(
                $this->dataProvider->getData($arguments)
            )
        );
    }
}

$service = new ReportingService(
    new APIDataProvider(),
    new CSVFormatter(),
    new LocalOutputWriter()
);

$service = new ReportingService(
    new HadoopDataProvider(),
    new ExcelFormatter(),
    new LocalOutputWriter()
);
```

### Materiały uzupełniające

- [Obiektość w PHP, dokumentacja](http://php.net/manual/en/language.oop5.php)
- [Video, Robert C. Martin "Uncle Bob", SOLID Principles of Object Oriented and Agile Design](https://www.youtube.com/watch?v=TMuno5RZNeE)
- [Principles of Object-oriented Design](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod)


