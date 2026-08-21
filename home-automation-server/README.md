---
id: IDEA-0012
title: "7DEJV Home Automation Server — Yoga 500 + n8n"
slug: "home-automation-server"
area: "Automation / Infrastructure / Self-hosting"
tags: [n8n, docker, ubuntu-server, yoga-500, self-hosted, tailscale, cloudflare-tunnel, postgresql, backup, prestashop, monitoring]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: concept-design
outcome: none
priority: P1
origin: "Pomysł wykorzystania Lenovo Yoga 500 jako stale działającego lokalnego serwera automatyzacji, początkowo skoncentrowanego na n8n, a następnie rozwiniętego o self-hosted usługi, backup, zdalny dostęp i własny panel wielokanałowy."
source_conversations:
  - role: origin
    conversation_title: "Pomysł serwera z Yoga 500 / lokalny serwer n8n"
    conversation_date: 2026-08-21
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [Yoga 500, n8n, Docker, Awesome Selfhosted, Tailscale, Cloudflare Tunnel, PrestaShop backup]
    note: "Rozmowa rozwinęła pomysł od prostego serwera n8n do lokalnego węzła automatyzacji i infrastruktury operacyjnej firmy."
---

# 7DEJV Home Automation Server — Yoga 500 + n8n

## 0. Mapa rozmów źródłowych

| Rola | Data | Tytuł rozmowy | Link / ID | Słowa kluczowe | Co wnosiła |
|---|---|---|---|---|---|
| origin/development | 2026-08-21 | Pomysł serwera z Yoga 500 / lokalny serwer n8n | unavailable | Yoga 500, n8n, Docker, Awesome Selfhosted, backup, Tailscale, Cloudflare Tunnel | Geneza, architektura, zdalny dostęp, domena, backup PrestaShop, audyt i kierunek panelu wielokanałowego |

## 1. Aktualny stan — przeczytaj najpierw

### Cel

Zbudować z posiadanego Lenovo Yoga 500 energooszczędny, stale działający lokalny serwer automatyzacji firmy. Głównym silnikiem ma być n8n. Serwer ma z czasem obsługiwać wiele automatyzacji, integracje e-commerce, backupy, monitoring oraz backend dla własnego interfejsu wielokanałowego dostępnego z komputerów i telefonu.

### Najważniejsze ustalenia

- `DECISION` Głównym zastosowaniem serwera jest n8n i duża liczba automatyzacji; nie jest to przede wszystkim serwer AI.
- `DECISION` Docelowy host: Lenovo Yoga 500 z Linuxem/Ubuntu Server i Dockerem.
- `DECISION` n8n ma działać w Dockerze, nie jako przypadkowa instalacja bezpośrednio w systemie.
- `DECISION` PostgreSQL ma być podstawową bazą n8n zamiast traktowania instalacji jako jednorazowego eksperymentu na SQLite.
- `DECISION` Redis/workery są etapem skalowania, a nie obowiązkowym elementem pierwszej wersji.
- `DECISION` Prywatny zdalny dostęp administracyjny ma być realizowany przez Tailscale zamiast bezpośredniego wystawiania SSH/paneli technicznych do Internetu.
- `PROPOSAL` Publiczne aplikacje i webhooki pod domeną mają być wystawiane przez Cloudflare Tunnel, bez klasycznego otwierania portów routera, jeśli rozwiązanie przejdzie końcową weryfikację przed wdrożeniem.
- `DECISION` Baza PostgreSQL i aktywne dane n8n powinny preferencyjnie pozostać na wewnętrznym SSD Yoga; posiadany zewnętrzny dysk 4 TB ma służyć głównie do backupów, archiwów, eksportów i dużych plików.
- `DECISION` Zewnętrzny dysk 4 TB nie jest sam w sobie pełnym backupem off-site.
- `DECISION` Backup PrestaShop ma obejmować zarówno bazę danych, jak i pliki sklepu, a jego jakość ma być potwierdzana testami odtworzenia.
- `DECISION` n8n może koordynować backup i raportować wynik, ale ciężkie kopiowanie/archiwizowanie powinny wykonywać standardowe narzędzia systemowe/skrypty, nie przepływ danych przez n8n.
- `DECISION` Audyt ma być oparty na mierzalnych dowodach, nie na deklaracji AI.
- `PROPOSAL` Docelowo serwer może być backendem dla własnego panelu Staw Expert/7DEJV agregującego Allegro, ERLI, PrestaShop, e-mail, przesyłki, zadania, błędy i role pracowników.

