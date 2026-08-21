---
id: IDEA-0004
title: "7DEJV Local Task Runner"
slug: "local-task-runner"
area: "Automation / Infrastructure"
tags: [windows, scheduler, codex, git, powershell, tasks, logs]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: concept
outcome: none
priority: P2
origin: "Rozmowa o dwóch Codexach, pracy dom/praca i cyklicznych zadaniach"
source_conversations:
  - role: origin
    conversation_title: "Udostępnianie projektów Codex"
    conversation_date: 2026-08-20
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [codex, scheduler, push, praca, dom]
---

# 7DEJV Local Task Runner

## 1. Aktualny stan

### Cel
Mały lokalny system do bezpiecznego wykonywania cyklicznych zadań na komputerach dom/praca i późniejszego uruchamiania kontrolowanych zadań Codex CLI.

### Preferowany MVP
`PowerShell + Windows Task Scheduler + tasks.yaml + Git + logs + locks`.

### Wymagania
- `REQUIREMENT` Nie uruchamiać dwóch zadań na tym samym repo jednocześnie bez blokady.
- `REQUIREMENT` Git Guard: sprawdzanie branch/status/pull przed automatycznym zadaniem i bezpieczne przerwanie przy konflikcie.
- `REQUIREMENT` Pełny log: start, polecenia, exit code, zmienione pliki, commit/push lub powód przerwania.
- `PROPOSAL` Później: `codex exec`, testy, generowanie handoff, retry, SQLite, panel WWW i powiadomienia.

### Następny krok
Zaprojektować format `tasks.yaml`, lock model i Git Guard bez dodawania jeszcze panelu WWW.

## 2. Problem
Praca na co najmniej dwóch stanowiskach zwiększa ryzyko rozjazdu branchy i ręcznego zapominania o push/pull oraz zadaniach okresowych.

## 3. Czego nie robić w MVP
Nie budować od razu rozproszonego orkiestratora, bazy danych ani rozbudowanego UI. Najpierw sprawdzić prosty runner oparty o mechanizmy Windows.

## 4. Relacje
- `CHILD_OF` IDEA-0002 — lokalny wykonawca zadań dla 7DEJV OS.