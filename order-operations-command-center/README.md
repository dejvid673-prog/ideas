---
id: IDEA-0001
title: "7DEJV Order Operations Command Center"
slug: "order-operations-command-center"
area: "Operations / UI / Back Office"
tags: [prestashop, allegro, erli, orders, packing, pwa, realtime, multi-monitor, printing, scale, agents, ui]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: concept-design
outcome: none
priority: P1
origin: "Rozmowa o skillach UI, centrum zamówień i stanowisku pakowania"
source_conversations:
  - role: origin
    conversation_title: "7DEJV OS — Back Office, centrum zamówień i skill UI"
    conversation_date: 2026-08-21
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [skills, UI, back-office, centrum-dowodzenia, zamówienia, pakowanie, dwa-monitory, drukarka, waga]
    note: "Rozmowa rozwinęła się od skilla do projektowania UI do koncepcji centralnego systemu operacyjnego zamówień."
---

# 7DEJV Order Operations Command Center

## 0. Mapa rozmów źródłowych

| Rola | Data | Tytuł rozmowy | Link / ID | Słowa kluczowe | Co wnosiła |
|---|---|---|---|---|---|
| origin | 2026-08-21 | 7DEJV OS — Back Office, centrum zamówień i skill UI | unavailable | UI, zamówienia, packing, realtime, multi-monitor, agents | Główna koncepcja systemu, UX, architektura, integracje i sprzęt lokalny |

## 1. Aktualny stan — przeczytaj najpierw

### Cel
Zbudować centralny, wygodny system operacyjny do obsługi zamówień i pakowania, dostępny zarówno w domu, jak i w pracy, integrujący przede wszystkim PrestaShop 9.1, Allegro i ERLI. System ma ograniczyć konieczność pracy w wielu topornych panelach i docelowo stać się centrum zdarzeń firmy.

### Najważniejsze ustalenia
- `DECISION` System powinien mieć jeden centralny backend i bazę danych, a stanowiska dom/praca mają być klientami tego samego systemu, zamiast synchronizować dwie niezależne lokalne bazy.
- `DECISION` Preferowany kierunek prototypu: aplikacja webowa/PWA zachowująca się jak program desktopowy.
- `DECISION` V1 koncentruje się na zamówieniach i pakowaniu, nie na budowie kompletnego ERP/BaseLinkera ani autonomicznego systemu AI.
- `REQUIREMENT` Dane muszą być aktualne pomiędzy lokalizacjami i ekranami; preferowane eventy/realtime plus okresowa synchronizacja zabezpieczająca.
- `REQUIREMENT` Integracje muszą być rzeczywiście działające i weryfikowane endpoint po endpoincie; żadnych założeń typu „API istnieje, więc wszystko się da”.
- `REQUIREMENT` Stanowisko pakowania ma obsługiwać trzy wyniki pracy: spakowane (zielony), częściowo spakowane (żółty), niespakowane/problem (czerwony), oraz techniczny stan „w trakcie”.
- `REQUIREMENT` System ma wspierać opcjonalną pracę na dwóch monitorach.
- `REQUIREMENT` Druk etykiety ma następować bez ręcznego pobierania i otwierania pliku; potrzebny lokalny bridge/agent drukowania.
- `PROPOSAL` Ten sam Local Agent może później obsługiwać wagę USB/RS-232 i skaner kodów.
- `DECISION` Agenci AI nie są rdzeniem V1. Najpierw powstaje model zdarzeń, do którego później można podpinać agentów.

### Aktualnie preferowany kierunek
PWA + centralny backend + PostgreSQL (na prototyp rozważany Supabase Free) + adaptery PrestaShop/Allegro/ERLI + mechanizm realtime + synchronizacja okresowa + lokalny 7DEJV Local Agent do sprzętu stanowiska.

### Czego świadomie nie robimy
- dwóch niezależnych aplikacji z osobnymi bazami w domu i pracy;
- pełnego ERP/CRM/PIM w MVP;
- natywnej aplikacji Windows bez uzasadnienia;
- agentów AI sterujących procesami przed ustabilizowaniem event modelu;
- automatycznego ponownego tworzenia przesyłki po błędzie samego druku.