### Aktualnie preferowany kierunek

Minimalny, stabilny stack:

```text
Lenovo Yoga 500
└── Ubuntu Server
    ├── Tailscale
    └── Docker
        ├── n8n
        ├── PostgreSQL
        ├── Uptime Kuma
        ├── ntfy (opcjonalnie w V1/V2)
        └── dashboard typu Homepage (opcjonalnie)

Zewnętrzny dysk 4 TB
├── backup PrestaShop
├── backup PostgreSQL/n8n
├── archiwum
├── eksporty
└── duże pliki
```

Dalsze elementy dopiero po rzeczywistej potrzebie: Redis, n8n workers, Caddy/Traefik, MinIO, własne API, dodatkowe usługi z Awesome-Selfhosted.

### Czego świadomie nie robimy

- Nie instalujemy kilkudziesięciu aplikacji tylko dlatego, że znajdują się w Awesome-Selfhosted.
- Nie stawiamy Kubernetes ani rozbudowanego klastra na początku.
- Nie zakładamy, że Yoga będzie docelowym serwerem produkcyjnym firmy bez względu na skalę.
- Nie wystawiamy PostgreSQL, Redis ani SSH bezpośrednio do publicznego Internetu.
- Nie traktujemy zewnętrznego USB 4 TB jako jedynej kopii bezpieczeństwa.
- Nie uznajemy backupu za sprawny wyłącznie dlatego, że istnieje plik archiwum.
- Nie uznajemy wyniku audytu AI za dowód techniczny bez logów/testów/skanów.

### Najważniejsze nierozwiązane kwestie

- `TODO_VERIFY` Dokładny model Yoga 500, CPU, RAM, wewnętrzny dysk, SMART, bateria, temperatury, interfejs Ethernet/Wi-Fi i możliwości BIOS/UEFI.
- `TODO_VERIFY` Czy RAM i wewnętrzny SSD wymagają rozbudowy.
- `TODO_VERIFY` Typ i stan zewnętrznego dysku 4 TB oraz interfejs USB.
- `TODO_VERIFY` Parametry domowego Internetu i routera; nie są konieczne dla Tailscale/Cloudflare Tunnel, ale wpływają na dostępność usług.
- `OPEN` Wybór domeny i podział subdomen.
- `OPEN` Które usługi mają być wyłącznie prywatne, a które muszą być publiczne dla webhooków/API.
- `OPEN` Wybór narzędzia backupowego: np. restic/Borg/inne po osobnej analizie.
- `OPEN` Dokładny zakres pierwszych realnych automatyzacji n8n.

### Następny sensowny krok

Najpierw nauczyć się n8n w lokalnym środowisku testowym na głównym PC, równolegle zinwentaryzować hardware Yoga 500. Następnie zaprojektować i wdrożyć minimalny serwer V1, bez instalowania opcjonalnych usług przed pojawieniem się konkretnej potrzeby.

## 2. Problem i geneza

Pomysł zaczął się od potrzeby posiadania stale działającego n8n do wielu automatyzacji. Następnie pojawiła się możliwość wykorzystania nieużywanego Lenovo Yoga 500 zamiast kupowania od razu nowego serwera lub płacenia za hosting. Katalog Awesome-Selfhosted został wskazany jako źródło gotowych komponentów, ale przyjęto zasadę selekcji według realnej funkcji, a nie kolekcjonowania usług.

