---
id: IDEA-0002
title: "7DEJV OS — AI/GitHub Control Plane"
slug: "7dejv-os-control-plane"
area: "AI / Automation / Infrastructure"
tags: [7dejv-os, github, codex, agents, skills, workflows, hooks, source-of-truth]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: architecture-audit
outcome: none
priority: P1
origin: "Wiele rozmów o organizacji GitHub, Codex, agentach, skills i workflow"
source_conversations:
  - role: development
    conversation_title: "Dostępne repozytoria GitHub"
    conversation_date: 2026-08-20
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [audit, github, agents, skills, workflow]
  - role: development
    conversation_title: "Udostępnianie projektów Codex"
    conversation_date: 2026-08-20
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [codex, repo, synchronizacja, praca-dom]
  - role: development
    conversation_title: "Hooks środowiska wtyczki"
    conversation_date: 2026-08-19
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [hooks, worktrees, codex, security]
---

# 7DEJV OS — AI/GitHub Control Plane

## 0. Mapa rozmów źródłowych
Temat rozwijał się w wielu rozmowach o repozytoriach, Codex, agentach, skills, hookach, Worktrees, handoffach i automatyzacji pracy.

## 1. Aktualny stan — przeczytaj najpierw

### Cel
Zbudować spójny system pracy, w którym ChatGPT analizuje, planuje, projektuje i audytuje; Codex i inni agenci wykonują zamknięte zadania; GitHub przechowuje kod, dokumentację, decyzje i stan techniczny.

### Najważniejsze ustalenia
- `DECISION` GitHub jest źródłem prawdy dla kodu i dokumentacji technicznej.
- `DECISION` Repozytorium wykonawcze ma pierwszeństwo przed pamięcią rozmowy w kwestii aktualnego stanu projektu.
- `DECISION` Przed tworzeniem nowych agentów/skills/workflow należy sprawdzić istniejące elementy i unikać duplikacji.
- `REQUIREMENT` Agent przed zmianą analizuje repo, dokumentację, skills, agentów i workflow.
- `REQUIREMENT` Zadanie dla agenta zawiera cel, zakres, ograniczenia, pliki, skills, kryteria akceptacji, testy i oczekiwany raport.
- `REQUIREMENT` Raport wykonania zawiera zmienione pliki, wyniki testów/poleceń, błędy, ryzyka i następny krok.
- `PROPOSAL` Docelowy Control Plane może używać GitHub Projects/Issues jako kolejki pracy.

### Aktualnie preferowany kierunek
Najpierw audyt i konsolidacja istniejącego ekosystemu, następnie standard kontraktów agentów, workflow i hooks. Dopiero potem dalsza automatyzacja.

### Czego świadomie nie robimy
- nie tworzymy nowych agentów tylko dlatego, że można;
- nie traktujemy deklaracji agenta jako dowodu wykonania;
- nie modyfikujemy szeroko repo bez audytu i uzasadnienia;
- nie przechowujemy sekretów w repo.

### Następny sensowny krok
Dokończyć pełną mapę repozytoriów i sklasyfikować agentów/skills/workflow jako KEEP / MERGE / CONVERT / REFERENCE / RETIRE.

## 2. Problem i geneza
Wiele repozytoriów, agentów i skills powstawało w różnych okresach. Ryzykiem są duplikaty, sprzeczne zasady, niejasne źródła prawdy i trudne przekazywanie pracy między komputerami/agentami.

## 3. Docelowy przepływ
`Idea/Issue → analiza ChatGPT → zamknięte zadanie → branch/worktree → Codex → testy → raport → review → merge → aktualizacja dokumentacji`.

## 4. Główne elementy
- mapa repozytoriów i odpowiedzialności;
- kontrakty agentów;
- katalog współdzielonych skills;
- hooks bezpieczeństwa i jakości;
- standard handoff (`CODEX_HANDOFF.md` tam, gdzie potrzebny);
- workflow W000–W700 / odpowiednik po audycie;
- Definition of Done;
- rozdzielenie globalnych zasad od lokalnych wyjątków repo.

## 5. Ryzyka
Tool explosion, dublowanie kompetencji, autonomiczne write bez kontroli, drift dokumentacji, różne wersje środowiska dom/praca, sekrety w logach lub repo.

## 6. Relacje
- `RELATED_TO` IDEA-0003 — MCP jest warstwą narzędziową dla OS.
- `RELATED_TO` IDEA-0004 — Local Runner wykonuje cykliczne zadania lokalne.
- `RELATED_TO` IDEA-0005 — PrestaShop Agent jest jednym z systemów wykonawczych.
- `RELATED_TO` IDEA-0001 — Order Operations może być główną aplikacją operacyjną korzystającą z zasad OS.

## 7. Repozytoria / artefakty wykonawcze
Znane repozytoria powiązane: `7dejv.os`, `7dejv-agent-os`, `7dejv-ai-command-center`, `7dejv-skills-prompts`, `7dejv-prestashop`, `7dejv-staw-expert`. Ich role wymagają dalszego audytu i konsolidacji.