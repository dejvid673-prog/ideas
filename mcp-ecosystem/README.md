---
id: IDEA-0003
title: "7DEJV MCP Ecosystem"
slug: "mcp-ecosystem"
area: "AI / Integrations"
tags: [mcp, github, prestashop, allegro, erli, n8n, docker, tools]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: research
outcome: none
priority: P1
origin: "Research serwerów MCP i wcześniejsze rozmowy o Docker MCP Toolkit"
source_conversations:
  - role: research
    conversation_title: "Research serwerów MCP"
    conversation_date: 2026-08-20
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [MCP, serwery, 7DEJV, Docker]
---

# 7DEJV MCP Ecosystem

## 1. Aktualny stan — przeczytaj najpierw

### Cel
Zapewnić agentom 7DEJV OS kontrolowany, standaryzowany dostęp do narzędzi i danych bez budowania osobnej integracji klienta AI z każdym systemem.

### Ustalenia
- `VERIFIED` MCP jest warstwą udostępniającą Tools/Resources/Prompts; nie jest sam w sobie agentem.
- `DECISION` Skills określają jak pracować, MCP określa z jakich narzędzi/danych agent może korzystać.
- `DECISION` GitHub pozostaje źródłem prawdy niezależnie od MCP.
- `PROPOSAL` Kontrolowany Docker MCP Gateway/Hub jako centralna warstwa serwerów.
- `PROPOSAL` Priorytet P0: GitHub MCP, Context7/dokumentacja, Playwright oraz zasoby dokumentacji PrestaShop.
- `PROPOSAL` Kolejne: n8n, Allegro w sandbox/read-only, natywne możliwości MCP PrestaShop po audycie.
- `PROPOSAL` W przyszłości własny `7dejv-mcp` dla produktów, zamówień, ERLI, wysyłki, magazynu, raportów i systemu.
- `REQUIREMENT` Domyślnie READ; write tylko tam, gdzie potrzebne, z approval dla operacji ryzykownych.
- `REQUIREMENT` Oddzielne poświadczenia test/production i minimalne uprawnienia.

### Następny krok
Zweryfikować aktualne oficjalne/utrzymywane serwery, ich bezpieczeństwo i zakres; stworzyć rejestr MCP z właścicielem, źródłem, uprawnieniami, statusem i zastosowaniem.

## 2. Architektura
`Agent/ChatGPT/Codex → profil MCP → Gateway → wybrane serwery → API/systemy`.

Profile mają ograniczać tool explosion: DEV, PRESTASHOP-READ, MARKETPLACE-READ, OPERATIONS itd.

## 3. Ryzyka
Supply-chain, zbyt szerokie scopes, niekontrolowany write, prompt/tool injection, ujawnienie danych produkcyjnych, duża liczba narzędzi pogarszająca wybór właściwego toola.

## 4. Relacje
- `CHILD_OF` IDEA-0002 — warstwa narzędziowa 7DEJV OS.
- `RELATED_TO` IDEA-0005 — PrestaShop Agent może korzystać z MCP/API.
- `RELATED_TO` IDEA-0001 — Order Operations może udostępniać własne kontrolowane narzędzia w późniejszym etapie.