# ideas

Centralne repozytorium pomysłów 7DEJV.

Repozytorium służy do trwałego zachowywania pomysłów, koncepcji, niedokończonych projektów, wariantów rozwiązań, researchu i ustaleń z rozmów w formie na tyle szczegółowej, aby można było wrócić do nich po tygodniach lub miesiącach bez ponownego odtwarzania całego kontekstu.

Repozytorium nie jest listą luźnych haseł ani backlogiem z jednym zdaniem na pomysł. Każdy zapis ma być możliwie kompletną kartą wiedzy o danym pomyśle.

---

# Komenda operacyjna: `Zapisz w pomysłach`

## Znaczenie komendy

Fraza:

```text
Zapisz w pomysłach
```

jest stałą komendą operacyjną odnoszącą się do repozytorium `dejvid673-prog/ideas`.

Po otrzymaniu tej komendy należy potraktować aktualny kontekst rozmowy jako materiał do zapisania lub aktualizacji w repozytorium `ideas`.

Nie należy wymagać dodatkowego polecenia typu „utwórz plik”, „zapisz README”, „zrób commit” itp. Sama komenda `Zapisz w pomysłach` oznacza wykonanie pełnej procedury opisanej poniżej.

## Procedura po komendzie

Po komendzie `Zapisz w pomysłach` należy:

1. Przeanalizować aktualny wątek rozmowy i ustalić, jaki pomysł lub pomysły są jego przedmiotem.
2. Przeszukać repozytorium `ideas`, aby sprawdzić, czy podobny pomysł już istnieje.
3. Jeżeli pomysł istnieje — **zaktualizować istniejący folder**, zamiast automatycznie tworzyć duplikat.
4. Jeżeli pomysł nie istnieje — **utworzyć nowy folder** zgodnie z zasadami nazewnictwa tego repozytorium.
5. Zapisać możliwie pełny kontekst pomysłu, nie tylko ostatnią wiadomość użytkownika.
6. Uzupełnić lub utworzyć `README.md` pomysłu.
7. W razie potrzeby uzupełnić dodatkowe pliki, np. `conversation.md`, `architecture.md`, `research.md`, `decisions.md`, `sources.md`, `todo.md`, `assets/`.
8. Zachować historię wcześniejszych decyzji zamiast nadpisywać ją bez śladu.
9. Zaktualizować **Indeks pomysłów** w głównym `README.md` repozytorium.
10. W indeksie dodać lub zaktualizować krótki opis pomysłu, status i link do folderu.
11. Sprawdzić, czy nowy pomysł ma powiązania z innymi pomysłami już znajdującymi się w repozytorium i zapisać te relacje.
12. Nie zapisywać sekretów, tokenów, haseł, kluczy API ani danych klientów.

## Aktualizacja zamiast duplikacji

Komenda nie oznacza automatycznie „utwórz nowy folder”.

Najpierw należy ustalić, czy aktualna rozmowa:

- tworzy nowy pomysł,
- rozwija istniejący pomysł,
- zmienia wcześniejszą decyzję,
- dodaje nowy wariant rozwiązania,
- dostarcza research,
- dostarcza nowe wymagania,
- łączy dwa lub więcej istniejących pomysłów.

Jeżeli aktualny materiał rozwija istniejący pomysł, należy go dopisać do istniejącej dokumentacji i zaktualizować datę `Last updated`.

Jeżeli dwa pomysły zaczynają tworzyć jeden większy system, nie należy usuwać historii. Należy opisać relację, a w razie potrzeby oznaczyć jeden z pomysłów jako `MERGED` i wskazać pomysł nadrzędny.

## Główny indeks pomysłów

Główny `README.md` pełni również funkcję szybkiej mapy repozytorium.

Każde użycie komendy `Zapisz w pomysłach`, które tworzy lub istotnie aktualizuje pomysł, powinno prowadzić również do aktualizacji indeksu poniżej.

Indeks ma pozwalać po kilku miesiącach szybko ustalić:

- jakie pomysły istnieją,
- czego dotyczą,
- na jakim są etapie,
- które są aktywne,
- które są powiązane,
- gdzie znajduje się pełna dokumentacja.

