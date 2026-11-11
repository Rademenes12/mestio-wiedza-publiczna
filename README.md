# mestio.pl — dossier projektu (dla narzędzi zewnętrznych: Claude Design, Perplexity)

> Wiedza kontekstowa projektu **bez kodu, bez danych klientów, bez sekretów**.
> Aktualizacja: 2026-11-11. Wersja: 1.0

## Czym jest Mestio

Platforma dla wspólnot mieszkaniowych i zarządców nieruchomości (Polska):
**moduł komunikacji i rozliczeń** (dwupanelowy) + **Mestio Remonty** (rynek zleceń remontowych:
wspólnota/firma remontowa, licytacje ofert — prowizja 1% od wartości umowy **dla obu stron**).

## Glosariusz (nasze pojęcia — tak je czytaj)

| Termin | Znaczenie u nas |
|---|---|
| **Dwupanelowy UI** | zatwierdzony wzorzec: panel zarządcy + panel lokatora/wspólnoty (dwa widoki, jeden system) |
| **Kolejka AI→człowiek** | agent proponuje (odpowiedź/wycenę), **człowiek zatwierdza** — automat nic nie wysyła sam |
| **RFQ** | zapytanie ofertowe wspólnoty do firm remontowych (prowizja 1%/strona) |
| **KSeF / FA(3)** | polski obowiązkowy e-faktura (Krajowy System e-Faktur); PDF/A-3 z osadzonym XML |
| **Zarządca** | administrator wspólnoty — jego panel jest „growym” widokiem |
| **Style zatwierdzony** | jasny, premium, oszczędny w ozdobnikach — NIE przeprojektowujemy UI od zera |

## Stack (zamrożony — nie proponuj zamiany)

- **Front/hosting:** Vercel (monorepo, domena mestio.pl) — React/Next
- **Backend/dane:** Supabase (Postgres + RLS + auth) — plan bez abonamentu
- **PDF:** Gotenberg (self-host) — HTML→PDF, PDF/A-3 + osadzony XML dla KSeF FA(3)
- **Rola AI:** czat z lokatorem/wspólnotą (intake zgłoszeń), klasyfikacja do kolejki AI→człowiek
- **Środowisko:** jeden serwer VPS (Linux, Docker); narzędzia self-host, 0 zł abonamentu

## Decyzje zamrożone (nie do ponownej dyskusji)

1. UI: **dwupanelowy**, jasny premium — tylko szlif, nie redesign.
2. Wysyłka na zewnątrz: **tylko po zatwierdzeniu człowieka** (kolejka AI→człowiek).
3. Hosting: Vercel + Supabase; narzędzia self-host na VPS.
4. Prowizja Mestio Remonty: **1% od umowy — od OBU stron**.
5. Bez płatnych planów SaaS w rdzeniu (0 zł abonamentu).

## Zakres prac 2026 (kolejność)

1. **Silnik faktur C/B** + KSeF FA(3) (PDF/A-3 + XML) — priorytet #1
2. Moduł komunikacji (intake zgłoszeń, kolejka AI→człowiek)
3. Mestio Remonty — licytacje ofert (RFQ), prowizje
4. Monity/zaległości (powiadomienia po zatwierdzeniu przez zarządcę)

## Design brief (dla Claude Design)

Styl zatwierdzony: **jasny, premium, czytelny dla 50+ użytkownika** (lokatorzy). Duże kontrasty tekstu,
duże pola dotykowe, minimum kolorów, jeden akcent markowy. Reference-ekrany dostarczamy jako **screenshoty**.
Prosimy o: (a) ocenę zgodności z zasadami dostępności, (b) propozycje typografii/rytmu na tokenach designu,
(c) pojedyncze decyzje wizualne — **jedna decyzja na wiadomość**, jeden ekran na sesję.

## Pytania otwarte (do badań — dla Perplexity)

1. Prawo i praktyka: które obowiązkowe integracje PL dla panelu zarządcy (poza KSeF) w 2026?
2. Rynek: podmioty konkurujące z „remontowym marketplace” dla wspólnot w PL + modele prowizji.
3. Wzorce UX kolejki „AI proponuje → człowiek zatwierdza” w gotowych produktach (do inspiracji).
4. Dostępność: audyt checklist dla UI 50+ w PL (jesteśmy na etapie panelu MVP).

## Czego tu NIE ma

Kod źródłowego, danych klientów, kluczy/adresów API, mockupów, cenników wewnętrznych.
Dostęp do kodu = osobny brief z paczką (na żądanie).

---
*Sekcje pominięte w wersji publicznej: szczegóły finansowe, kontakty, wewnętrzne ścieżki infrastruktury.*
