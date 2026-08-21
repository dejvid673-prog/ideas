# ideas

Centralne repozytorium pomysłów 7DEJV.

Celem repozytorium jest zachowanie pomysłów, koncepcji, niedokończonych projektów, wariantów rozwiązań i ustaleń z rozmów w formie na tyle szczegółowej, aby można było wrócić do nich po tygodniach lub miesiącach bez ponownego odtwarzania całego kontekstu.

Repozytorium nie jest listą haseł ani backlogiem z jednym zdaniem na pomysł. Każdy zapis ma być możliwie kompletną kartą wiedzy o danym pomyśle.

## Główna zasada

**Każdy pomysł otrzymuje osobny folder.**

Folder powinien zawierać możliwie dużo kontekstu, ustaleń, alternatyw, ograniczeń, źródeł i informacji technicznych. Pomysł ma być opisany tak, aby inny agent lub człowiek mógł zrozumieć go bez dostępu do pierwotnej rozmowy.

Przykładowa struktura:

```text
ideas/
├── README.md
├── order-command-center/
│   ├── README.md
│   ├── conversation.md
│   ├── decisions.md
│   ├── architecture.md
│   ├── research.md
│   └── assets/
├── packing-workstation/
│   └── ...
└── another-idea/
    └── ...
```

Nie każdy pomysł musi od razu posiadać wszystkie pliki. Minimalnie powinien mieć własny folder i szczegółowy `README.md`. Dodatkowe pliki należy tworzyć wtedy, gdy poprawiają czytelność lub zapobiegają powstaniu jednego ogromnego dokumentu.

## Standard opisu pomysłu

README pomysłu powinien, jeśli dane są dostępne, zawierać następujące sekcje.

### 1. Nazwa i krótki opis

Jednoznaczna nazwa oraz krótkie wyjaśnienie, czego dotyczy pomysł.

### 2. Problem

Dokładny opis problemu, który pomysł ma rozwiązać.

Należy opisać:

- obecny sposób działania,
- co jest niewygodne, wolne, kosztowne lub błędogenne,
- kto doświadcza problemu,
- jak często problem występuje,
- jakie są skutki pozostawienia problemu bez rozwiązania.

### 3. Cel

Co dokładnie chcemy osiągnąć.

Cel powinien być opisany funkcjonalnie, a nie tylko technologicznie.

Przykład:

Zamiast:

> napisać aplikację w React

lepiej:

> umożliwić pracownikowi obsługę zamówień Allegro, ERLI i PrestaShop w jednym interfejsie, z aktualnymi statusami i bez ręcznego przechodzenia pomiędzy trzema panelami.

### 4. Kontekst

Wszystkie informacje potrzebne do zrozumienia pomysłu:

- proces biznesowy,
- środowisko pracy,
- używane systemy,
- istniejące ograniczenia,
- wcześniejsze rozwiązania,
- powiązane projekty,
- istotne decyzje historyczne.

### 5. Ustalenia z rozmów

Należy zapisywać wszystkie istotne wnioski wypracowane w rozmowach, także te, które nie zostały jeszcze wdrożone.

Ważne jest rozróżnienie:

- faktu,
- założenia,
- hipotezy,
- propozycji,
- decyzji,
- rozwiązania odrzuconego,
- elementu wymagającego weryfikacji.

Nie wolno przedstawiać hipotezy jako zatwierdzonej decyzji.

### 6. Proponowane rozwiązanie

Szczegółowy opis aktualnie preferowanego wariantu.

Jeżeli dotyczy systemu technicznego, należy opisać m.in.:

- architekturę,
- komponenty,
- przepływ danych,
- źródła prawdy,
- integracje,
- sposób autoryzacji,
- synchronizację,
- obsługę błędów,
- bezpieczeństwo,
- wymagania sprzętowe,
- zależności zewnętrzne.

### 7. Alternatywne rozwiązania

Nie usuwać wariantów tylko dlatego, że nie zostały wybrane.

Dla każdej sensownej alternatywy opisać:

- jak działa,
- zalety,
- wady,
- koszty,
- ograniczenia,
- kiedy mogłaby być lepsza od wariantu preferowanego.

### 8. Integracje

Dla każdego systemu zewnętrznego opisać osobno:

- co chcemy odczytywać,
- co chcemy zapisywać,
- czy dostępne jest oficjalne API,
- czy dostępne są webhooki/eventy,
- czy potrzebny jest polling,
- mechanizm autoryzacji,
- limity,
- ryzyka,
- link do dokumentacji.

Dla integracji, które nie zostały jeszcze sprawdzone, oznaczyć stan jako `DO WERYFIKACJI`.

### 9. Dane i źródło prawdy

Jeżeli pomysł obejmuje dane, należy określić:

- skąd pochodzą,
- gdzie są przechowywane,
- który system jest źródłem prawdy,
- kto może je zmieniać,
- jak działa synchronizacja,
- jak rozwiązywane są konflikty.

### 10. Interfejs i UX

Jeżeli pomysł obejmuje interfejs, zapisać:

