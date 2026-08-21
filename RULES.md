# RULES — pamięć projektowa 7DEJV

## Cel nadrzędny

Repozytorium `ideas` jest przede wszystkim zewnętrzną pamięcią projektową rozmów 7DEJV, a nie backlogiem zadań ani katalogiem krótkich notatek.

Najważniejszym kryterium jakości zapisu jest odpowiedź na pytanie:

> Czy po kilku tygodniach lub miesiącach, w nowej rozmowie i bez pamiętania starego czatu, agent może odtworzyć najważniejsze ustalenia, decyzje, warianty i nierozwiązane problemy bez zaczynania analizy od zera?

Jeżeli nie — zapis jest zbyt płytki.

## Komenda `Zapisz w pomysłach`

Po tej komendzie agent ma automatycznie:
1. sprawdzić istniejące pomysły i ich relacje;
2. rozpoznać, czy bieżąca rozmowa aktualizuje istniejący pomysł, tworzy nowy, czy łączy wcześniejsze;
3. zachować szczegółowe ustalenia z dostępnego kontekstu rozmowy;
4. zaktualizować kartę pomysłu i indeks;
5. dopisać historię zmian i źródło nowych ustaleń;
6. oznaczyć elementy niepewne, nieweryfikowane i otwarte;
7. nie usuwać wcześniejszej wiedzy tylko dlatego, że zmienił się aktualny kierunek.

Użytkownik nie musi podawać kategorii, statusu ani nazwy folderu. Agent klasyfikuje materiał sam.

## Priorytet informacji

Najwyższy priorytet mają:
- konkretne decyzje i ich uzasadnienie;
- wymagania i ograniczenia;
- rzeczy, których użytkownik wyraźnie chce lub nie chce;
- znalezione rozwiązania i ich warianty;
- wyniki researchu i weryfikacji;
- architektura i przepływy danych;
- integracje oraz potwierdzone możliwości API;
- ryzyka, problemy i odrzucone kierunki wraz z przyczyną;
- zależności z innymi pomysłami;
- otwarte pytania i następny sensowny krok;
- istotne szczegóły UX, operacyjne, biznesowe i techniczne.

Krótki opis jest wyłącznie pomocą nawigacyjną. Nie może zastępować szczegółowego zapisu.

## Fakty a pomysły

Każdy zapis powinien w miarę możliwości rozróżniać:
- `DECISION` — podjęta decyzja;
- `REQUIREMENT` — wymaganie;
- `VERIFIED` — informacja zweryfikowana;
- `PROPOSAL` — propozycja, jeszcze nie decyzja;
- `HYPOTHESIS` — hipoteza;
- `TODO_VERIFY` — wymaga weryfikacji;
- `REJECTED` — rozważone i odrzucone wraz z powodem;
- `OPEN` — nierozstrzygnięte pytanie.

Nie wolno przepisywać propozycji jako decyzji ani hipotezy jako faktu.

## Historia jest nienaruszalna

Pomysłów nie usuwamy. Jeśli kierunek został zastąpiony, połączony, odrzucony albo wdrożony, zachowujemy jego dokumentację i oznaczamy wynik.

Jeżeli kilka pomysłów zostaje świadomie połączonych, tworzymy nowy pomysł i zapisujemy jego genezę. Pomysły źródłowe pozostają w repo.

## Aktualizacja istniejącego pomysłu

Nowa rozmowa nie oznacza nowego pomysłu. Jeżeli dotyczy tego samego problemu i celu, aktualizujemy istniejący folder.

Przy aktualizacji:
- nie zastępuj bez śladu wcześniejszych ustaleń;
- zaznacz, co zostało zmienione i dlaczego;
- aktualny stan ma być łatwy do odnalezienia;
- historyczne decyzje zachowuj w historii decyzji lub rozmów.

## Szczegółowość

Nie obowiązuje sztuczny limit długości. Lepiej zachować ważny kontekst niż skrócić go do ogólnika.

Jednocześnie nie należy mnożyć tekstu bez wartości. Szczegółowość oznacza zachowanie konkretów, a nie powtarzanie tej samej informacji wieloma słowami.

## Rozmowy

`conversation.md` służy do zachowania genezy i kolejnych etapów dyskusji. Jeśli pełny transcript jest dostępny i użyteczny, można go zachować. Jeśli nie, należy stworzyć dokładną rekonstrukcję opartą wyłącznie na dostępnej treści i oznaczyć ją jako rekonstrukcję.

Najważniejsze decyzje nie mogą istnieć wyłącznie w `conversation.md`. Muszą zostać przeniesione do głównej karty pomysłu lub `decisions.md`, aby agent nie musiał czytać całej historii w celu ustalenia aktualnego stanu.

## Relacje

Pomysły mogą mieć relacje m.in.:
- `PARENT_OF` / `CHILD_OF`;
- `DEPENDS_ON`;
- `RELATED_TO`;
- `MERGED_FROM` / `MERGED_INTO`;
- `SUPERSEDES` / `SUPERSEDED_BY`;
- `IMPLEMENTED_IN`.

Relacja ma zawierać nie tylko link, ale również krótkie wyjaśnienie, co łączy pomysły.

## Implementacja

Repo `ideas` przechowuje wiedzę o genezie i projekcie. Kod produkcyjny trafia do repo wykonawczego. Pomysł pozostaje w `ideas` i wskazuje repo implementacyjne oraz istotne artefakty.

## Bezpieczeństwo

Nigdy nie zapisujemy sekretów, tokenów, haseł, kluczy API, danych klientów ani wartości z `.env`. Można dokumentować nazwy integracji, wymagane uprawnienia i nazwy zmiennych bez ich wartości.