### Najważniejsze nierozwiązane kwestie
- dokładny audyt możliwości READ/WRITE/EVENT/POLLING dla PrestaShop, Allegro, ERLI, DPD i późniejszych integracji;
- wybór ostatecznego backendu/hostingu po prototypie;
- model statusów i mapowanie statusów zewnętrznych;
- sposób obsługi konfliktów zmian;
- dokładny protokół lokalnego Print/Device Agenta;
- wybór fizycznej wagi i drukarki na podstawie udokumentowanych interfejsów;
- zakres integracji Gmail/wiadomości marketplace w kolejnych etapach.

### Następny sensowny krok
Wykonać Integration Feasibility Audit i zbudować tabelę dla każdej integracji: READ / WRITE / EVENT / POLLING / AUTH / LIMIT / RISK / SOURCE. Następnie zamrozić zakres MVP i wykonać działający prototyp Order Command Center oraz Packing Workspace.

## 2. Problem i geneza

### Problem
Obsługa sprzedaży jest rozproszona między PrestaShop, Allegro, ERLI i kolejne narzędzia. PrestaShop 9.1 jest oceniany jako toporny i mało czytelny operacyjnie. Celem nie jest wyłącznie zmiana wyglądu, lecz stworzenie wygodniejszej warstwy operacyjnej.

### Dlaczego temat powstał
Punktem wyjścia była potrzeba tworzenia znacznie lepszych interfejsów Back Office oraz skill `7dejv-ui-prototype-builder`. Podczas projektowania benchmarku Order Command Center koncepcja rozwinęła się w realny system operacyjny zamówień, pakowania, integracji i lokalnego sprzętu.

### Użytkownicy
- właściciel/administrator;
- pracownik obsługi zamówień;
- pracownik stanowiska pakowania;
- w przyszłości agenci automatyzacji działający jako konsumenci zdarzeń.

## 3. Wymagania

### Wymagania obowiązkowe
- jeden spójny stan danych dostępny z domu i pracy;
- PrestaShop + Allegro + ERLI jako pierwsze kanały;
- szybka lista zamówień, filtrowanie i statusy;
- aktualizacja zmian między ekranami bez ręcznego odświeżania tam, gdzie to uzasadnione;
- historia zmian i użytkownik wykonujący operację;
- Packing Workspace;
- lokalny druk etykiet bez dialogu drukowania;
- obsługa awarii druku bez ponownego tworzenia przesyłki;
- architektura możliwa do rozbudowy o urządzenia lokalne i agentów.

### Preferencje
- minimalny lub zerowy koszt infrastruktury na etapie eksperymentu;
- desktop-first, monitory ok. 24 cali;
- możliwość rozszerzenia stanowiska na dwa monitory;
- system ma wyglądać jak narzędzie operacyjne/program, nawet jeśli technicznie jest PWA.

## 4. UX / styl Back Office

### Profil wizualny
- ciemny granat/grafit jako baza, ale dark mode nie jest celem samym w sobie;
- wysoka gęstość informacji bez wizualnego chaosu;
- informacje nie powinny niepotrzebnie się powtarzać;
- kolor ma znaczenie semantyczne i umożliwia szybkie skanowanie ekranu bez czytania wszystkich tekstów;
- jaskrawe, kontrastowe akcenty dla najważniejszych statusów i działań;
- czerwony: problem/weryfikacja; żółty/pomarańczowy: uwaga/częściowe; zielony: sukces/gotowe; niebieski/fiolet: akcje/informacje/procesy zależnie od kontekstu;
- kompaktowy sidebar po lewej, z ikoną + nazwą i kategoriami oraz rozwijanymi grupami;
- sidebar nie może zabierać niepotrzebnie dużej części ekranu;
- rutynowe dane (np. adres klienta podczas standardowego pakowania) są wizualnie drugorzędne;
- najważniejsze informacje i częste akcje są większe;
- mało tekstów instruktażowych w codziennym Back Office;
- niewielkie lub umiarkowane zaokrąglenia; preferencja bardziej kanciastych powierzchni;
- przestrzeń ekranu ma być wykorzystywana efektywnie;
- funkcja > dekoracja, ale interfejs ma być przyjemny wizualnie.

### Command Center
Centralny dashboard ma być centrum dowodzenia, nie kolekcją przypadkowych wykresów. Główna przestrzeń pokazuje stan pracy, wyjątki, kolejkę i najważniejsze akcje. Prawy panel może prezentować aktywność i w przyszłości agentów.

