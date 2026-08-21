---
id: IDEA-0005
title: "PrestaShop Local AI Agent"
slug: "prestashop-local-ai-agent"
area: "PrestaShop / AI"
tags: [prestashop9, api, mcp, products, audit, codex, local-agent]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: design
outcome: none
priority: P1
origin: "Rozmowy o lokalnym agencie ChatGPT/PrestaShop i audycie produktów"
source_conversations:
  - role: development
    conversation_title: "Projekt modułu PrestaShop"
    conversation_date: 2026-08-19
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [prestashop, agent, api, produkty, audyt]
---

# PrestaShop Local AI Agent

## 1. Aktualny stan

### Cel
Kontrolowane narzędzie lokalne do pobierania danych PrestaShop, audytu, proponowania zmian, generowania raportu i wykonywania zatwierdzonych operacji.

### Ustalenia
- `DECISION` Domyślnie PrestaShop 9; wersję rzeczywistą potwierdza repo/środowisko.
- `DECISION` Nie modyfikować core; preferować moduły, hooki, usługi Symfony, osobne tabele i oficjalne API.
- `DECISION` Pierwszy model pracy ma być ręcznie wyzwalany przez administratora, bez autonomicznego crona/workera.
- `REQUIREMENT` Przepływ: import/pobranie → audyt → propozycje → zatwierdzenie → zmiana → raport → weryfikacja.
- `REQUIREMENT` Zacząć READ_ONLY i rozszerzać write operacja po operacji.
- `REQUIREMENT` Log audytowy i możliwość ustalenia, co agent zmienił.
- `PROPOSAL` Możliwa architektura: mała aplikacja lokalna zamiast ciężkiego modułu PrestaShop.
- `PROPOSAL` MCP może być warstwą narzędziową, ale API pozostaje interfejsem systemowym.

### Następny krok
Audyt istniejącego `7dejv-prestashop`, aktualnych skills i oficjalnych możliwości API/MCP; następnie jeden pilot na pojedynczym produkcie.

## 2. Zakres pilota
1. pobierz jeden produkt;
2. pokaż stan wejściowy;
3. wykonaj audyt według jawnych reguł;
4. przygotuj diff/propozycję;
5. po approval zapisz minimalną zmianę;
6. pobierz produkt ponownie;
7. wygeneruj raport z dowodem wyniku.

## 3. Bezpieczeństwo
Minimalne scopes, brak sekretów w repo/logach, CSRF i kontrola uprawnień w BO, walidacja danych, parametryzowane zapytania, brak bezpośredniego write bez approval w początkowej fazie.

## 4. Relacje
- `CHILD_OF` IDEA-0002 — wykonawczy komponent 7DEJV OS.
- `RELATED_TO` IDEA-0003 — może korzystać z MCP.
- `RELATED_TO` IDEA-0006 — audyt produktów marketplace może używać wspólnego modelu danych.
- `RELATED_TO` IDEA-0001 — część funkcji operacyjnych może zostać później wykorzystana w Command Center.