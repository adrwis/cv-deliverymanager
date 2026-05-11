# Changelog — 2026-05-03

## Podsumowanie

Sesja poprawek CV Delivery Manager i 7 dopasowanych CV: stat tiles odzwierciedlające faktyczny zakres odpowiedzialności (people-cost allocation, nie ownership budżetu), nowy generator dopasowanych CV w estetyce redesign (navy+gold), polonizacja, depolonizacja czasowników (imperfekt), unifikacja oznaczeń języków.

**Build:** nie dotyczy (tylko zmiany w cv-analityk + cv-deliverymanager)
**Pliki zmodyfikowane:** 3 | **Pliki nowe:** 2 (generator + ten changelog)

---

## Zmiany

### 1. CV Delivery Manager redesign — content + estetyka

**Problem:** Kafelki statystyk i tekst CV przekłamywały zakres odpowiedzialności ($15M Annual Budget Owned, ~40 IT Projects Coordinated). Adriana faktycznie ogarniała people-cost allocation dla obu liczb. Ponadto bullet Zimmer "Continuous Improvement tracker to standardise process change management" był nieprawdziwy — aplikacja służyła do gromadzenia nowych rozwiązań i usprawnień, nie do change management.

**Rozwiązanie:**
- Stat tiles: `$15M Annual Budget Owned` → `$15M People-Cost Pool Allocated`; `~40 IT Projects Coordinated` → `~40 IT Projects Cost-Allocated`
- Zimmer bullet: `to standardise process change management` → `to capture new solutions and process improvements` (też w PL: `do standaryzacji zarządzania zmianami procesowymi` → `do gromadzenia nowych rozwiązań i usprawnień procesowych`)
- ISS impact: em dashes (—) zamienione na dwukropek/przecinek
- Sidebar: usunięty wiersz `Open to FinTech & Banking`
- Plik wynikowy: `AG_Delivery Manager_FinTech_Redesign_EN.pdf` → `AG_Delivery Manager.pdf`

### 2. Iteracja po feedbacku Adriany — padding, czasowniki, języki

**Problem:** Tekst CV był „obgryziony" z krawędzi. PL czasowniki używały formy perfektywnej (przeanalizowałam) zamiast imperfektywnej (analizowałam). Stat tile mówił `8+ Years Delivery` zamiast bardziej uniwersalnego `Experience`. Oznaczenia języków zawierały nadmiarowe `C1` i `A2`.

**Rozwiązanie:**
- Padding `.side` 38px→44px (góra/dół), `.main` 38px→44px wszędzie; `.page2 padding-top` 32→38px
- Stat #1: `Years Delivery` → `Years Experience` (PL: `Lat Realizacji` → `Lat Doświadczenia`)
- PL czasowniki: Przeprojektowałam→Analizowałam, Przeszkoliłam→Szkoliłam, Stworzyłam→Tworzyłam, Wdrożyłam→Wdrażałam, Zmapowałam→Mapowałam, Zaprojektowałam→Projektowałam, Zdiagnozowałam→Diagnozowałam (5 impact paragrafów DM PL + 4 Analyst PL)
- Języki: `C1 · Fluent` → `Fluent`; `C1 · Biegły` → `Biegły`; `A2` → `Basic` / `Podstawowy`

### 3. Nowy generator: 7 dopasowanych CV w estetyce redesign

**Problem:** Stary `generate-tailored-cvs.js` generował 7 dopasowanych CV w starszej estetyce (Inter, Fraunces, jednolity layout z editorial pull-quote). Adriana chciała te same 7 CV w stylu nowego DM redesign (navy+gold sidebar 250px, Cormorant Garamond + Inter, photo, stat tiles, impact callouts).

**Rozwiązanie:** Nowy plik `generate-tailored-cvs-redesign.js` (~830 linii) — port estetyki redesign + parametryzacja per oferta:
- Profile data: `dmProfile` (en+pl) i `analystProfile` (en+pl) z bullets, impacts, sidebarSkills, stats, education, certs, method, toolbox, gdpr
- Offer override: `title`, `summary`, `skillOrder` (mapuje na kolejność toolbox grid)
- Tailoring: skill bars sidebar per profil, toolbox per oferta (skillOrder)
- 7 PDFów wygenerowanych — każdy 2 strony A4, ~3.7 MB

| Plik | Profil | Język | Pod ofertę |
|------|--------|:-----:|------------|
| `AG_Lead_PM_DWH_BI_EN.pdf` | DM | EN | Lead PM DWH/BI |
| `AG_Executive_Data_Analyst_FinTech_EN.pdf` | Analyst | EN | GoMining Executive Data Analyst |
| `AG_Process_Business_PM_EN.pdf` | DM | EN | Hays Process/Business PM |
| `AG_Process_Automation_Lead_PL.pdf` | DM | PL | InPost Lead Automation |
| `AG_Power_Platform_Consultant_PL.pdf` | DM | PL | Budowa 2.0 Power Platform |
| `AG_PowerBI_Developer_PL.pdf` | Analyst | PL | Power BI Developer rescue IT |
| `AG_PowerBI_Solutions_Specialist_EN.pdf` | Analyst | EN | GP Strategies Power BI Specialist |