Projekt zaczął rozszerzać się na:
- automatyzacje e-commerce;
- integracje Allegro/ERLI/PrestaShop;
- e-mail i administrację;
- backup PrestaShop;
- monitoring;
- własny panel operacyjny;
- prywatny dostęp z pracy/telefonu;
- publiczną domenę dla wybranych usług i webhooków;
- kontrolowany audyt bezpieczeństwa i niezawodności.

## 3. Wymagania

### Wymagania obowiązkowe

- praca 24/7 lub możliwie blisko tego poziomu;
- łatwe zarządzanie zdalne;
- konteneryzacja usług;
- n8n jako główny orkiestrator;
- trwała baza PostgreSQL;
- monitoring działania;
- backup i procedura restore;
- separacja usług prywatnych od publicznych;
- brak bezpośredniego wystawienia baz danych i paneli administracyjnych;
- wersjonowana dokumentacja infrastruktury;
- audyt oparty na dowodach.

### Preferencje

- maksymalne wykorzystanie istniejącego sprzętu;
- niski koszt utrzymania;
- możliwość późniejszej migracji stacku na mini-PC/VPS/serwer bez przebudowy od zera;
- preferowanie prostych, dojrzałych komponentów;
- możliwość wykorzystania aplikacji z Awesome-Selfhosted, jeśli rozwiązują konkretny problem.

### Ograniczenia

- Yoga 500 jest starszym laptopem i może mieć ograniczony CPU/RAM/SSD;
- wewnętrzny dysk jest relatywnie mały;
- dostępny jest zewnętrzny dysk 4 TB;
- domowe zasilanie i Internet nie mają redundancji centrum danych;
- użytkownik jest początkujący w administracji serwerami, dlatego system musi być dobrze udokumentowany i odporny na błędy operacyjne.

## 4. Szczegółowe ustalenia

### `DECISION`

1. Docker na Yoga jest warstwą uruchomieniową dla n8n i usług pomocniczych.
2. n8n jest centrum automatyzacji, ale nie powinien wykonywać każdego zadania technicznego samodzielnie.
3. PostgreSQL pozostaje na szybkim i stabilnym storage wewnętrznym, jeśli pojemność na to pozwala.
4. Dysk 4 TB jest przeznaczony przede wszystkim na dane o dużej objętości, backupy i archiwa.
5. Administracja zdalna: prywatna sieć/Tailscale.
6. Publiczne wejścia: osobna warstwa tunelu/reverse proxy/access control, preferencyjnie Cloudflare Tunnel po weryfikacji.
7. Backup musi być testowany przez restore.
8. Każda ważna automatyzacja biznesowa musi być testowana także negatywnie i pod kątem idempotencji.

### `PROPOSAL`

- Uptime Kuma jako lekki monitoring V1.
- ntfy/Gotify jako kanał alertów.
- Homepage/Homarr/Dashy jako wygodny dashboard usług.
- MinIO dopiero jeśli pojawi się realna potrzeba lokalnego storage kompatybilnego z S3.
- Redis + workers dopiero przy potrzebie queue mode/concurrency.
- GitHub jako źródło prawdy konfiguracji, dokumentacji i historii zmian, bez sekretów.

### `TODO_VERIFY`

- konkretne wymagania aktualnej wersji n8n i jej licencjonowania/funkcji przed wdrożeniem;
- oficjalny sposób konfiguracji queue mode/workers dla wybranej wersji;
- aktualne zalecenia bezpieczeństwa Cloudflare/Tailscale/Docker/n8n przed produkcyjnym uruchomieniem;
- polityka retencji executions n8n;
- możliwości hostingu produkcyjnego przy awarii domowego łącza.

## 5. Rozwiązanie / warianty

### Wariant preferowany — domowy Automation Node

