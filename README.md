# ideas — pamięć projektowa 7DEJV

Centralne repozytorium trwałej pamięci pomysłów, projektów i ustaleń powstających w rozmowach.

## Po co istnieje to repo

Najważniejszym problemem, który rozwiązuje `ideas`, jest utrata ciągłości między rozmowami. Temat może rozpocząć się w jednym czacie, wrócić po kilku dniach w innym, a następnie zostać połączony z jeszcze inną koncepcją. Repo ma sprawić, że wcześniejsze decyzje, szczegółowe ustalenia, research, warianty i odrzucone rozwiązania nie przepadają.

**Repo nie jest przede wszystkim backlogiem ani kolekcją krótkich opisów. Jest zewnętrzną pamięcią projektową.**

Dobry zapis ma pozwolić agentowi wejść w temat w nowej rozmowie bez rozpoczynania analizy od zera.

## Komenda: `Zapisz w pomysłach`

Ta fraza oznacza wykonanie pełnej procedury zapisu/aktualizacji repo `dejvid673-prog/ideas`.

Agent automatycznie:
1. sprawdza istniejące pomysły i indeks;
2. rozpoznaje, czy aktualizuje istniejący temat, tworzy nowy, czy łączy wcześniejsze;
3. zachowuje szczegółowe ustalenia z dostępnego kontekstu;
4. zapisuje aktualny stan, decyzje, wymagania, warianty, rzeczy zweryfikowane, odrzucone i otwarte;
5. aktualizuje relacje i historię;
6. aktualizuje `INDEX.md` oraz — jeśli potrzebne — skrót poniżej;
7. w miarę możliwości aktualizuje historię rozmów;
8. nigdy nie usuwa istniejącego pomysłu.

Użytkownik nie musi ręcznie podawać kategorii, nazwy folderu ani statusu.

## Najważniejsza zasada jakości

**Krótkie streszczenie nie wystarcza.** Największą wartość mają konkretne ustalenia, które normalnie trzeba byłoby ponownie odtwarzać w następnej rozmowie.

Każdy rozwinięty pomysł powinien mieć na początku sekcję `Aktualny stan — przeczytaj najpierw`, a w niej:
- cel;
- najważniejsze aktualne decyzje;
- obowiązkowe wymagania i ograniczenia;
- preferowany obecnie kierunek;
- rzeczy świadomie odrzucone lub poza zakresem;
- najważniejsze otwarte kwestie;
- następny sensowny krok.

Dalej zachowywane są szczegóły potrzebne do zrozumienia **dlaczego** podjęto te decyzje.

## Historia jest nienaruszalna

**Pomysłów nigdy nie usuwamy.** Mogą zostać połączone, zastąpione, odrzucone, wstrzymane lub wdrożone, ale ich dokumentacja pozostaje.

Nowa rozmowa nie oznacza nowego pomysłu. Jeżeli dotyczy tego samego problemu i celu, aktualizujemy istniejący folder.

Jeżeli kilka pomysłów świadomie łączymy w nową koncepcję, powstaje nowy folder z sekcją `Geneza / powstał z`. Źródłowe foldery pozostają i wskazują następcę.

## Struktura repo

```text
ideas/
├── README.md            # wejście do repo i najważniejsze zasady
├── RULES.md             # szczegółowy kontrakt pamięci i zapisu
├── IDEA_TEMPLATE.md     # wzorzec szczegółowej karty pomysłu
├── INDEX.md             # pełna mapa i wyszukiwalny indeks pomysłów
│
└── <idea-slug>/
    ├── README.md        # aktualny stan + pełna wiedza o pomyśle
    ├── conversation.md  # transcript lub oznaczona rekonstrukcja rozmów
    ├── decisions.md     # opcjonalnie: rozbudowana historia decyzji
    ├── architecture.md  # opcjonalnie: szczegóły architektury
    ├── research.md      # opcjonalnie: research i porównania
    ├── sources.md       # opcjonalnie: źródła i dokumentacja
    └── assets/          # opcjonalnie: mockupy, diagramy, screenshoty
```