Preferowany format wpisu:

```text
| Pomysł | Status | Krótki opis | Ostatnia aktualizacja |
|---|---|---|---|
| [order-command-center](./order-command-center/) | DESIGN | Centrum obsługi zamówień i procesów operacyjnych z integracjami marketplace, pakowaniem i agentami. | 2026-08-21 |
```

Krótki opis powinien przekazywać sens pomysłu w 1–3 zdaniach i umożliwiać szybkie odróżnienie go od innych projektów.

---

# Indeks pomysłów

> Ten indeks jest aktualizowany przy użyciu komendy `Zapisz w pomysłach`.

| Pomysł | Status | Krótki opis | Ostatnia aktualizacja |
|---|---|---|---|
| _Brak zapisanych pomysłów w indeksie_ | — | Pierwszy wpis zostanie dodany podczas pierwszego użycia komendy `Zapisz w pomysłach`. | — |

---

# Główna zasada repozytorium

**Każdy odrębny pomysł otrzymuje osobny folder.**

Folder powinien zawierać możliwie dużo użytecznego kontekstu, ustaleń, alternatyw, ograniczeń, źródeł i informacji technicznych. Pomysł ma być opisany tak, aby inny agent lub człowiek mógł zrozumieć go bez dostępu do pierwotnej rozmowy.

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
│   ├── sources.md
│   └── assets/
├── packing-workstation/
│   └── ...
└── another-idea/
    └── ...