Yoga 500 działa jako `7dejv-node-01`: Ubuntu Server + Docker + n8n + PostgreSQL + monitoring. Tailscale zapewnia prywatny dostęp. Publiczne webhooki i wybrane aplikacje otrzymują osobną, kontrolowaną ścieżkę przez tunel/domenę. Dysk 4 TB przechowuje backupy i archiwa.

### Wariant alternatywny A — VPS

Przenieść całość do VPS, jeśli dostępność domowego Internetu/sprzętu okaże się niewystarczająca. Zaletą jest centrum danych i prostszy publiczny hosting; wadą koszt, zależność od dostawcy i storage.

### Wariant alternatywny B — hybrydowy

Publiczny panel/API/webhook gateway na VPS, natomiast n8n/storage/backup lub część workerów lokalnie. Rozważyć dopiero po wzroście krytyczności systemu.

## 6. Architektura i przepływy

```text
                         INTERNET
                            │
                ┌───────────┴───────────┐
                │                       │
          dostęp prywatny          dostęp publiczny
             Tailscale          domena / Tunnel
                │                       │
                └───────────┬───────────┘
                            ▼
                     YOGA 500 / HOME
                     Ubuntu Server
                            │
                          Docker
                            │
       ┌────────────────────┼────────────────────┐
       ▼                    ▼                    ▼
      n8n              PostgreSQL          Uptime Kuma
       │
       ├── Allegro
       ├── ERLI
       ├── PrestaShop
       ├── e-mail
       ├── GitHub
       ├── przewoźnicy
       └── inne API

                    USB / storage
                         │
                         ▼
                     dysk 4 TB
                    backup/archive
```

### Docelowy panel wielokanałowy

```text
Użytkownik/pracownik
        │
        ▼
Staw Expert / 7DEJV Operations UI
        │
     Backend API
        │
   ┌────┴────┐
   ▼         ▼
  n8n    PostgreSQL
   │
   ├── Allegro
   ├── ERLI
   ├── PrestaShop
   ├── e-mail
   └── logistyka
```

Panel nie powinien być utożsamiany z n8n. n8n jest silnikiem procesów; panel jest kontrolowanym interfejsem dla użytkownika i pracowników.

## 7. Integracje

Planowane/rozważane: PrestaShop, Allegro, ERLI, e-mail, GitHub, przewoźnicy, system alertów, Cloudflare, Tailscale. Każda integracja przed produkcyjnym użyciem wymaga osobnej weryfikacji API, autoryzacji, limitów, retry, timeoutów i skutków ponowienia operacji.

## 8. UX / sposób użycia

Dostęp administracyjny powinien być prosty: komputer domowy, komputer w pracy i telefon łączą się prywatnie z serwerem. Docelowy panel operacyjny ma prezentować wspólnie zamówienia, problemy, wiadomości, przesyłki, marketplace, automatyzacje i alerty. Pracownik powinien otrzymywać wyłącznie role/uprawnienia potrzebne do jego zadań, zamiast danych logowania do wszystkich platform źródłowych.

## 9. Automatyzacje i agenci

n8n może obsługiwać dziesiątki/setki workflow, ale obciążenie zależy bardziej od częstotliwości, równoległości i rodzaju operacji niż od samej liczby workflow. Krytyczne przepływy muszą posiadać retry, timeout, error workflow, alert i ochronę przed duplikacją.

Przykładowe obszary: zamówienia, produkty, ceny, stany, wysyłki, e-mail, dokumenty, raporty, GitHub, backup, health checks.

## 10. Sprzęt lokalny

### Yoga 500

Do inwentaryzacji: dokładny model, CPU, RAM, możliwość rozbudowy, dysk, SMART, bateria, temperatury, Ethernet/USB, BIOS/UEFI i zachowanie po zaniku zasilania. Bateria może pełnić rolę krótkiego mini-UPS wyłącznie jeśli jest w dobrym stanie.

### Dysk 4 TB

