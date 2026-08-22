# Centralny AI workspace + Google Drive + dwa komputery

## Status
Pomysł / architektura do dalszego rozwinięcia.

## Kontekst
Celem jest możliwość pracy z tym samym środowiskiem projektowym z dwóch komputerów (np. dom i praca), przy założeniu, że **nigdy nie odbywa się równoczesna praca na obu komputerach**. Rozważany jest również własny serwer działający 24/7 jako centralny element 7DEJV OS oraz dostęp do modeli GPT przez OpenAI API.

## Główna idea
Zamiast utrzymywać całkowicie niezależne katalogi robocze na obu komputerach, można wykorzystać folder synchronizowany przez Google Drive jako wspólny workspace. Ten sam folder jest dostępny lokalnie na obu komputerach.

Przykład:

```text
PC DOM
G:\Google Drive\7DEJV\projekty\...
        ↕
   Google Drive
        ↕
PC PRACA
G:\Google Drive\7DEJV\projekty\...
```

W folderze mogą znajdować się również lokalne klony repozytoriów Git wraz z katalogami `.git`.

## Kluczowe założenie
Nie będzie jednoczesnej pracy na dwóch komputerach. Przed zmianą stanowiska należy zakończyć synchronizację Google Drive.

To znacząco zmniejsza ryzyko konfliktów, ale go całkowicie nie eliminuje. Google Drive nie jest systemem kontroli wersji i może mieć problemy z częściowo zsynchronizowanymi plikami, plikami tylko-online, lockami i szybko zmieniającymi się metadanymi `.git`.

## Zalecany tryb pracy

1. Praca na komputerze A.
2. Przed zakończeniem sprawdzić `git status`.
3. Preferencyjnie wykonać commit istotnych zmian.
4. Upewnić się, że Google Drive zakończył synchronizację całego workspace.
5. Dopiero wtedy zakończyć pracę / wyłączyć komputer A.
6. Uruchomić komputer B.
7. Poczekać na pełną synchronizację Google Drive.
8. Przed rozpoczęciem pracy wykonać `git status` i sprawdzić stan repozytorium.

## Konfiguracja Google Drive
Folder roboczy powinien być dostępny **lokalnie/offline**, a nie działać wyłącznie jako pliki strumieniowane na żądanie. Repozytoria i szczególnie `.git` powinny fizycznie istnieć na dysku lokalnym podczas pracy.

## Rola GitHub
Google Drive nie powinien zastępować GitHub.

Docelowy podział odpowiedzialności:

- **Google Drive** — synchronizacja workspace i zwykłych plików między komputerami.
- **GitHub** — źródło prawdy dla kodu, historia zmian, branche, commity, PR-y i dodatkowe zabezpieczenie projektu.

Dzięki temu awaria lub konflikt synchronizacji Google Drive nie oznacza utraty historii kodu.

## Wariant z serwerem AI
Osobny serwer może działać jako centralny element systemu:

```text
                 OpenAI API
                     │
                AI / Agent
                     │
        ┌────────────┴────────────┐
        │                         │
   lokalne repo              Google Drive
        │                         │
      GitHub                dokumenty/pliki

PC DOM  ─────── dostęp ─────── SERWER
PC PRACA ────── dostęp ─────── SERWER
```

Sam GPT nie musi działać lokalnie. Serwer może uruchamiać aplikację/agenta, który korzysta z modeli OpenAI przez API.

### Możliwe komponenty serwera

- Ubuntu Server,
- Docker / Docker Compose,
- interfejs webowy AI (np. Open WebUI albo własny panel),
- OpenAI API,
- PostgreSQL,
- n8n,
- Git,
- Tailscale do prywatnego dostępu,
- opcjonalnie Cloudflare Tunnel dla wybranych publicznych usług/webhooków,
- opcjonalnie Ollama dla modeli lokalnych.