## 5. Packing Workspace — dwa monitory

### Koncepcja
Opcjonalny tryb stanowiska pakowania wykorzystujący dwa niezależne, zsynchronizowane okna.

**Monitor kolejki:** lista zamówień, kanał, status, liczba paczek, czas, priorytet/problem.

**Monitor roboczy:** aktywne zamówienie, produkty, ilości, dane wysyłki, waga, przewoźnik, nadanie i druk.

Kliknięcie zamówienia w kolejce ładuje je na monitorze roboczym. Zmiana statusu na monitorze roboczym natychmiast aktualizuje kolejkę.

### Stany pakowania
- `WAITING` — oczekuje;
- `IN_PROGRESS` — techniczny stan po otwarciu/rozpoczęciu;
- `PACKED` — zielony, spakowane i gotowe;
- `PARTIAL` — żółty, częściowo spakowane;
- `BLOCKED/NOT_PACKED` — czerwony, niespakowane/wymaga działania.

Kolor nigdy nie jest jedynym nośnikiem informacji: kolor + ikona + tekst.

### Przyciski końcowe
Często używana akcja `SPAKOWANE` powinna być duża i wygodna. Żółta i czerwona akcja są wyjątkami i powinny być przestrzennie oddzielone od zielonej oraz od siebie, aby ograniczyć przypadkowe kliknięcia.

### Powody wyjątków
Dla `PARTIAL` i `BLOCKED` system powinien umożliwić szybkie wskazanie przyczyny, np. brak produktu, problem z adresem, płatnością, przesyłką, konieczność kontaktu, inny problem. W przypadku częściowego pakowania warto przechowywać postęp per pozycja, np. 2/2, 0/1, 4/4.

## 6. Architektura

```text
PrestaShop ─┐
Allegro ────┼────> Integrations / Sync ───> 7DEJV Backend ───> PostgreSQL
ERLI ───────┘                                  │
                                               ├── Realtime/events ──> PWA dom
                                               ├── Realtime/events ──> PWA praca
                                               └── Print/Device jobs ─> Local Agent ─> sprzęt
```

### Źródła prawdy
Na początku platformy pozostają źródłami swoich danych zewnętrznych. 7DEJV OS przechowuje ujednolicony model operacyjny oraz własne dane, np. packing_status, packed_by, internal_notes, problem_reason, agent_flags.

### Synchronizacja
Preferowana hybryda:
1. event/webhook tam, gdzie platforma go oferuje i jest odpowiedni;
2. okresowe pobieranie zmian jako zabezpieczenie;
3. rzadsza synchronizacja kontrolna/reconciliation.

Nie zakładać niezawodności pojedynczego webhooka.

## 7. Integracje — obecny stan koncepcyjny

### PrestaShop 9.1
`VERIFIED` W rozmowie sprawdzono istnienie oficjalnego Webservice API i możliwość dostępu do zasobów zamówień oraz nadawania ograniczonych uprawnień. Szczegółowy zakres należy jeszcze audytować endpoint po endpoincie.

### Allegro
`VERIFIED` Istnieje oficjalne REST API do procesów sprzedażowych. Szczegółowy zakres operacji wymaganych przez projekt pozostaje do audytu.

### ERLI
`VERIFIED` W rozmowie sprawdzono oficjalne REST API, mechanizm inbox i hooki m.in. dla utworzenia zamówienia/zmiany statusu. Szczegóły należy utrwalić w osobnym researchu ze źródłami.

### DPD / przewoźnicy
`TODO_VERIFY` Wymagany dokładny audyt obecnie używanej integracji/API. Cel: z poziomu zamówienia ustawić parametry, utworzyć przesyłkę, otrzymać numer i etykietę, przekazać ją do lokalnego druku.

## 8. Local Agent / Print Bridge

### Cel
Przeglądarka/PWA nie powinna być odpowiedzialna za bezpośredni, bezdialogowy dostęp do lokalnego sprzętu. Na stanowisku działa mała usługa/aplikacja Windows `7DEJV Local Agent`.

### Pierwsza funkcja: drukowanie
Przepływ:
1. użytkownik ustawia parametry przesyłki;
2. `NADAJ I DRUKUJ`;
3. backend tworzy przesyłkę przez API przewoźnika;
4. zapisuje shipment ID/numer;
5. pobiera etykietę;
6. tworzy `PRINT_JOB`;
7. Local Agent odbiera zadanie;
8. wysyła etykietę na skonfigurowaną drukarkę;
9. zwraca ACK/FAILED;
10. UI pokazuje wynik.