Preferowane zastosowanie: backup, archiwum, eksporty, pliki dokumentów, ewentualny storage obiektowy. Aktywnej bazy PostgreSQL nie przenosić na USB bez konkretnego powodu i testów.

## 11. Koszty i opłacalność

Główną zaletą jest wykorzystanie już posiadanego laptopa i dysku. Potencjalne koszty: SSD/RAM jeśli potrzebne, adapter Ethernet, domena, ewentualny backup off-site, później VPS/mini-PC. Koszt energii należy zmierzyć watomierzem zamiast szacować bez danych.

## 12. Ryzyka i ograniczenia

- pojedynczy punkt awarii: Yoga;
- pojedyncze domowe łącze internetowe;
- awaria USB/SSD;
- utrata konfiguracji/credentials;
- błędnie publicznie wystawiona usługa;
- zbyt szerokie uprawnienia kontenerów;
- podatne/nieaktualne obrazy;
- niekontrolowany wzrost bazy executions n8n;
- automatyzacja wykonująca podwójne operacje biznesowe;
- fałszywe poczucie bezpieczeństwa wynikające z samego istnienia backupu lub raportu skanera.

## 13. MVP

- Ubuntu Server na Yoga;
- Docker/Compose;
- n8n;
- PostgreSQL;
- Tailscale;
- Uptime Kuma;
- poprawnie zamontowany storage 4 TB;
- podstawowy backup;
- pierwszy test restore;
- jedna realna, niekrytyczna automatyzacja.

MVP nie zawiera Redis/workers, MinIO, Kubernetes, ciężkiego monitoringu, dużego AI ani publicznego panelu produkcyjnego.

## 14. Wersja docelowa

Stabilny lokalny Automation Node z wieloma workflow, bezpiecznym dostępem zdalnym, domeną dla kontrolowanych usług, monitoringiem, backupem, audytem i możliwością obsługi własnego wielokanałowego panelu operacyjnego. Architektura ma umożliwiać migrację na mocniejszy host lub model hybrydowy bez przepisywania całego systemu.

## 15. Etapy realizacji

1. Nauka n8n na PC.
2. Inwentaryzacja Yoga i dysku 4 TB.
3. Projekt storage/network/security.
4. Ubuntu Server + SSH/Tailscale.
5. Docker + Compose.
6. PostgreSQL + n8n.
7. Monitoring i alerty.
8. Backup + restore test.
9. Pierwsze bezpieczne automatyzacje.
10. Domena/publiczne webhooki po osobnym security review.
11. Rozwój panelu wielokanałowego.
12. Redis/workers/skalowanie tylko po pomiarach.

## 16. Kryteria akceptacji

- serwer uruchamia się stabilnie po restarcie;
- n8n i PostgreSQL automatycznie wracają po restarcie hosta;
- administracja z pracy działa bez publicznego SSH;
- backup jest wykonywany i przynajmniej jeden restore został praktycznie potwierdzony;
- monitoring wykrywa awarię n8n;
- sekrety nie trafiają do repo;
- publiczne porty odpowiadają wyłącznie zatwierdzonej architekturze;
- krytyczne workflow posiadają testy negatywne i idempotencji.

## 17. Plan audytu i testów

Podstawowy zestaw narzędzi:
- Lynis — audyt Linux/hardening;
- Trivy — obrazy, podatności, konfiguracja, sekrety;
- Docker Scout — druga analiza obrazów/SBOM;
- `n8n audit` — natywny audyt instancji n8n;
- Uptime Kuma — availability;
- smartmontools — SMART dysków;
- `ss`, `systemctl`, `journalctl`, `docker inspect`, logi Dockera — stan rzeczywisty;
- narzędzie backupowe + praktyczny restore test.

Zasada: AI interpretuje wyniki, ale `PASS` wymaga technicznego dowodu. Średnia ocena nie może ukrywać blokera. Nieudany restore oznacza `NOT PRODUCTION READY` niezależnie od pozostałych ocen.