### 4. Analyst CV — content fixes (oba języki)

**Problem:** Stat tiles Analyst były niespójne z DM (Reporting Scope vs People-Cost). Polski PowerBI Developer miał angielskie wyrażenia w nawiasie (`star schema, measures, relationships`) i nadmiarowe zdanie o współpracy z inżynierami danych. Trustwave bullet używał `insighty „at-a-glance"`. Zwrot `obiegi raportowe` lepiej brzmi jako `workflow raportowe` (zostawić po angielsku). Drobne błędy gramatyczne i interpunkcyjne.

**Rozwiązanie:**
- Analyst stat tiles ujednolicone z DM (Pula Kosztów Osobowych / Projektów IT Alokowanych / Lat Doświadczenia / Członków Zespołu) — EN + PL
- PowerBI Developer PL: `(star schema, measures, relationships)` → `(schemat gwiazdy, miary, relacje)`
- PowerBI Developer PL: usunięte zdanie `współpracuję z inżynierami danych przy zapewnianiu spójności i gotowości danych do analizy`
- Trustwave bullet (PL+EN): `insighty „at-a-glance" w Power BI` / `at-a-glance insights in Power BI` → `w Power BI` / `in Power BI` (uproszczone)
- Analyst HSBC bullet PL: `budżetowanie, prognozowanie, alokacja zasobów` → `budżetowanie, prognozowanie alokacji zasobów`
- Analyst HSBC impact PL: `obiegi raportowe` → `workflow raportowe`
- Analyst ISS bullet PL: `Novatorium — wdrożenie` → `Novatorium: wdrożenie` (em dash → dwukropek)
- Analyst Zimmer impact PL: usunięte słowo `każdej` (komunikację każdej zmiany → komunikację zmiany)

### 5. Strona standalone cv-deliverymanager — sync

**Problem:** Strona miała `C1 biegły` / `C1 fluent` i `A2 podstawowy` / `A2 basic` w sekcji języków. Bullet Zimmer miał stary tekst `do standaryzacji zarządzania zmianami procesowymi`.

**Rozwiązanie:**
- `index.html` (PL+EN): `C1 fluent`/`C1 biegły` → `fluent`/`biegły`; `A2 basic`/`A2 podstawowy` → `basic`/`podstawowy`
- Zimmer bullet (PL+EN) zsynchronizowany z PDF: `capture new solutions and process improvements` / `gromadzenia nowych rozwiązań i usprawnień procesowych`

### Pliki

| Repo | Plik | Zmiana |
|------|------|--------|
| cv-analityk | `cv/generate-cv-delivery-manager-redesign.js` | Modified (stat tiles, padding, languages, sidebar cleanup) |
| cv-analityk | `cv/generate-tailored-cvs-redesign.js` | **Nowy** generator (~830 linii) — 7 dopasowanych CV w estetyce redesign |
| cv-deliverymanager | `index.html` | Modified (Zimmer bullet PL+EN, languages PL+EN) |
| adriana-gusciora-pl | `archiwum/CHANGELOG-2026-05-03.md` | **Nowy** — ten plik |

### Lokalnie wygenerowane (gitignored)

- `cv-analityk/cv/AG_Delivery Manager.pdf` (3.7 MB, 2 strony A4)
- `cv-analityk/cv/AG_Lead_PM_DWH_BI_EN.pdf` (3.7 MB)
- `cv-analityk/cv/AG_Executive_Data_Analyst_FinTech_EN.pdf` (3.7 MB)
- `cv-analityk/cv/AG_Process_Business_PM_EN.pdf` (3.7 MB)
- `cv-analityk/cv/AG_Process_Automation_Lead_PL.pdf` (3.8 MB)
- `cv-analityk/cv/AG_Power_Platform_Consultant_PL.pdf` (3.8 MB)
- `cv-analityk/cv/AG_PowerBI_Developer_PL.pdf` (3.8 MB)
- `cv-analityk/cv/AG_PowerBI_Solutions_Specialist_EN.pdf` (3.7 MB)

## Commits planowane

- cv-analityk: `fix: CV Delivery Manager + 7 tailored CV — content corrections, redesign generator, padding, languages`
- cv-deliverymanager: `fix: language levels (drop C1/A2) + Zimmer bullet sync with PDF`
- adriana-gusciora-pl: `docs: changelog 2026-05-03 — CV poprawki + nowy generator dopasowanych CV`

## Następne kroki

1. Adriana sprawdza nowe PDFy (8 plików) i daje feedback
2. W razie potrzeby — kolejne iteracje na content
3. Przy zaakceptowanej formie — można usunąć stary `generate-tailored-cvs.js` (duplikuje funkcjonalność z `-redesign.js`)
