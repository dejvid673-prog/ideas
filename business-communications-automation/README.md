---
id: IDEA-0009
title: "Business Communications & Administration Automation"
slug: "business-communications-automation"
area: "Business / Administration / AI"
tags: [email, gmail, ai-agent, invoices, administration, ksef, automation]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: concept
outcome: none
priority: P2
origin: "Rozmowy o skrzynce firmowej i automatyzacji startu firmy"
source_conversations:
  - role: development
    conversation_title: "Wybór skrzynki firmowej"
    conversation_date: 2026-08-20
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [email, firma, agent-ai]
  - role: development
    conversation_title: "Automatyzacja startu firmy"
    conversation_date: 2026-08-13
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [faktury, ksef, email, automatyzacja]
---

# Business Communications & Administration Automation

## 1. Aktualny stan

### Cel
Uporządkować kilka firmowych adresów e-mail, faktury, powiadomienia i zadania administracyjne tak, aby człowiek miał jeden czytelny punkt kontroli, a AI pomagało w klasyfikacji i przygotowaniu działań.

### Ustalenia
- `REQUIREMENT` System ma obsługiwać kilka skrzynek/adresów i być prosty dla pracowników.
- `PROPOSAL` Agent AI może klasyfikować pocztę, łączyć wiadomość z zamówieniem/problemem, przygotowywać odpowiedź i zadanie.
- `REQUIREMENT` Wysyłka/operacje o skutkach biznesowych powinny mieć kontrolę uprawnień i historię.
- `PROPOSAL` Automatyczny zapis faktur z poczty, miesięczne zestawienia i integracja z procesem księgowym.
- `OPEN` KSeF i docelowy obieg faktur wymagają osobnego projektu zgodności z aktualnymi przepisami i API.

### Następny krok
Zaprojektować mapę adresów firmowych, typów wiadomości i reguł routingu; dopiero potem wybierać automatyzacje i agenta.

## 2. Relacje
- `RELATED_TO` IDEA-0001 — wiadomości związane z zamówieniami/problemami powinny być widoczne w Order Operations.
- `RELATED_TO` IDEA-0002 — agent pocztowy powinien stosować te same zasady approval/audytu.