```

Nie każdy pomysł musi od razu posiadać wszystkie pliki. Minimalnie powinien mieć własny folder i szczegółowy `README.md`. Dodatkowe pliki należy tworzyć wtedy, gdy poprawiają czytelność lub zapobiegają powstaniu jednego ogromnego dokumentu.

---

# Standard opisu pomysłu

README pomysłu powinien, jeśli dane są dostępne, zawierać poniższe sekcje.

## 1. Metadane

Preferowany blok:

```text
Created: YYYY-MM-DD
Last updated: YYYY-MM-DD
Origin: ChatGPT conversation / observation / business problem / research
Status: CAPTURED
```

Jeżeli pomysł pochodzi z kilku rozmów, należy to zaznaczyć.

## 2. Nazwa i krótki opis

Jednoznaczna nazwa oraz krótkie wyjaśnienie, czego dotyczy pomysł.

## 3. Problem

Dokładny opis problemu, który pomysł ma rozwiązać.

Należy opisać m.in.:

- obecny sposób działania,
- co jest niewygodne, wolne, kosztowne lub błędogenne,
- kto doświadcza problemu,
- jak często problem występuje,
- jakie są skutki pozostawienia problemu bez rozwiązania.

## 4. Cel

Co dokładnie chcemy osiągnąć.

Cel powinien być opisany funkcjonalnie, a nie tylko technologicznie.

Zamiast:

> napisać aplikację w React

lepiej:

> umożliwić pracownikowi obsługę zamówień Allegro, ERLI i PrestaShop w jednym interfejsie, z aktualnymi statusami i bez ręcznego przechodzenia pomiędzy trzema panelami.

## 5. Kontekst

Wszystkie informacje potrzebne do zrozumienia pomysłu:

- proces biznesowy,
- środowisko pracy,
- używane systemy,
- istniejące ograniczenia,
- wcześniejsze rozwiązania,
- powiązane projekty,
- istotne decyzje historyczne.

## 6. Ustalenia z rozmów

Należy zapisywać wszystkie istotne wnioski wypracowane w rozmowach, także te, które nie zostały jeszcze wdrożone.

Trzeba rozróżniać:

- fakt,
- założenie,
- hipotezę,
- propozycję,
- decyzję,
- rozwiązanie odrzucone,
- element wymagający weryfikacji.

Nie wolno przedstawiać hipotezy jako zatwierdzonej decyzji.

## 7. Proponowane rozwiązanie

Szczegółowy opis aktualnie preferowanego wariantu.

Jeżeli dotyczy systemu technicznego, należy opisać m.in.:

- architekturę,
- komponenty,
- przepływ danych,
- źródła prawdy,
- integracje,
- autoryzację,
- synchronizację,
- obsługę błędów,
- bezpieczeństwo,
- wymagania sprzętowe,
- zależności zewnętrzne.

## 8. Alternatywne rozwiązania

Nie usuwać wariantów tylko dlatego, że nie zostały wybrane.

Dla każdej sensownej alternatywy opisać:

- jak działa,
- zalety,
- wady,
- koszty,
- ograniczenia,
- kiedy mogłaby być lepsza od wariantu preferowanego.

## 9. Integracje

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

Dla integracji jeszcze niesprawdzonych używać oznaczenia `DO WERYFIKACJI`.

## 10. Dane i źródło prawdy

Jeżeli pomysł obejmuje dane, należy określić:

- skąd pochodzą,
- gdzie są przechowywane,
- który system jest źródłem prawdy,
- kto może je zmieniać,
- jak działa synchronizacja,
- jak rozwiązywane są konflikty.

## 11. Interfejs i UX

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

## 12. Automatyzacje i agenci

Jeżeli pomysł ma wykorzystywać automatyzacje lub agentów AI, opisać:

- jakie zdarzenia uruchamiają działanie,
- jakie dane agent otrzymuje,
- co może wykonać automatycznie,
- co wymaga zatwierdzenia człowieka,
- jakie ma uprawnienia,
- jakie są ograniczenia bezpieczeństwa,
- jakie logi i audyt działania są wymagane.

Preferowane jest projektowanie agentów wokół zdarzeń systemowych, a nie tworzenie agentów bez jasno określonej odpowiedzialności.

## 13. Sprzęt lokalny

Jeżeli pomysł współpracuje ze sprzętem, opisać np.:

- drukarki,
- wagi USB/RS-232,
- skanery,
- terminale,
- komputery stanowiskowe,
- lokalne agenty/bridge,
- protokoły komunikacyjne,
- zachowanie po utracie połączenia.

## 14. Koszty

Oddzielnie opisywać:

- koszt prototypu,
- koszt wdrożenia,
- koszt miesięczny,
- koszt sprzętu,
- koszt usług zewnętrznych,
- potencjalny koszt utrzymania.

Jeżeli wartość jest szacunkiem, należy to oznaczyć.

## 15. Ryzyka i ograniczenia

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

## 16. MVP / wersja minimalna

Określić najmniejszy zakres, który pozwala sprawdzić, czy pomysł rzeczywiście ma wartość.

Nie należy automatycznie projektować pełnego systemu, jeżeli można najpierw zweryfikować główną hipotezę prostszą i tańszą wersją.

## 17. Wersja docelowa

Osobno opisać kierunek rozwoju po potwierdzeniu MVP.

## 18. Etapy realizacji

Przykładowy schemat:

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

## 19. Kryteria akceptacji

Pomysł powinien posiadać mierzalne warunki uznania danego etapu za zakończony.

Przykład:

- zamówienie z ERLI pojawia się w systemie bez ręcznego importu,
- zmiana statusu jest widoczna na drugim stanowisku bez ręcznego odświeżania,
- ponowny druk etykiety nie tworzy drugi raz przesyłki,
- błąd API jest zapisany w logach i widoczny dla operatora.

## 20. Testy

Plan testów powinien uwzględniać zależnie od projektu m.in.:

- happy path,
- błędy API,
- utratę internetu,
- duplikaty,
- równoczesne zmiany,
- błędne dane,
- uprawnienia,
- awarię urządzenia lokalnego.

## 21. Otwarte pytania

Wszystkie kwestie, które nadal wymagają decyzji lub researchu.

## 22. Powiązania z innymi pomysłami

To jedna z najważniejszych części repozytorium.

Dla każdego pomysłu należy wskazać możliwe połączenia z innymi folderami i opisać **na czym polega powiązanie**.

Przykład:

```text
Powiązane:
- ../order-command-center/ — wspólny model zamówień i eventów
- ../packing-workstation/ — współdzielony workflow pakowania
- ../local-device-agent/ — wspólny bridge do drukarek, wag i skanerów
```

## 23. Możliwe elementy wielokrotnego użytku

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

Celem jest unikanie budowania tego samego kilka razy.

## 24. Źródła i linki

Zapisywać linki do:

- oficjalnej dokumentacji,
- API,
- norm,
- repozytoriów,
- artykułów technicznych,
- badań,
- produktów sprzętowych,
- materiałów referencyjnych.

Przy linku warto dopisać, **po co został zapisany** i jaki wniosek z niego wynika.

Nie dodawać linków bez znaczenia tylko po to, aby dokument wyglądał na bardziej kompletny.

## 25. Historia decyzji

Jeżeli koncepcja ewoluuje, nie nadpisywać bez śladu wcześniejszych ważnych decyzji.

Zapisywać:

- co zmieniono,
- dlaczego,
- kiedy,
- co zostało odrzucone.

Dla większych pomysłów można prowadzić osobny `decisions.md`.

---

# Zapis rozmów

Jeżeli jest to możliwe, folder pomysłu powinien zawierać `conversation.md`.

Celem nie jest wyłącznie archiwizacja tekstu rozmowy. Zapis ma zachować **tok rozwoju pomysłu**.

Preferowana kolejność:

1. pełny transcript rozmowy, jeżeli jest technicznie dostępny i można go bezpiecznie zapisać,
2. jeżeli pełny transcript nie jest dostępny — szczegółowa rekonstrukcja rozmowy,
3. dodatkowo sekcja z najważniejszymi ustaleniami, zmianami koncepcji i decyzjami.

Preferowana struktura:

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

Jeżeli rozmowa zawiera dużo istotnych szczegółów, należy preferować bardziej kompletny zapis zamiast krótkiego streszczenia.

---

# Status pomysłu

Dozwolone przykładowe statusy:

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

Status nie oznacza jakości pomysłu. Pokazuje etap jego życia.

---

# Nazewnictwo folderów

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

---

# Poziom szczegółowości

W tym repozytorium preferujemy **nadmiar użytecznego kontekstu nad zbyt krótkim opisem**.

Nie należy jednak sztucznie rozwlekać treści. Każdy zapis powinien pomagać w co najmniej jednym z poniższych:

- zrozumieniu pomysłu,
- podjęciu decyzji,
- późniejszej implementacji,
- porównaniu wariantów,
- połączeniu z innym pomysłem,
- uniknięciu ponownego researchu,
- przekazaniu pracy innemu agentowi.

---

# Zasada niedublowania

Przed utworzeniem nowego folderu należy sprawdzić, czy podobny pomysł już istnieje.

Jeżeli istnieje:

- rozszerzyć istniejący folder, albo
- utworzyć osobny folder tylko wtedy, gdy koncepcje są rzeczywiście różne,
- zapisać relację pomiędzy nimi.

Jeżeli dwa pomysły z czasem stają się jednym systemem, nie należy usuwać historii. Można oznaczyć jeden jako `MERGED` i wskazać nowy nadrzędny projekt.

---

# Repozytorium nie jest źródłem prawdy dla gotowego kodu

`ideas` przechowuje koncepcje, wiedzę, decyzje i research.

Gdy pomysł przechodzi do właściwej implementacji, kod powinien trafić do odpowiedniego repozytorium projektowego. Folder w `ideas` nadal pozostaje miejscem opisującym genezę, założenia, warianty, powiązania i decyzje.

W folderze pomysłu należy wtedy dodać link do repozytorium wykonawczego.

---

# Bezpieczeństwo

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

---

# Cel długoterminowy

Repozytorium ma z czasem stworzyć mapę pomysłów 7DEJV, dzięki której można:

- wracać do niedokończonych koncepcji,
- szybko odnajdywać wcześniejsze pomysły po głównym indeksie,
- łączyć kilka pomysłów w większy system,
- identyfikować wspólne komponenty,
- wykorzystywać wcześniejszy research,
- unikać powtarzania tych samych rozmów,
- przekazywać kontekst agentom wykonawczym,
- oceniać, które pomysły dojrzały do wdrożenia.

**Pomysł zapisany w tym repozytorium powinien być użyteczny nawet wtedy, gdy osoba czytająca nie pamięta już pierwotnej rozmowy.**