Częstotliwość robocza do dalszego dopracowania:
- ciągle: availability;
- codziennie: backup, disk usage, critical errors;
- tygodniowo: vulnerability/n8n audit/SMART;
- miesięcznie: szerszy system audit i restore;
- kwartalnie: pełny disaster recovery exercise.

## 18. Relacje z innymi pomysłami

| Relacja | Pomysł | Co je łączy |
|---|---|---|
| RELATED_TO | IDEA-0001 — Order Operations Command Center | Serwer może hostować backend/automatyzacje dla centralnego panelu operacyjnego. |
| RELATED_TO | IDEA-0002 — 7DEJV OS Control Plane | Automation Node może być warstwą wykonawczą infrastruktury 7DEJV OS. |
| RELATED_TO | IDEA-0003 — MCP Ecosystem | Serwer może później hostować kontrolowane serwery/usługi MCP. |
| RELATED_TO | IDEA-0004 — Local Task Runner | Część cyklicznych zadań może zostać przejęta przez n8n lub działać obok niego. |
| RELATED_TO | IDEA-0005 — PrestaShop Local AI Agent | Yoga może hostować komponenty integracyjne/automatyzacyjne i backup PrestaShop. |
| RELATED_TO | IDEA-0009 — Business Communications Automation | n8n może być silnikiem automatyzacji poczty i administracji. |

## 19. Elementy wielokrotnego użytku

- standard Docker Compose dla usług;
- standard backup/restore;
- standard healthcheck;
- polityka publikacji portów;
- standard nazw workflow n8n;
- wspólny error workflow;
- standard testów idempotencji;
- szablon karty usługi i raportu audytu.

## 20. Źródła i linki

- Awesome-Selfhosted: https://github.com/awesome-selfhosted/awesome-selfhosted — katalog potencjalnych komponentów; nie jest listą obowiązkowych instalacji.
- Oficjalna dokumentacja n8n, Docker, Tailscale i Cloudflare powinna być ponownie sprawdzona przed konkretnym wdrożeniem; historyczne ustalenia z rozmowy nie zastępują aktualnej dokumentacji.

## 21. Historia decyzji i zmian

| Data | Źródło / rozmowa | Zmiana lub decyzja | Powód | Wpływ |
|---|---|---|---|---|
| 2026-08-21 | bieżąca rozmowa | Yoga 500 jako lokalny serwer | wykorzystanie istniejącego sprzętu | powstanie koncepcji |
| 2026-08-21 | bieżąca rozmowa | n8n określono jako główny cel | potrzeba wielu automatyzacji | uproszczenie architektury |
| 2026-08-21 | bieżąca rozmowa | Docker jako standard hostowania | izolacja, migracja, utrzymanie | podstawa stacku |
| 2026-08-21 | bieżąca rozmowa | 4 TB jako storage backup/archive | mały dysk Yoga | rozdzielenie storage |
| 2026-08-21 | bieżąca rozmowa | backup PrestaShop + restore tests | potrzeba realnej odtwarzalności | funkcja serwera |
| 2026-08-21 | bieżąca rozmowa | audyt wielowarstwowy oparty na dowodach | brak niezależnego administratora | zasada jakości |
| 2026-08-21 | bieżąca rozmowa | Tailscale dla administracji z pracy | brak potrzeby publicznego SSH | bezpieczny remote access |
| 2026-08-21 | bieżąca rozmowa | Cloudflare Tunnel jako preferowany kandydat dla domeny/publicznych wejść | ograniczenie ekspozycji routera | wymaga weryfikacji przy wdrożeniu |

## 22. Repozytoria / artefakty wykonawcze

Na etapie koncepcji brak dedykowanego repo implementacyjnego. Gdy rozpocznie się wdrożenie, konfiguracja infrastruktury powinna trafić do osobnego repo wykonawczego, a `ideas` zachować genezę, decyzje i relacje. Sekrety i wartości `.env` nie mogą trafić do repo.