# ideas

Centralne repozytorium pomysłów 7DEJV.

Repozytorium służy do trwałego zachowywania pomysłów, koncepcji, niedokończonych projektów, wariantów rozwiązań, researchu i ustaleń z rozmów w formie na tyle szczegółowej, aby można było wrócić do nich po tygodniach lub miesiącach bez ponownego odtwarzania całego kontekstu.

## Nienaruszalna zasada historii

**Pomysłów nigdy nie usuwamy.** Repozytorium ma zachowywać historię ewolucji koncepcji, również gdy pomysł został odrzucony, zastąpiony, połączony z innymi albo przestał być aktualnym kierunkiem.

Nie wolno usuwać folderu pomysłu tylko dlatego, że:
- powstała lepsza wersja,
- wykonujemy reset/reorganizację pomysłów,
- kilka pomysłów zaczęło się pokrywać,
- pomysł został odrzucony,
- został wdrożony w innym repozytorium,
- powstaje nowy pomysł nadrzędny.

Jeżeli dwa lub więcej istniejących pomysłów zostaje połączonych w nową koncepcję, należy **utworzyć nowy folder dla nowego pomysłu**, zachowując wszystkie foldery źródłowe. W README nowego pomysłu obowiązkowo należy dodać sekcję `Geneza / powstał z`, zawierającą linki do wszystkich pomysłów źródłowych i opis tego, co zostało z każdego z nich przejęte.

Pomysły źródłowe mogą otrzymać status `MERGED`, `SUPERSEDED`, `REJECTED`, `DONE` lub inny adekwatny status, ale ich dokumentacja pozostaje w repozytorium. W ich README należy dodać relację `Połączony w / zastąpiony przez`, wskazując nowy folder. Główny indeks również zachowuje stare pozycje i pokazuje ich status oraz relację do następcy.

Ta zasada ma pierwszeństwo przed zasadą niedublowania: niedublowanie zapobiega przypadkowemu tworzeniu tego samego pomysłu drugi raz, ale **świadome połączenie, reset lub stworzenie nowej generacji koncepcji tworzy nowy pomysł i nigdy nie kasuje historii**.

---

# Komenda operacyjna: `Zapisz w pomysłach`

Fraza `Zapisz w pomysłach` jest stałą komendą operacyjną odnoszącą się do repozytorium `dejvid673-prog/ideas`.

Po komendzie należy:
1. przeanalizować pełny dostępny kontekst rozmowy,
2. sprawdzić istniejące pomysły,
3. ustalić, czy rozmowa rozwija istniejący pomysł, tworzy nowy, czy łączy kilka wcześniejszych,
4. zaktualizować istniejący folder, jeśli jest to naturalna kontynuacja tej samej koncepcji,
5. utworzyć nowy folder, jeśli powstaje odrębna koncepcja, nowa generacja lub świadome połączenie wcześniejszych pomysłów,
6. nigdy nie usuwać istniejącego pomysłu,
7. zapisać możliwie pełny kontekst, decyzje, warianty, integracje, ryzyka, źródła i otwarte pytania,
8. w miarę możliwości prowadzić `conversation.md`, bez wymyślania brakujących wypowiedzi,
9. zapisać relacje i genezę między pomysłami,
10. zawsze zaktualizować główny indeks pomysłów w tym README,
11. nie zapisywać sekretów, tokenów, haseł, kluczy API ani danych klientów.

---

# Indeks pomysłów

> Indeks jest aktualizowany przy użyciu komendy `Zapisz w pomysłach`. Ma zawierać również pomysły historyczne, połączone, zastąpione i odrzucone — nic nie znika z mapy repozytorium.

| Pomysł | Status | Krótki opis | Powiązania / następca | Ostatnia aktualizacja |
|---|---|---|---|---|
| _Brak zapisanych pomysłów w indeksie_ | — | Pierwszy wpis zostanie dodany podczas pierwszego użycia komendy. | — | — |

---

# Standard folderu pomysłu

Każdy odrębny pomysł otrzymuje osobny folder w `lowercase-kebab-case`. Minimalnie posiada szczegółowy `README.md`; dla większych koncepcji można dodawać `conversation.md`, `decisions.md`, `architecture.md`, `research.md`, `sources.md`, `todo.md` i `assets/`.

README pomysłu powinien w miarę dostępności danych zawierać:

