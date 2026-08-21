# ideas — pamięć projektowa 7DEJV

Centralne repozytorium trwałej pamięci pomysłów, projektów i ustaleń powstających w rozmowach.

## Po co istnieje to repo

Temat może rozpocząć się w jednym czacie, wrócić w innym i połączyć się z kolejną koncepcją. Repo ma zachować decyzje, wymagania, research, warianty, odrzucone rozwiązania i następne kroki. **Jednostką repo jest pomysł/projekt, nie rozmowa.**

Pełne zasady: [`RULES.md`](./RULES.md). Wzorzec: [`IDEA_TEMPLATE.md`](./IDEA_TEMPLATE.md). Mapa: [`INDEX.md`](./INDEX.md).

## Komenda `Zapisz w pomysłach`

Oznacza: sprawdź indeks i istniejące pomysły, rozpoznaj aktualizację/nowy temat/merge, zachowaj istotne konkrety, oznacz fakty i hipotezy, zaktualizuj relacje, historię i indeks. Pomysłów nie usuwamy.

## Klasy wiedzy

`DECISION` · `REQUIREMENT` · `VERIFIED` · `PROPOSAL` · `HYPOTHESIS` · `TODO_VERIFY` · `REJECTED` · `OPEN`

## Aktywne pomysły

| ID | Pomysł | Priorytet |
|---|---|---|
| IDEA-0001 | [7DEJV Order Operations Command Center](./order-operations-command-center/README.md) | P1 |
| IDEA-0002 | [7DEJV OS — AI/GitHub Control Plane](./7dejv-os-control-plane/README.md) | P1 |
| IDEA-0003 | [7DEJV MCP Ecosystem](./mcp-ecosystem/README.md) | P1 |
| IDEA-0004 | [7DEJV Local Task Runner](./local-task-runner/README.md) | P2 |
| IDEA-0005 | [PrestaShop Local AI Agent](./prestashop-local-ai-agent/README.md) | P1 |
| IDEA-0006 | [Marketplace Product Control & Audit](./marketplace-product-control/README.md) | P1 |
| IDEA-0007 | [Staw Expert — program kontroli splewki](./staw-expert-argulus-program/README.md) | P2 |
| IDEA-0008 | [Staw Expert — kontrolowane uwalnianie tlenu](./controlled-oxygen-release/README.md) | P2 |
| IDEA-0009 | [Business Communications & Administration Automation](./business-communications-automation/README.md) | P2 |
| IDEA-0010 | [YouTube Channel Diagnostics & Recovery](./youtube-channel-diagnostics/README.md) | P3 |
| IDEA-0011 | [AI-Assisted Workstation & Device Environment](./ai-assisted-workstation/README.md) | P3 |

## Najważniejsza zasada jakości

Krótki opis nie wystarcza. Karta pomysłu ma pozwolić agentowi po kilku tygodniach odtworzyć: cel, aktualne decyzje, wymagania, preferowany kierunek, rzeczy odrzucone, otwarte kwestie i następny krok — bez rozpoczynania analizy od zera.

## Historia i rozmowy

Nowa rozmowa nie oznacza nowego pomysłu. Jeśli dotyczy tego samego problemu i celu, aktualizujemy istniejący folder. Jeśli kilka pomysłów jest świadomie łączonych, zachowujemy genezę i relacje. Linków/ID rozmów nie wolno wymyślać; gdy są niedostępne zapisujemy tytuł, datę/słowa kluczowe i `unavailable`.

## Repo a implementacja

`ideas` przechowuje genezę, research i decyzje. Kod produkcyjny trafia do właściwych repozytoriów wykonawczych. Stan kodu i dokumentacji technicznej w repo wykonawczym ma pierwszeństwo przed historyczną rozmową.

## Bezpieczeństwo

Nigdy nie zapisujemy haseł, tokenów, kluczy API, sekretów OAuth, danych klientów ani wartości `.env`. Repozytorium było publiczne podczas konsolidacji 2026-08-21, dlatego obecny zapis celowo nie zawiera sekretów ani danych klientów. Docelowo repo powinno być prywatne ze względu na wewnętrzne koncepcje biznesowe i techniczne.