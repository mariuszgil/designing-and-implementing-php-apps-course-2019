# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Commands + Events

### Wprowadzenie

Zadanie to składa się z dwóch części, niezależnie punktowanych po 10 pkt każda. 

- [Zadanie 7, Command Bus](../exercises/07-command-bus.md)
- [Zadanie 8, Financial Commitment](../exercises/08-financial-commitment.md)
- Rozszerzenie (dodatkowe 5 pkt)
    - Z wykorzystaniem własnej implementacji command-busa, zaimplementować commandy i handlery dla obsługi akcji opisanych w zadaniu 8, tj.
        - Utworzenia zobowiązania finansowe
        - Spłaty we wskazanej wysokości
        - Umorzenia

Zalecam implementację obu części i zastanowienie się, w jaki sposób taka implementacja może wspierać komunikację asynchroniczną, np. w architekturze mikroserwisowej (z wykorzystaniem systemów typu [RabbitMQ](https://www.rabbitmq.com) jako część implementacji command busa).

Oba zadania wpisują się w koncept opisany w artykule ["DDD, Hexagonal, Onion, Clean, CQRS, … How I put it all together"](https://herbertograca.com/2017/11/16/explicit-architecture-01-ddd-hexagonal-onion-clean-cqrs-how-i-put-it-all-together/) Herberto Graca.