### Krytyczna zasada idempotencji
`shipment created` i `label printed` są osobnymi stanami. Awaria drukarki nie może spowodować ponownego utworzenia przesyłki. `DRUKUJ PONOWNIE` używa istniejącej etykiety.

Przykładowe stany:
- shipment_status = CREATED;
- label_status = READY;
- print_status = PENDING / PRINTED / FAILED.

### Format etykiety
Preferować format natywny drukarki (np. ZPL), jeśli przewoźnik i drukarka go wspierają; PDF pozostaje obsługiwanym wariantem. Nie zakładać ZPL bez sprawdzenia konkretnego API i urządzenia.

### Konfiguracja per stanowisko
Stanowisko powinno mapować role urządzeń, np. `label_printer`, `document_printer`, `scale`, zamiast polegać wyłącznie na domyślnej drukarce Windows.

## 9. Waga i inne urządzenia

### Waga
`PROPOSAL` Waga paczkowa USB lub RS-232 może przekazywać pomiar do Local Agenta. Preferowane urządzenia z udokumentowanym USB HID/API albo USB-Serial/RS-232. Sam napis „USB” nie jest wystarczającym kryterium zakupu.

Możliwy workflow: paczka na wadze → Local Agent odczytuje pomiar → po ustabilizowaniu wartości przekazuje wagę do aktywnego zamówienia → pracownik zatwierdza/nadaje przesyłkę.

### Rozbudowa Local Agenta
- drukarka etykiet;
- drukarka A4;
- waga;
- skaner kodów;
- inne urządzenia lokalne tylko wtedy, gdy pojawi się realna potrzeba.

## 10. Event model — fundament przyszłych agentów

Przykładowe zdarzenia:
- ORDER_CREATED
- ORDER_UPDATED
- PAYMENT_CONFIRMED
- PACKING_STARTED
- PACKING_PARTIAL
- PACKING_BLOCKED
- PACKING_COMPLETED
- SHIPMENT_CREATED
- LABEL_PRINT_FAILED
- CUSTOMER_MESSAGE_RECEIVED
- ORDER_CANCELLED

Agenci AI mają w przyszłości reagować na zdarzenia, a nie być luźną kolekcją chatbotów. Przykład: PACKING_BLOCKED + PRODUCT_MISSING może uruchomić reguły magazynowe, pilnowanie terminu marketplace i przygotowanie propozycji kontaktu z klientem.

## 11. Infrastruktura i koszt prototypu

`PROPOSAL` Na etap eksperymentalny rozważany Supabase Free (PostgreSQL/Auth/Realtime/API/Functions) jako sposób na szybki prototyp bez własnego VPS. Alternatywa: Cloudflare. Decyzja nie jest jeszcze ostateczna.

`REQUIREMENT` Nie projektować infrastruktury produkcyjnej przed potwierdzeniem wartości systemu. Darmowy tier może być prototypem, ale nie należy zakładać, że pozostanie docelową infrastrukturą.

## 12. MVP

### Minimalny zakres
- logowanie/użytkownicy;
- wspólna lista zamówień z wybranych kanałów;
- normalizacja podstawowych danych;
- filtry/statusy/wyszukiwanie;
- historia operacyjna;
- Packing Workspace;
- synchronizacja dwóch ekranów/stanowisk;
- podstawowy adapter przewoźnika;
- Local Print Agent;
- obsługa błędu i ponownego druku.

### Czego MVP celowo nie zawiera
- pełnego CRM;
- księgowości;
- PIM;
- autonomicznych agentów AI;
- aplikacji mobilnych native;
- pełnego zarządzania ofertami wszystkich marketplace;
- rozbudowanej analityki biznesowej.

### Hipoteza do zweryfikowania
Czy jedna ujednolicona warstwa operacyjna pozwala szybciej, czytelniej i z mniejszą liczbą błędów obsługiwać zamówienia niż praca bezpośrednio w wielu panelach PrestaShop/Allegro/ERLI.

## 13. Powiązany skill UI

Osobnym, ale ściśle powiązanym pomysłem jest `7dejv-ui-prototype-builder`: skill/workflow do projektowania i weryfikowania działających interfejsów Back Office. Order Command Center i Packing Workspace mają być jego pierwszymi benchmarkami.

