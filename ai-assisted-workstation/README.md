---
id: IDEA-0011
title: "AI-Assisted Workstation & Device Environment"
slug: "ai-assisted-workstation"
area: "Infrastructure / Productivity"
tags: [windows, android, screen-sharing, workstation, ai, phone]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: exploration
outcome: none
priority: P3
origin: "Rozmowy o udostępnianiu ekranu, telefonie firmowym i środowisku Windows"
source_conversations:
  - role: development
    conversation_title: "Zarządzanie Androidem z Windows"
    conversation_date: 2026-08-10
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [android, windows, telefon, firma]
  - role: development
    conversation_title: "Budzenie z zadaniem"
    conversation_date: 2026-08-18
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [screen-sharing, chatgpt, komputer]
---

# AI-Assisted Workstation & Device Environment

## 1. Aktualny stan

### Cel
Uporządkować środowisko Windows + Android tak, aby praca firmowa była odseparowana od prywatnej, łatwa do obsługi i możliwa do wspierania przez AI/automatyzacje.

### Wątki składowe
- oddzielny profil/środowisko Windows dla firmy;
- zarządzanie Realme/Android z Windows;
- prywatna i firmowa strefa telefonu;
- wykorzystanie SIM/kont w dwóch strefach;
- udostępnianie ekranu i prowadzenie użytkownika krok po kroku;
- lokalne AI/Ollama jako możliwy komponent infrastruktury, ale nie cel sam w sobie.

### Ustalenia
- `REQUIREMENT` Bezpieczeństwo kont firmowych i rozdzielenie danych ma pierwszeństwo przed wygodą pełnego współdzielenia.
- `PROPOSAL` Wspólny standard konfiguracji stanowiska dom/praca może ograniczyć różnice środowiskowe Codex/VS Code/Git/Docker.
- `OPEN` Zakres realnego sterowania/obserwacji ekranu przez AI zależy od aktualnych możliwości aplikacji i nie może być zakładany bez weryfikacji.

### Następny krok
Spisać docelowy standard stanowiska 7DEJV: konta Windows, katalogi, Git, VS Code, Docker, Codex, sekrety, backup i urządzenia mobilne; oddzielić elementy obowiązkowe od eksperymentalnych.

## 2. Relacje
- `RELATED_TO` IDEA-0002 — standard środowiska wykonawczego 7DEJV OS.
- `RELATED_TO` IDEA-0004 — Local Runner działa na tych stanowiskach.