Nie każdy pomysł musi mieć wszystkie pliki. Dodatkowe pliki tworzymy wtedy, gdy poprawiają możliwość odzyskania wiedzy, a nie dla samej struktury.

## Metadane

Każdy pomysł powinien otrzymać trwałe ID i machine-readable metadata, np.:

```yaml
---
id: IDEA-0001
title: Order Command Center
slug: order-command-center
area: Operations
tags: [prestashop, allegro, erli, orders]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: design
outcome: none
priority: P2
---
```

ID pozostaje stałe nawet wtedy, gdy nazwa pomysłu ewoluuje.

## Oznaczanie wiedzy

Ważne ustalenia należy w miarę możliwości klasyfikować:

- `DECISION` — decyzja;
- `REQUIREMENT` — wymaganie;
- `VERIFIED` — informacja zweryfikowana;
- `PROPOSAL` — propozycja;
- `HYPOTHESIS` — hipoteza;
- `TODO_VERIFY` — wymaga sprawdzenia;
- `REJECTED` — rozważone i odrzucone wraz z przyczyną;
- `OPEN` — pytanie nierozstrzygnięte.

Zapobiega to sytuacji, w której w kolejnej rozmowie dawna propozycja zostanie błędnie potraktowana jako podjęta decyzja.

## Relacje

Stosowane relacje mogą obejmować:
- `PARENT_OF` / `CHILD_OF`;
- `DEPENDS_ON`;
- `RELATED_TO`;
- `MERGED_FROM` / `MERGED_INTO`;
- `SUPERSEDES` / `SUPERSEDED_BY`;
- `IMPLEMENTED_IN`.

Relacja powinna zawierać opis tego, **co konkretnie łączy pomysły**, a nie sam link.

## Rozmowy

Jeżeli dostępny jest pełny transcript i wnosi wartość, można go zachować w `conversation.md`. Jeżeli pełny zapis nie jest dostępny, należy stworzyć szczegółową, wyraźnie oznaczoną rekonstrukcję wyłącznie na podstawie dostępnego kontekstu.

Najważniejsze ustalenia nie mogą pozostać ukryte wyłącznie w historii rozmowy. Muszą trafić również do głównej karty pomysłu.

## Indeks

Pełny indeks znajduje się w [`INDEX.md`](./INDEX.md). Ma umożliwiać odnalezienie tematu nawet wtedy, gdy w nowej rozmowie używana jest inna nazwa niż wcześniej.

### Szybki indeks aktywnych pomysłów

| ID | Pomysł | Obszar | Etap | Najważniejszy kontekst | Aktualizacja |
|---|---|---|---|---|---|
| — | Brak zapisanych pomysłów | — | — | — | — |

## Repo a implementacja

`ideas` jest źródłem prawdy dla genezy, ustaleń, researchu i decyzji. Kod produkcyjny trafia do właściwego repozytorium wykonawczego. Folder pomysłu pozostaje i wskazuje implementację oraz istotne artefakty.

## Bezpieczeństwo

Nigdy nie zapisujemy haseł, tokenów, kluczy API, sekretów OAuth, danych klientów ani wartości z `.env`. Można dokumentować wymagane integracje, zakres uprawnień i nazwy zmiennych bez ich wartości.

## Dokumenty sterujące

- [`RULES.md`](./RULES.md) — szczegółowe reguły zapisu i zachowania pamięci.
- [`IDEA_TEMPLATE.md`](./IDEA_TEMPLATE.md) — wzorzec rozwiniętego pomysłu.
- [`INDEX.md`](./INDEX.md) — pełna mapa pomysłów.

**Najważniejszym produktem tego repo nie jest lista pomysłów. Jest nim zachowana wiedza, dzięki której nie musimy drugi raz dochodzić do tych samych ustaleń.**