## Dostęp z dwóch komputerów
Agent może być uruchomiony tylko raz na serwerze. Oba komputery mogą korzystać z niego przez przeglądarkę lub bezpieczne połączenie Tailscale. Pozwala to zachować wspólne rozmowy, pamięć, konfigurację, narzędzia i dane.

## Wariant docelowy — centralny workspace na serwerze
Alternatywą dla synchronizacji repozytorium przez Google Drive jest przeniesienie właściwego workspace na serwer i używanie komputerów jako terminali.

```text
               SERWER
          /srv/7dejv/repos
                 │
        ┌────────┴────────┐
        │                 │
     PC DOM            PC PRACA
```

Ten wariant może być bezpieczniejszy dla Git niż synchronizowanie `.git` przez Google Drive. Google Drive pozostaje wtedy magazynem dokumentów, grafik, eksportów, PDF-ów i innych plików użytkowych.

## Możliwy podział danych

```text
/repos/                 # repozytoria Git
  prestashop/
  allegro/
  ideas/
  ...

/drive/                 # Google Drive
  dokumenty/
  produkty/
  grafiki/
  eksporty/
  pdf/
  archiwum/
```

Agent AI może otrzymać kontrolowany dostęp do obu obszarów.

## Potencjalne integracje agenta
W przyszłości centralny agent może korzystać m.in. z:

- GitHub API,
- PrestaShop API,
- Allegro API,
- ERLI API,
- poczty,
- n8n,
- PostgreSQL,
- Dockera,
- SSH,
- lokalnych repozytoriów,
- dokumentów z Google Drive.

## Lokalny model + GPT
Można również zastosować routing modeli:

- proste i masowe zadania → lokalny model przez Ollama,
- trudniejsze analizy/projektowanie/kod → OpenAI API.

Pozwala to ograniczyć koszt API i zachować możliwość wykonywania części zadań lokalnie.

## Ważne ograniczenia

1. ChatGPT Plus i OpenAI API są odrębnymi usługami — korzystanie z API jest rozliczane osobno.
2. Google Drive nie jest zamiennikiem Gita.
3. Synchronizacja `.git` przez Drive jest dopuszczalnym kompromisem przy sekwencyjnej pracy, ale wymaga dyscypliny i backupu w GitHub.
4. Nie należy rozpoczynać pracy na drugim komputerze przed zakończeniem synchronizacji pierwszego.
5. Serwera administracyjnego nie należy wystawiać bezpośrednio do Internetu przez otwarty port; preferowany prywatny dostęp przez Tailscale.

## Kierunek rekomendowany

### Etap 1 — minimum
- Google Drive jako synchronizowany workspace między dwoma komputerami,
- pliki zawsze dostępne offline,
- GitHub nadal jako źródło prawdy,
- obowiązkowy `git status` przy zmianie stanowiska,
- commit istotnych zmian przed zmianą komputera.

### Etap 2 — serwer
- Ubuntu Server + Docker,
- Tailscale,
- n8n,
- PostgreSQL,
- AI przez OpenAI API,
- opcjonalnie Ollama,
- repozytoria dostępne dla agenta.

### Etap 3 — docelowy 7DEJV OS
- centralny workspace na serwerze,
- komputery jako terminale,
- role i konta użytkowników,
- integracje GitHub/PrestaShop/Allegro/ERLI/e-mail,
- automatyzacje n8n,
- kontrolowane narzędzia dla agentów,
- logowanie operacji i backupy.

## Do rozstrzygnięcia przed wdrożeniem

- Czy repozytoria od początku synchronizować przez Google Drive, czy pozostawić osobne klony Git na PC.
- Czy docelowo workspace ma zostać przeniesiony całkowicie na serwer.
- Jaki interfejs AI zastosować: Open WebUI czy własny panel 7DEJV OS.
- Jak rozdzielić dane prywatne, firmowe i repozytoria.
- Jakie katalogi agent może tylko czytać, a do których może zapisywać.
- Polityka backupów i testów odtwarzania.
- Sposób zarządzania sekretami/API keys.