1. **Metadane** — Created, Last updated, Origin, Status.
2. **Nazwa i krótki opis**.
3. **Problem** — obecny proces, niedogodności, skutki i użytkownicy.
4. **Cel funkcjonalny**.
5. **Kontekst** — systemy, środowisko, wcześniejsze rozwiązania i ograniczenia.
6. **Ustalenia z rozmów** — z rozróżnieniem faktów, założeń, hipotez, propozycji, decyzji i rzeczy do weryfikacji.
7. **Proponowane rozwiązanie** — architektura, komponenty, przepływy danych, źródła prawdy, synchronizacja, autoryzacja, błędy i bezpieczeństwo.
8. **Alternatywne rozwiązania** — zalety, wady, koszty, ograniczenia i warunki wyboru.
9. **Integracje** — READ/WRITE, API, webhook/event, polling, auth, limity, ryzyka i dokumentacja; niesprawdzone elementy oznaczać `DO WERYFIKACJI`.
10. **Dane i źródło prawdy** — pochodzenie, przechowywanie, modyfikacja, synchronizacja i konflikty.
11. **Interfejs i UX** — użytkownik, zadania, akcje, priorytety, nawigacja, widoki, stany, desktop/mobile/multi-monitor i zasady wizualne.
12. **Automatyzacje i agenci** — eventy, dane wejściowe, uprawnienia, human approval, logi i audyt.
13. **Sprzęt lokalny** — drukarki, wagi, skanery, terminale, lokalne bridge/agenty, protokoły i awarie.
14. **Koszty** — prototyp, wdrożenie, miesięczne utrzymanie, sprzęt i usługi zewnętrzne; szacunki oznaczać jako szacunki.
15. **Ryzyka i ograniczenia** — API, synchronizacja, internet, bezpieczeństwo, błędy użytkownika, vendor lock-in, skalowanie i utrzymanie.
16. **MVP** — najmniejszy zakres pozwalający zweryfikować wartość.
17. **Wersja docelowa**.
18. **Etapy realizacji**.
19. **Kryteria akceptacji** — mierzalne.
20. **Plan testów** — happy path, błędy API, utrata internetu, duplikaty, równoczesność, dane, uprawnienia i awarie sprzętu.
21. **Otwarte pytania**.
22. **Powiązania z innymi pomysłami** — linki i opis relacji.
23. **Geneza / powstał z** — obowiązkowa dla pomysłu będącego połączeniem lub nową generacją wcześniejszych pomysłów. Dla każdego źródła wskazać, co zostało przejęte, zmienione albo odrzucone.
24. **Możliwe elementy wielokrotnego użytku** — UI, API client, moduł PrestaShop, local agent, event system, adapter, skill, workflow, schema itd.
25. **Źródła i linki** — z opisem, po co dane źródło jest zapisane i jaki wniosek wspiera.
26. **Historia decyzji** — co zmieniono, dlaczego, kiedy i co zostało odrzucone.

## Zapis rozmów

Jeżeli jest to możliwe, folder powinien zawierać `conversation.md`. Preferowany jest pełny transcript, jeśli jest technicznie dostępny i bezpieczny do zapisania. W przeciwnym razie należy stworzyć szczegółową rekonstrukcję i jednoznacznie oznaczyć ją jako rekonstrukcję. Nie wolno wymyślać brakujących wypowiedzi.

## Statusy

Przykładowe statusy: `CAPTURED`, `RESEARCH`, `DESIGN`, `PROTOTYPE`, `VALIDATION`, `READY`, `IN_PROGRESS`, `PAUSED`, `MERGED`, `SUPERSEDED`, `REJECTED`, `DONE`.

Status zmienia sposób interpretacji pomysłu, **nie jest podstawą do jego usunięcia**.

## Powiązania i łączenie

Przed utworzeniem pomysłu należy sprawdzić istniejące foldery, aby uniknąć przypadkowego duplikatu. Jeżeli jednak użytkownik lub analiza świadomie prowadzi do połączenia kilku pomysłów albo stworzenia nowej wersji nadrzędnej, powstaje **nowy folder**, a stare pozostają nietknięte jako źródła historyczne.

Przykład:

```text
ideas/
├── order-command-center/          # istniejący pomysł A
├── packing-workstation/           # istniejący pomysł B
├── local-device-agent/            # istniejący pomysł C
└── unified-order-operations/      # NOWY pomysł powstały z A+B+C
```

W `unified-order-operations/README.md`:

```text
## Geneza / powstał z
- ../order-command-center/ — model centrum operacyjnego i wspólnej kolejki zamówień.
- ../packing-workstation/ — workflow pakowania i tryb multi-monitor.
- ../local-device-agent/ — integracja drukarek, wag i skanerów.
```

W źródłowych README należy dodać link do `../unified-order-operations/`, ale nie usuwać ani nie przepisywać ich historii.

---

# Repozytorium a implementacja

`ideas` jest źródłem prawdy dla genezy pomysłów, researchu, wariantów i decyzji, ale nie dla produkcyjnego kodu. Po przejściu do implementacji kod trafia do właściwego repozytorium projektowego, a folder pomysłu pozostaje i otrzymuje link do repo wykonawczego.

# Bezpieczeństwo

Nigdy nie zapisywać haseł, tokenów, kluczy API, sekretów OAuth, danych klientów ani plików `.env` z sekretami. Można zapisywać nazwy wymaganych zmiennych, ale bez wartości.

# Cel długoterminowy

Repozytorium ma być trwałą mapą ewolucji pomysłów 7DEJV. Ma umożliwiać powrót do niedokończonych koncepcji, łączenie kilku pomysłów w większe systemy, odnajdywanie wspólnych komponentów, ponowne wykorzystanie researchu i przekazywanie pełnego kontekstu agentom wykonawczym.

**Historia pomysłów jest wartością. Pomysł może zostać zastąpiony, połączony lub odrzucony, ale nie może zniknąć z repozytorium.**