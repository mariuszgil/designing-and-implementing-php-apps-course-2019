# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Students

### Wprowadzenie

Uczelnia przygotowuje nowy system obsługi rekrutacji kandydatów na studia. Obsługiwać on będzie jednocześnie wszystkie wydziały, które mogą mieć jednak odmienne polityki rekrutacyjne. Przykładowo:

- Wydział A:
    - Kolejność na liście wyznaczana jest przez datę zgłoszenia
    - Wydział przygotowuje 3 listy:
        - Główną listę 100 kandydatów, których zgłoszenia wpłynęły jako pierwsze
        - Rezerwową listę 10 kandydatów, których zgłoszenia wpłynęły jako kolejne
        - Odrzuconą listę pozostałych kandydatów
    - Kolejność na opublikowanych listach również jest wyznaczana przez datę zgłoszeń, od najstarszych do najnowszych
- Wydział B:
    - Kolejność na liście wyznaczana jest przez ilość uzyskanych punktów podczas procesu rekutacji
    - Wydział przygotowuje 2 listy:
        - Główną listę 75 kandydatów, którzy uzyskali największą listę punktów
        - Odrzuconą listę pozostałych kandydatów
    - Kolejność na opublikowanej liście przyjętych kandydatów jest wyznaczana przez ilość uzyskanych punktów, od największej do najmniejszej
    - Kolejność na opublikowanej liście odrzuconych kandydatów jest wyznaczana alfabetycznie względem nazwisk kandydatów, od A do Z
- Wydział C:
    - Z powodów historycznych wydział nie przeprowadza standardowej rekrutacji, ale losuje kandydatów z puli zgłoszeń 
    - Wydział przygotowuje 2 listy:
        - Główną listę 50 kandydatów, którzy zostali wylosowani 
        - Rezerwową listę 5 kandydatów, którzy również zostali wylosowani
        - Odrzuconą listę pozostałych kandydatów
    - Kolejność na obu listach kandydatów jest wyznaczana alfabetycznie względem nazwisk kandydatów, od A do Z 
        

### Zadanie

Z powyższych wymagań wynika, że istnieją tu 2 funkcjonalności, tj. podział puli wszystkich zgłoszeń na listy oraz ustalanie kolejności na listach. Każda z funkcjonalności ma kilka wariantów, np. podział na 2 lub 3 listy, kolejność alfabetyczną, względem punktów, względem czasu, losową...

- Zdefiniuj interfejsy dla obu funkcjonalności
- Poszczególne warianty zaimplementuj w postaci osobnych klas
- Napisz program demonstrujący działanie zaimplementowanego modelu, prezentujący działanie dla poszczególnych wydziałów. Dane wejściowe mogą być przygotowane wewnątrz skryptu demonstracyjnego, nie muszą być odczytywane z parametrów skryptu

Możesz wykorzystać poniższe implementacje wybranych klas jako punkt startowy:

```php
class Student
{
    /**
     * @var string
     */
    private $firstName;
    
    /**
     * @var string
     */
    private $lastName;
    
    // Konstruktor...
    
    public function getFirstName(): string
    {
        return $this->firstName;
    }
    
    public function getLastName(): string
    {
        return $this->lastName;
    }
}

class Application
{
    /**
     * @var Student
     */
    private $student;
     
    /**
     * @var DateTimeImmutable
     */
    private $submissionDate;
    
    // Konstruktor...
     
    /**
     * @var int
     */
    private $points;
     
    public function getStudent(): Student
    {
       return $this->student;
    }
     
    public function getSubmissionDate(): DateTimeImmutable
    {
       return $this->submissionDate;
    }
     
    public function getPoints(): int
    {
        return $this->points;
    }
}
```


### Dodatkowe wymagania

- Każdy z zaimplementowanych elementów, tj. interfejsów, klas, traitów (jeśli istnieją) powinny zostać umieszczone w osobnym pliku, zgodnie z rekomendacją PSR-4
    - Zaproponuj odpowiednią strukturę namespace'ów
- Staraj się postępować zgodnie z zasadami SOLID
- Program demonstracyjny powinien wykorzystać mechanizmy Composera do ładowania poszczególnych klas i interfejsów


### Uwagi

Program demonstracyjny będzie uruchamiany z lini poleceń.

Problemem polskich znaków nie należy się przejmować.