- typ użytkownika,
- główne zadania,
- najczęstsze akcje,
- priorytety informacji,
- strukturę nawigacji,
- kluczowe widoki,
- stany błędów,
- stany puste,
- wymagania desktop/mobile/multi-monitor,
- ustalone zasady wizualne.

Jeżeli istnieją grafiki referencyjne lub mockupy, umieścić je w `assets/` i opisać, co dokładnie z nich wynika.

### 11. Automatyzacje i agenci

Jeżeli pomysł ma wykorzystywać automatyzacje lub agentów AI, opisać:

- jakie zdarzenia uruchamiają działanie,
- jakie dane agent otrzymuje,
- co może wykonać automatycznie,
- co wymaga zatwierdzenia człowieka,
- jakie ma uprawnienia,
- jakie są ograniczenia bezpieczeństwa,
- jakie logi i audyt działania są wymagane.

Preferowane jest projektowanie agentów wokół zdarzeń systemowych, a nie tworzenie agentów bez jasno określonej odpowiedzialności.

### 12. Sprzęt lokalny

Jeżeli pomysł współpracuje ze sprzętem, opisać np.:

- drukarki,
- wagi USB/RS-232,
- skanery,
- terminale,
- komputery stanowiskowe,
- lokalne agenty/bridge,
- protokoły komunikacyjne,
- zachowanie po utracie połączenia.

### 13. Koszty

Należy oddzielić:

- koszt prototypu,
- koszt wdrożenia,
- koszt miesięczny,
- koszt sprzętu,
- koszt usług zewnętrznych,
- potencjalny koszt utrzymania.

Jeżeli wartość jest szacunkiem, należy ją tak oznaczyć.

### 14. Ryzyka i ograniczenia

Zapisywać zarówno ryzyka techniczne, jak i biznesowe, m.in.:

- zależność od API zewnętrznego,
- limity usług,
- błędy synchronizacji,
- utratę połączenia,
- bezpieczeństwo,
- błędy użytkownika,
- vendor lock-in,
- koszty skalowania,
- utrzymanie.

### 15. MVP / wersja minimalna

Określić najmniejszy zakres, który pozwala sprawdzić, czy pomysł rzeczywiście ma wartość.

Nie należy automatycznie projektować pełnego systemu, jeżeli można najpierw zweryfikować główną hipotezę tańszą wersją.

### 16. Wersja docelowa

Osobno opisać kierunek rozwoju po potwierdzeniu MVP.

### 17. Etapy realizacji

Preferowany format:

```text
Etap 0 — research / feasibility
Etap 1 — prototyp
Etap 2 — MVP
Etap 3 — test operacyjny
Etap 4 — integracje produkcyjne
Etap 5 — automatyzacja
Etap 6 — skalowanie
```

Etapy należy dostosować do konkretnego pomysłu.

### 18. Kryteria akceptacji

Pomysł powinien posiadać mierzalne warunki uznania danego etapu za zakończony.

Przykład:

- zamówienie z ERLI pojawia się w systemie bez ręcznego importu,
- zmiana statusu jest widoczna na drugim stanowisku bez odświeżania strony,
- ponowny druk etykiety nie tworzy drugi raz przesyłki,
- błąd API jest zapisany w logach i widoczny dla operatora.

### 19. Testy

Zapisać plan testów:

- happy path,
- błędy API,
- utrata internetu,
- duplikaty,
- równoczesne zmiany,
- błędne dane,
- uprawnienia,
- awaria urządzenia lokalnego.

### 20. Otwarte pytania

Wszystkie kwestie, które nadal wymagają decyzji lub researchu.

### 21. Powiązania z innymi pomysłami

To jedna z najważniejszych części repozytorium.

Dla każdego pomysłu należy wskazać możliwe połączenia z innymi folderami.

Przykład:

```text
Powiązane:
- ../order-command-center/
- ../packing-workstation/
- ../local-device-agent/
```

Opisać również **na czym polega powiązanie**, np. wspólny backend, ten sam agent lokalny, wspólny model zdarzeń, ten sam UI kit.

### 22. Możliwe elementy wielokrotnego użytku

Wskazać elementy, które mogą zostać wykorzystane w innych pomysłach:

- komponent UI,
- API client,
- moduł PrestaShop,
- lokalny agent,
- system zdarzeń,
- adapter przewoźnika,
- skill,
- prompt,
- workflow,
- schema bazy danych.

To ma ułatwiać łączenie pomysłów i unikać budowania tego samego kilka razy.

### 23. Źródła i linki

Zapisywać linki do:

- oficjalnej dokumentacji,
- API,
- norm,
- repozytoriów,
- artykułów technicznych,
- badań,
- produktów sprzętowych,
- materiałów referencyjnych.

Przy każdym linku warto dopisać, **po co został zapisany**.

Nie dodawać linków bez znaczenia tylko po to, aby dokument wyglądał na bardziej kompletny.

### 24. Historia decyzji

Jeżeli koncepcja ewoluuje, nie nadpisywać bez śladu wcześniejszych ważnych decyzji.

Zapisywać:

- co zmieniono,
- dlaczego,
- kiedy,
- co zostało odrzucone.