Kluczowe założenie skilla: generacja kodu nie oznacza zakończenia zadania. Prototyp musi być uruchomiony, sprawdzony funkcjonalnie i wizualnie, poprawiony i dopiero potem oddany użytkownikowi.

## 14. Etapy realizacji

1. Integration Feasibility Audit.
2. Zamrożenie MVP i modelu danych/statusów.
3. Działający prototyp Order Command Center na mock data.
4. Działający Packing Workspace, w tym multi-window/realtime.
5. Pierwsza prawdziwa integracja jednego kanału.
6. Local Print Agent + test fizycznego wydruku.
7. Kolejne kanały i przewoźnicy.
8. Waga/skaner po potwierdzeniu wartości.
9. Event model i dopiero później agenci.
10. Ocena infrastruktury produkcyjnej po realnych testach.

## 15. Kryteria akceptacji pierwszego etapu

- prototyp jest faktycznie uruchamialny, nie jest statycznym obrazkiem;
- podstawowe akcje UI działają;
- zmiana statusu na jednym widoku jest widoczna na drugim bez ręcznego przeładowania;
- nie ma duplikowania przesyłki przy ponownym druku;
- integracje są dokumentowane na podstawie realnych endpointów i testów;
- UI pozostaje czytelne przy wysokiej gęstości danych;
- system jest w pełni używalny na jednym monitorze, drugi jest rozszerzeniem;
- historia zmian umożliwia ustalenie kto/co/kiedy zmienił.

## 16. Ryzyka

- różnice modeli zamówień i statusów między platformami;
- ograniczenia i zmiany API marketplace;
- konflikty synchronizacji dwukierunkowej;
- zgubione webhooki/eventy;
- bezpieczeństwo tokenów integracji;
- awarie lokalnego agenta/drukarki;
- błędne przypisanie drukarki do stanowiska;
- overengineering przed walidacją MVP;
- zbyt wczesne dodanie AI zamiast stabilizacji procesów.

## 17. Bezpieczeństwo

- tokeny i sekrety nigdy nie trafiają do repo;
- minimalne uprawnienia API;
- rozdział uprawnień użytkowników;
- log audytowy operacji;
- walidacja danych wejściowych;
- bezpieczna komunikacja Local Agent ↔ backend;
- działania krytyczne i finansowe nie mogą być wykonywane przez agentów bez świadomie zaprojektowanych uprawnień/approval.

## 18. Elementy wielokrotnego użytku

- 7DEJV Local Agent;
- adapterowy model integracji;
- event bus/model zdarzeń;
- komponenty UI Back Office;
- detachable/multi-window workspace;
- status/reason model;
- mechanizm print job + retry/idempotency;
- przyszły 7DEJV UI Kit.

## 19. Historia decyzji

| Data | Zmiana / decyzja | Powód | Wpływ |
|---|---|---|---|
| 2026-08-21 | Wybrano kierunek centralnej aplikacji zamiast dwóch lokalnych baz | dane mają być wspólne w domu i pracy | upraszcza synchronizację i źródło prawdy |
| 2026-08-21 | Multi-monitor jako opcjonalny tryb | szczególnie użyteczny przy pakowaniu | Packing Workspace jako osobny widok operacyjny |
| 2026-08-21 | Dodano Local Agent | potrzeba bezdialogowego druku i późniejszego sprzętu | powstaje lokalna warstwa urządzeń |
| 2026-08-21 | Rozdzielono utworzenie przesyłki od druku | zapobieganie duplikatom przy awarii drukarki | wymagana idempotencja i osobne stany |
| 2026-08-21 | Waga USB/RS-232 jako późniejsze rozszerzenie | eliminacja ręcznego przepisywania masy | wymaga doboru sprzętu z udokumentowanym protokołem |
| 2026-08-21 | AI przesunięto za event model | uniknięcie budowy efektownych, ale nieużytecznych botów | agenci będą konsumentami zdarzeń |

## 20. Repozytoria / artefakty wykonawcze
Na tym etapie brak repozytorium implementacyjnego. Ten folder jest źródłem prawdy dla genezy i aktualnej koncepcji. Po rozpoczęciu implementacji należy dodać link do repo wykonawczego, branchy/PR oraz prototypów.