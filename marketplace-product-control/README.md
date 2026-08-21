---
id: IDEA-0006
title: "Marketplace Product Control & Audit"
slug: "marketplace-product-control"
area: "Marketplace / Products"
tags: [erli, allegro, prestashop, products, audit, shipping, pricing, product-master]
created: 2026-08-21
updated: 2026-08-21
lifecycle: active
stage: concept-research
outcome: none
priority: P1
origin: "Rozmowy o ERLI, Allegro, audycie produktów i konflikcie cenników dostaw"
source_conversations:
  - role: development
    conversation_title: "BDO dla JDG"
    conversation_date: 2026-08-18
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [ERLI, cenniki, waga, dostawy]
  - role: development
    conversation_title: "Projekt modułu PrestaShop"
    conversation_date: 2026-08-19
    conversation_url: unavailable
    conversation_id: unavailable
    keywords: [audyt, produkty, ERLI, PrestaShop]
---

# Marketplace Product Control & Audit

## 1. Aktualny stan

### Cel
Jednoznacznie kontrolować dane produktu pomiędzy PrestaShop, Allegro i ERLI oraz wykrywać błędy przed publikacją lub po synchronizacji.

### Problemy do rozwiązania
- różne wymagania platform dla wagi, dostawy, kategorii i ofert;
- konflikt modelu cenników ERLI: masa paczki + maksymalna liczba sztuk, szczególnie 1 kg × 20 vs 20 kg × 1;
- potrzeba audytu produktów wysłanych z PrestaShop do ERLI;
- ryzyko utraty marży przez błędną wagę/dostawę/Smart;
- rozbieżności nazw, opisów, cen, SKU, SEO i danych logistycznych.

### Ustalenia
- `REQUIREMENT` Rozróżniać dane źródłowe produktu od danych specyficznych dla marketplace.
- `REQUIREMENT` Każdy wariant magazynowy powinien mieć stabilny SKU; wcześniejsza propozycja formatu: `KATEGORIA-MARKA-PRODUKT-WARIANT`.
- `REQUIREMENT` Audyt ma generować różnice i ryzyka, a nie automatycznie przepisywać dane bez kontroli.
- `PROPOSAL` Product Master może stać się nadrzędnym modelem danych, ale wybór technologii wymaga ponownej oceny; wcześniejszy Airtable był rozważany bez autonomicznych automatyzacji.
- `REQUIREMENT` Logistyka musi uwzględniać rzeczywistą masę paczki, limity przewoźnika i koszt dostawy, nie tylko masę produktu.

### Następny krok
Odtworzyć wynik istniejącego audytu Codex produktów PrestaShop→ERLI z repo/raportu i na jego podstawie zdefiniować schemat Product Master + walidatory marketplace.

## 2. MVP
- import zestawu produktów;
- normalizacja pól;
- walidatory SKU/wagi/ceny/kategorii/dostawy;
- diff PrestaShop ↔ marketplace;
- raport błędów i rekomendowanych zmian;
- ręczne zatwierdzanie.

## 3. Relacje
- `RELATED_TO` IDEA-0005 — wspólny mechanizm audytu danych PrestaShop.
- `RELATED_TO` IDEA-0001 — dane logistyczne i zamówienia z marketplace trafiają do Command Center.