Dla większych pomysłów można prowadzić osobny `decisions.md`.

## Zapis rozmów

Jeżeli jest to możliwe, folder pomysłu powinien zawierać `conversation.md`.

Celem nie jest wyłącznie archiwizacja tekstu rozmowy. Zapis ma zachować **tok rozwoju pomysłu**.

Preferowana kolejność:

1. pełny transcript rozmowy, jeżeli jest technicznie dostępny i można go bezpiecznie zapisać,
2. jeżeli pełny transcript nie jest dostępny — szczegółowa rekonstrukcja rozmowy,
3. dodatkowo krótka sekcja z najważniejszymi ustaleniami i decyzjami.

`conversation.md` powinien w miarę możliwości zawierać:

```text
# Conversation

## Kontekst

## Przebieg rozmowy

### Użytkownik
...

### ChatGPT
...

## Najważniejsze ustalenia

## Decyzje

## Odrzucone warianty

## Otwarte pytania
```

Nie wolno wymyślać brakujących wypowiedzi. Jeżeli zapis jest rekonstrukcją, należy to wyraźnie zaznaczyć.

## Status pomysłu

Każdy folder powinien zawierać status, np.:

- `CAPTURED` — zapisany pomysł,
- `RESEARCH` — trwa analiza,
- `DESIGN` — projektowanie rozwiązania,
- `PROTOTYPE` — istnieje prototyp,
- `VALIDATION` — trwa test pomysłu,
- `READY` — gotowy do realizacji,
- `IN_PROGRESS` — realizowany,
- `PAUSED` — świadomie odłożony,
- `MERGED` — połączony z innym pomysłem,
- `REJECTED` — odrzucony,
- `DONE` — zrealizowany.

Status nie oznacza jakości pomysłu. Ma pokazywać etap jego życia.

## Nazewnictwo folderów

Preferowane:

```text
lowercase-kebab-case
```

Przykłady:

```text
order-command-center
packing-workstation
prestashop-product-auditor
local-print-agent
multi-monitor-backoffice
```

Nazwa powinna opisywać ideę, a nie datę rozmowy.

## Data i pochodzenie

W README każdego pomysłu warto zapisać:

```text
Created: YYYY-MM-DD
Last updated: YYYY-MM-DD
Origin: ChatGPT conversation / observation / business problem / research
Status: CAPTURED
```

Jeżeli pomysł pochodzi z kilku rozmów, należy to zaznaczyć.

## Poziom szczegółowości

W tym repozytorium preferujemy **nadmiar użytecznego kontekstu nad zbyt krótkim opisem**.

Nie należy jednak sztucznie rozwlekać treści. Każdy zapis powinien pomagać w co najmniej jednym z poniższych:

- zrozumieniu pomysłu,
- podjęciu decyzji,
- późniejszej implementacji,
- porównaniu wariantów,
- połączeniu z innym pomysłem,
- uniknięciu ponownego researchu,
- przekazaniu pracy innemu agentowi.

## Zasada niedublowania

Przed utworzeniem nowego folderu należy sprawdzić, czy podobny pomysł już istnieje.

Jeżeli istnieje:

- rozszerzyć istniejący folder, albo
- utworzyć osobny folder tylko wtedy, gdy koncepcje są rzeczywiście różne,
- zapisać relację pomiędzy nimi.

Jeżeli dwa pomysły z czasem stają się jednym systemem, nie należy usuwać historii. Można oznaczyć jeden jako `MERGED` i wskazać nowy nadrzędny projekt.

## Repozytorium nie jest źródłem prawdy dla gotowego kodu

`ideas` przechowuje koncepcje, wiedzę, decyzje i research.

Gdy pomysł przechodzi do właściwej implementacji, kod powinien trafić do odpowiedniego repozytorium projektowego. Folder w `ideas` nadal pozostaje miejscem opisującym genezę, założenia, warianty i decyzje.

W folderze pomysłu należy wtedy dodać link do repozytorium wykonawczego.

## Bezpieczeństwo

Nigdy nie zapisywać w repozytorium:

- haseł,
- tokenów,
- kluczy API,
- sekretów OAuth,
- danych klientów,
- prywatnych danych dostępowych,
- plików `.env` zawierających sekrety.

Można opisywać nazwy wymaganych sekretów, np.:

```text
ERLI_API_TOKEN
ALLEGRO_CLIENT_ID
PRESTASHOP_API_KEY
```

ale bez ich wartości.

## Cel długoterminowy

Repozytorium ma z czasem stworzyć mapę pomysłów 7DEJV, dzięki której można:

- wracać do niedokończonych koncepcji,
- łączyć kilka pomysłów w większy system,
- identyfikować wspólne komponenty,
- wykorzystywać wcześniejszy research,
- unikać powtarzania tych samych rozmów,
- przekazywać kontekst agentom wykonawczym,
- oceniać, które pomysły dojrzały do wdrożenia.

**Pomysł zapisany w tym repozytorium powinien być użyteczny nawet wtedy, gdy osoba czytająca nie pamięta już pierwotnej rozmowy.**
