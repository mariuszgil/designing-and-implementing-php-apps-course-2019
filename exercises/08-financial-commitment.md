# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Financial Commitment

### Wprowadzenie

Podczas krótkiej sesji EventStormingu odkryliśmy w domenie obiekt zobowiązania finansowego użytkownika, o następującej charakterystyce:

- Zobowiązanie zostaje utworzone ze wskazaniem czytelnika i odpowiedniej kwoty
- Zobowiązanie może zostać spłacone częściowo
- Zobowiązanie może zostać spłacone całościowo
- Zobowiązanie może zostać nadpłacone
- Zobowiązanie może zostać umorzone/anulowane

### Zadanie

Bazując na następujących szkieletach klas i interfejsów:

```php
abstract class Event
{
    /**
     * @var UuidInterface
     */
    private $id;
    
    /**
     * @var DateTimeImmutable
     */
    private $created;
    
    // ...
}

class FinancialCommitmentCreated extends Event
{
    // ... inne pola
}

class FinancialCommitment
{
    /**
     * @var UuidInterface
     */
    private $id;

    /**
     * @var Event[]
     */
    private $events = [];
    
    /**
     * @var Money
     */
    private $balance;
    
    // ... inne pola
    
    public function __construct(Money $amount): self
    {
        $this->id = ...
        $this->balance = $amount;
        $this->events[] = new FinancialCommitmentCreated($amount);         
    }
    
    public function registerPayment(Money $payment): void
    {
        // ...
    
        $this->events[] = new FinancialCommitmentPartiallyPaid($amount); // W zależności od stanu obiektu, należy zarejestrować także inne zdarzenia związane z zarejestrowaniem wpłaty
    }
     
    public function cancel(): void
    {
        // ...
    
        $this->events[] = ...
    }
    
    public function getBalance(): Money
    {
        // ...
    }
    
    public function getEvents(): array
    {
        // ...
    }
    
    public function getId(): UuidInterface
    {
        // ...
    }
}

interface FinancialCommitmentRepository
{
    public function load(UuidInterface $id): FinancialCommitment;
    
    public function save(FinancialCommitment $commitment): void
}

class InMemoryRepository implements FinancialCommitmentRepository
{
    /**
     * @var FinancialCommitment[]
     */ 
    private $commitments = [];
    
    public function load(UuidInterface $id): FinancialCommitment
    {
        // ...
    }
    
    public function save(FinancialCommitment $commitment): void
    {
        $this->commitments[$commitment->getId()->toString()] = $commitment;
    }
}
```

- Zaimplementuj poszczególne metody tak, aby generowane były odpowiednie zdarzenia we właściwym momencie
- Uwzględnij sytuacje brzegowe i zabezpiecz obiekt przed wprowadzeniem go w niewłaściwy stan. Przykładowo:
    - Nie można spłacać spłaconego zobowiązania
    - Nie można umorzyć spłaconego zobowiązania
    - Nie można umorzyć umorzonego zobowiązania
- Przygotuj program demonstracyjny, przedstawiający interakcje pomiędzy zaimplementowanymi elementami oraz przykładową ścieżkę użycia

Podczas implementacji należy wykorzystać następujące biblioteki:

- [ramsey/uuid](https://github.com/ramsey/uuid), do generowania identyfikatorów (ID) zobowiązań i zdarzeń
- [moneyphp/money](https://github.com/moneyphp/money), do opisania kwot zobowiązań i wysokości spłat


### Do zastanowienia

Jakie zmiany w strukturze/zachowaniu poszczególnych obiektów można wprowadzić, aby repozytorium pozwalało na odtworzenie stanu obiektu z historii zarejestrowanych zdarzeń (np. serializowanych jedno po drugim na dysk lub bazy danych)?