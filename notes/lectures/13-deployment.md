# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Wykład 13: Wdrażanie aplikacji

### Zakres:

- Testowanie wydajnośćiowe i obiążeniowe aplikacji (kontynuacja)
    - Metodyka przeprowadzania testów wydajnościowych
    - Tworzenie stabilnego i odizolowanego środowiska na potrzeby testów
    - Narzędzia
        - Apache Benchmark
        - Siege
        - Tsung
        - JMeter
        - Gatling
    - Generowanie obciążenia punktowego vs odtwarzanie sesji prawdziwych użytkowników
    - Analiza i interpretacja wyników
- Automatyzacja procesów
    - Typowe powody automatyzacji
        - Potrzeba przyśpieszenia wykonywania większej liczby zadań 
        - Chęć uniknięcia błędów przy powtarzalnych czynnościach
    - Przykładowe procesy możliwe do zautomatyzowania
        - Buildowanie aplikacji
        - Tworzenie środowiska developerskiego, testowego, produkcyjnego
        - Deployment aplikacji na serwery
        - Obsługa migracji bazy danych podczas deployment
        - Backupowanie baz danych
        - Usuwanie starszych logów
- Wdrażanie aplikacji
    - Przykładowe środowiska serwerowe
        - Serwery VPS, Virtual Private Server
        - Serwery dedykowane
        - Rozwiązania cloud
            - Amazon Web Services, usługa EC2
        - Konteneryzacja
            - Docker
            - Kubernetes
    - Przykładowe modele deploymentu aplikacji PHP
        - Update aplikacji "w miejscu"
            - git pull
            - Problem z obsługą ruchu użytkowników w momencie przepinania wersji
        - Deployment do osobnego folderu
            - Przypinanie linku symbolicznego do katalogu DOCUMENT ROOT webserwera
            - Wyniesienie plików współdzielonych poza katalog z rewizją aplikacji
                - shared/uploads
                - shared/logs
            - Rozwiązania
                - Capifony
                - Capistrano
        - Środowiska Blue/Green
            - Utworzenie kopii środowiska z nową wersją
            - Przepinanie ruchu na poziomie load-balansera
        - Canary Releases
    - Wersjonowanie assetów aplikacji
        - Powiązannie wersji assetów CSS/JS z rewizją aplikacji na potrzeby odświeżenia cache po stronie klienta
    - Udostępnianie funkcjonalności aplikacji części użytkownikom
        - Feature Flags
  

### Materiały uzupełniające

- [Deployer](https://deployer.org)
- [Feature Toggles, wpis na blogu Martina Fowlera](https://martinfowler.com/articles/feature-toggles.html)
- [FeatureFlags.io, Kompendium wiedzy na temat feature flags](http://featureflags.io)