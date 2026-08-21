# INDEX — mapa pamięci projektowej

Pełny indeks pomysłów. Repo organizuje wiedzę według rzeczywistych inicjatyw, a nie według liczby rozmów. Nowa rozmowa dotycząca tego samego problemu aktualizuje istniejący pomysł.

## Aktywne

| ID | Pomysł | Obszar | Tagi | Etap | Priorytet | Najważniejszy kontekst | Aktualizacja |
|---|---|---|---|---|---|---|---|
| IDEA-0001 | [7DEJV Order Operations Command Center](./order-operations-command-center/README.md) | Operations / UI / Back Office | orders, packing, realtime, printing | concept-design | P1 | Centralna PWA do zamówień + Packing Workspace + Local Agent | 2026-08-21 |
| IDEA-0002 | [7DEJV OS — AI/GitHub Control Plane](./7dejv-os-control-plane/README.md) | AI / Automation / Infrastructure | github, codex, agents, skills, hooks | architecture-audit | P1 | Nadrzędny model pracy ChatGPT→GitHub→Codex→testy→review | 2026-08-21 |
| IDEA-0003 | [7DEJV MCP Ecosystem](./mcp-ecosystem/README.md) | AI / Integrations | mcp, docker, github, prestashop | research | P1 | Kontrolowana warstwa narzędzi MCP dla agentów | 2026-08-21 |
| IDEA-0004 | [7DEJV Local Task Runner](./local-task-runner/README.md) | Automation / Infrastructure | windows, scheduler, codex, git | concept | P2 | Lokalny scheduler/runner z Git Guard, logami i blokadami | 2026-08-21 |
| IDEA-0005 | [PrestaShop Local AI Agent](./prestashop-local-ai-agent/README.md) | PrestaShop / AI | prestashop9, api, audit, products | design | P1 | Kontrolowany audyt i zatwierdzane operacje na PrestaShop | 2026-08-21 |
| IDEA-0006 | [Marketplace Product Control & Audit](./marketplace-product-control/README.md) | Marketplace / Products | erli, allegro, product-master, shipping | concept-research | P1 | Kontrola danych produktu, logistyki i różnic PS↔marketplace | 2026-08-21 |
| IDEA-0007 | [Staw Expert — program kontroli splewki](./staw-expert-argulus-program/README.md) | Research / R&D / Products | argulus, fish, pond, research | research | P2 | Evidence-based program prewencji/wspomagania/kuracji | 2026-08-21 |
| IDEA-0008 | [Staw Expert — kontrolowane uwalnianie tlenu](./controlled-oxygen-release/README.md) | Research / R&D / Products | oxygen, CaO2, water-quality | research-prototype | P2 | Badanie wkładu/preparatu o kontrolowanym profilu uwalniania | 2026-08-21 |
| IDEA-0009 | [Business Communications & Administration Automation](./business-communications-automation/README.md) | Business / Administration / AI | email, invoices, ksef, ai-agent | concept | P2 | Centralizacja poczty i administracji z kontrolowanym AI | 2026-08-21 |
| IDEA-0010 | [YouTube Channel Diagnostics & Recovery](./youtube-channel-diagnostics/README.md) | Marketing / Analytics | youtube, comments, analytics | research | P3 | Metoda diagnozy spadków i odbudowy kanału | 2026-08-21 |
| IDEA-0011 | [AI-Assisted Workstation & Device Environment](./ai-assisted-workstation/README.md) | Infrastructure / Productivity | windows, android, screen-sharing | exploration | P3 | Standard stanowiska dom/praca i środowiska mobilnego | 2026-08-21 |
| IDEA-0012 | [7DEJV Home Automation Server — Yoga 500 + n8n](./home-automation-server/README.md) | Automation / Infrastructure / Self-hosting | n8n, docker, yoga-500, tailscale, cloudflare, backup | concept-design | P1 | Lokalny Automation Node 24/7: n8n, PostgreSQL, backup 4 TB, zdalny dostęp, domena i audyt oparty na dowodach | 2026-08-21 |

## Główne klastry

### 7DEJV OS
IDEA-0002 jest projektem nadrzędnym. IDEA-0003, IDEA-0004 i IDEA-0005 są wyspecjalizowanymi elementami ekosystemu. IDEA-0011 opisuje środowisko, na którym system działa. IDEA-0012 dostarcza lokalną, stale działającą warstwę infrastruktury i automatyzacji n8n.

### Operations / e-commerce
IDEA-0001 jest główną warstwą operacyjną zamówień. IDEA-0006 odpowiada za jakość i kontrolę danych produktowych/marketplace. IDEA-0009 dostarcza kontekst komunikacji i administracji. IDEA-0012 może hostować backend automatyzacji, backupy i integracje wspierające te projekty.

### Staw Expert R&D
IDEA-0007 i IDEA-0008 są osobnymi torami badawczymi. Nie należy łączyć terapii, preparatów ani procedur tylko dlatego, że dotyczą wody/ryb; każda interakcja wymaga osobnej walidacji.

## Wstrzymane

| ID | Pomysł | Powód wstrzymania | Następny warunek / krok | Aktualizacja |
|---|---|---|---|---|
| — | Brak | — | — | — |

## Zakończone / wdrożone

| ID | Pomysł | Wynik | Implementacja / następca | Aktualizacja |
|---|---|---|---|---|
| — | Brak | — | — | — |

## Połączone / zastąpione / odrzucone

Historia pozostaje widoczna. Pomysłów nie usuwamy.

| ID | Pomysł | Wynik | Powiązanie / następca | Powód | Aktualizacja |
|---|---|---|---|---|---|
| — | Brak | — | — | — | — |

## Rozmowy wykorzystane przy konsolidacji

W obecnym przebiegu wykorzystano dostępny kontekst m.in. z rozmów: `Kontrola listów przewozowych`, `Projekt modułu PrestaShop`, `Research serwerów MCP`, `Udostępnianie projektów Codex`, `Hooks środowiska wtyczki`, `Wybór skrzynki firmowej`, `Automatyzacja startu firmy`, `BDO dla JDG`, `Znani ichtiolodzy w Polsce`, rozmów o CaO2/tlenie, `Analiza kanału YouTube`, `Zarządzanie Androidem z Windows`, rozmów o udostępnianiu ekranu oraz rozmowy z 2026-08-21 o Yoga 500 jako lokalnym serwerze n8n/self-hosted. Lista nie jest deklaracją kompletności całej historii konta — obejmuje rozmowy dostępne podczas tej konsolidacji.

## Zasada wyszukiwania

Przed utworzeniem nowego pomysłu szukaj po problemie, systemach, tagach, funkcjach, alternatywnych nazwach, decyzjach i relacjach. Jeśli cel jest ten sam, aktualizuj istniejący pomysł zamiast tworzyć duplikat.