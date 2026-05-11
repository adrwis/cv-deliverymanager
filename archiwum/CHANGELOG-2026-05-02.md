# Changelog 2026-05-02 — CV Delivery Manager redesign + 7 dopasowanych CV + nowe repo cv-deliverymanager

## Zakres
Sesja CV: przebudowa CV Delivery Manager FinTech wg 5 wytycznych Adriany, postawienie standalone GitHub Pages `adrwis/cv-deliverymanager` analogicznie do `cv-analityk`, wygenerowanie 7 dopasowanych CV pod konkretne oferty REK.

Plan operacyjny: `rek/plan-cv-deliverymanager-2026-05-02.md`.

## Zmiany w `cv-analityk` (sister repo)

### Generator CV `cv/generate-cv-delivery-manager.js`
- Header: dodane klikalne linki `mailto:Gusciora.Ada@gmail.com` + `linkedin.com/in/adriana-gu` z ikonkami SVG
- Imię z polskimi znakami: `Adriana Guściora` w obu wersjach (EN + PL)
- Zdjęcie `ada2.jpg` w obu wersjach (wcześniej tylko PL); ścieżka relatywna do `adriana-gusciora-pl/zdjecia/`
- Layout 2-kolumnowy (62% lewa: Experience+Education, 38% prawa: Skills+Certs+Languages)
- Każda firma (Trustwave, HSBC, Zimmer Biomet, ISS) dostała `★ Success story` w złotym bloku z konkretnym osiągnięciem
- Klauzula GDPR rozszerzona do wersji prawnej (EN: Personal Data Protection Act 10 May 2018 + GDPR 2016/679; PL: ustawa z 10 maja 2018 + RODO)
- Em dashes (—, –) usunięte zgodnie z feedbackiem (zamienione na przecinki / hyphen)
- Justify text + większy line-height (1.55) dla czytelności

### Nowy generator `cv/generate-tailored-cvs.js`
Parametryzowany generator 7 dopasowanych CV: 2 profile (Delivery Manager + Data Analyst), każdy w EN/PL, z opcjonalną kolejnością skill grup. Tworzy:

| # | Plik | Profil | Język | Pod ofertę |
|---|------|--------|:-----:|------------|
| 1 | `AG_Lead_PM_DWH_BI_EN.pdf` | DM | EN | Lead Project Manager (DWH/BI) |
| 2 | `AG_Executive_Data_Analyst_FinTech_EN.pdf` | Analyst | EN | GoMining Executive Data Analyst |
| 3 | `AG_Process_Business_PM_EN.pdf` | DM | EN | Hays Process/Business PM |
| 4 | `AG_Process_Automation_Lead_PL.pdf` | DM | PL | InPost Lead Automation |
| 5 | `AG_Power_Platform_Consultant_PL.pdf` | DM | PL | Budowa 2.0 Power Platform |
| 6 | `AG_PowerBI_Developer_PL.pdf` | Analyst | PL | Power BI Developer rescue IT |
| 7 | `AG_PowerBI_Solutions_Specialist_EN.pdf` | Analyst | EN | GP Strategies Power BI Specialist |

Dodano `.gitignore` z regułą `cv/*.pdf` — PDFy są tylko lokalne (nie commitowane).

## Nowe repo `cv-deliverymanager` (standalone GH Pages)

Lokalizacja: `C:/Users/adria/OneDrive/Dokumenty/GitHub/cv-deliverymanager/`. Struktura skopiowana z `cv-analityk` i dostosowana do Delivery Manager:

- `index.html` — hero z badge "Otwarta na nowe możliwości", tagline o Delivery Manager 8+ lat, fotem (110px), klikalne kontakty; 4 doświadczenia z bullets + ★ Success story; sekcja Skills (Delivery & PM jako highlighted, Finanse, BI & Reporting, Power Platform & AI z showcase 3 projektów); terminal claude-code; Wykształcenie z lightboxem dyplomów; Certyfikaty z lightboxem; Języki; Print + długi GDPR
- `cv-deliverymanager.css` — bazuje na cv-analityk.css z dodatkowym blokiem Success story (gold accent dla light/dark)
- `edukacja/` — skopiowane z cv-analityk (PRINCE2, Quality Manager, SQL, Power BI, Six Sigma, UX, Project Management, dyplomy)
- `ada2.jpg` — header photo
- `.github/workflows/deploy.yml` — auto-deploy do GH Pages
- Brak folderu `cv/` z PDFami (zgodnie z prośbą Adriany — strona ma tylko web CV)

Funkcjonalność:
- PL/EN toggle (data-i18n, translations object w JS)
- Light/dark theme toggle (data-mode atrybut)
- Lightbox certyfikatów (img + PDF iframe support)
- Responsywny mobile (320-768px) + print-friendly

## Ocena 7 ofert REK pod CV Delivery Manager

Wynik audytu (4 oferty — match dla CV DM, 3 oferty — lepiej pod CV Analityk):

| Stanowisko | Match | Aplikować jako |
|------------|:-----:|----------------|
| Hays Process/Business PM | 9/10 ★ | DM (B2B 180-250 PLN/h) |
| Budowa 2.0 Power Platform | 9/10 ★ | DM |
| Lead PM DWH/BI | 8/10 | DM |
| InPost Lead Automation | 7/10 | DM (gap PySpark do cover-letter) |
| GP Strategies Power BI Specialist | 6/10 | Analityk |
| GoMining Executive Data Analyst | 5/10 | Analityk (gap Python/Crypto) |
| Power BI Developer rescue IT | 4/10 | Analityk |

## Pliki

### Commit
- `cv-analityk/cv/generate-cv-delivery-manager.js` (modified)
- `cv-analityk/cv/generate-tailored-cvs.js` (new)
- `cv-analityk/.gitignore` (new — wyklucza PDFy)
- `rek/plan-cv-deliverymanager-2026-05-02.md` (new, status zamknięty)
- `cv-deliverymanager/*` (new repo: index.html, css, edukacja/, ada2.jpg, README, .github/workflows/deploy.yml, .gitignore)
- `archiwum/CHANGELOG-2026-05-02.md` (this file)

### Lokalnie (nie commitowane)
- 7 dopasowanych PDF + 2 bazowe PDF Delivery Manager w `cv-analityk/cv/` (.gitignore wyklucza)

## Następne kroki dla Adriany
1. ✅ `cd cv-deliverymanager && git init && git add . && git commit && git push` — DONE
2. ✅ GitHub → Settings → Pages → Source: GitHub Actions — DONE
3. Zaaplikować na top-3 oferty: Hays Process PM (★), Budowa 2.0 (★), Lead PM DWH/BI

## Iteracja #3 (2026-05-02 — editorial redesign + skrócenie treści, EN only)
Bazowe CV Delivery Manager (`cv-analityk/cv/AG_Delivery Manager_FinTech_EN.pdf`) — refined editorial layout zaprojektowany z pomocą skill `frontend-design`.

**Typografia:**
- Display + nagłówki: `Fraunces` (variable serif z italic accentami i `font-variation-settings: opsz 144`)
- Body: `Manrope` (clean modern sans)
- Inter porzucony jako "generic AI"

**Layout PDF — 2 strony, wymuszony page-break:**
- **Strona 1**: Header (foto 96px, name 26pt Fraunces, italic title, accent navy underline 72pt) → Summary (pull-quote, gradient bg) → 5 wierszy doświadczenia w 2-col grid (job lewa z navy left-border + period chip uppercase, success story prawa z gold left-border + Fraunces italic "✦ SUCCESS STORY" tag)
- **Strona 2** (`page-break-before: always`): Education full-width 2x2 grid → Skills 2-col grid 5 grup (serif italic labels, middot-separated tags) → Certifications 2-col z circle bullets (○ navy) → Languages 4-col elegant cards z Fraunces italic name → GDPR italic muted

**Skrócenie treści (radical):**
- Bullety: każda 1 linia (HSBC z 5→4, ISS pozostaje 4)
- Success stories: 1-2 zdania highlighting tooling
- Summary: 1 paragraf zamiast 4 zdań

**Padding/spacing:**
- exp-row gap 14→22px, padding-bottom 6→11px
- success-story padding 7→12px, line-height 1.45→1.6
- header padding-bottom 10→14px, gap 16→20px

**Generator:** w tej iteracji generuje tylko EN PDF (PL wyłączony — ochrona przed duplikacją; PL wraca jutro).

**Zmienione pliki:**
| Plik | Zmiana |
|------|--------|
| `cv-analityk/cv/generate-cv-delivery-manager.js` | Editorial CSS rewrite (Fraunces+Manrope), skrócone bullety+successy EN, IIFE tylko 'en' |

**Commits cv-analityk:**
- `e72f17a` — feat: editorial PDF redesign for CV Delivery Manager (2-page layout)
- `79b22cb` — feat: shorter bullets/success stories + more breathing space (CV DM EN only)
- `6f1f772` — feat: PDF layout - exp rows + bottom grid; drop margin optimization
- `d19899e` — fix: skill bar Budget→People cost allocation
- `5a4ca04` — feat: PDF generators - 12 content fixes + matrix rain SVG

**Commits cv-deliverymanager:**
- `9e78d3c` — fix: replace 'Zarządzanie budżetem' with 'Alokacja kosztów osobowych'
- `2563fa2` — fix: full-width skill bars in Power Platform & AI tile
- `1559e82` — feat: 12 content fixes + matrix rain in print + wider AI tile

**Pozostało na jutro (2026-05-03):**
- PL wersja bazowego CV Delivery Manager (zaaplikować nowy editorial layout do PL)
- Tailored 7 PDF (zaaplikować skrócenia + editorial layout)
- Sprawdzenie strony cv-deliverymanager.pl (na żywo) po Adriany weryfikacji

---

## Iteracja #2 (2026-05-02 — feedback Adriany, 12 poprawek)
- Tagline: "Zarządzałam zespołami do 15 osób i odpowiadałam za alokację kosztów personalnych dla projektów do 15 mln $"
- Trustwave bullet 1: "Analiza procesów finansowych w obszarze IT oraz przygotowywanie dashboardów: wysokopoziomowych dla CFO i dyrektorów finansowych oraz szczegółowych dla kierowników działowych"
- Usunięte "i planowaniu pojemności" z bullet o Power BI/Alteryx
- "Przeanalizowałam" → "Analizowałam" we wszystkich success stories
- HSBC: usunięte "release planning" i ", dokumentacji dla interesariuszy"
- HSBC bullet o Excel/PowerBI: "rentowność, raporty odchyleń, monitoring trendów" → "budżet, forecast"
- Depolonizacja PL-EN: spolszczone "delivery"→"realizacja", "burn rate"→"monitoring wydatków", "headcount"→"obsada etatowa", "deliverables"→"zadania projektowe", "stakeholder"→"interesariusz", "C-level"→"kadra zarządzająca", "P&L"→"rachunek zysków i strat", "end-to-end"→"kompleksowo", "toolset"→"zestaw narzędzi", "workflow"→"obieg/przepływ", "end userów"→"użytkowników końcowych"
- Usunięte "Roadmap, capacity, RAID" z skill bars
- Kafelek "Power Platform i AI" rozszerzony na pełną szerokość (2 kolumny) na stronie
- Drukuj CV (strona): snapshot canvas → background body → @media print z półprzezroczystymi kartami; po wydruku cleanup
- PDFy generowane: dodana funkcja `generateRainSVG()` produkująca statyczne SVG z numerkami w tle (kolor `rgba(30,58,110,opacity)`, opacity 0.32 × brightness × yFade); kafelki PDF z półprzezroczystym białym tłem (rgba 255,255,255,0.86)
- 9 PDFów zregenerowane lokalnie (2 bazowe Delivery Manager + 7 dopasowanych), każde z matrix rain w tle

Zmienione pliki:
- `cv-deliverymanager/index.html` + `cv-deliverymanager.css`
- `cv-analityk/cv/generate-cv-delivery-manager.js`
- `cv-analityk/cv/generate-tailored-cvs.js`

## Sources (weryfikacja klauzuli RODO EN extended)
- interviewme.pl/blog/klauzula-cv-po-angielsku
- livecareer.pl/cv/klauzula-cv-po-angielsku
- europajobs.pl/blog/klauzula-cv-po-angielsku-kompletny-przewodnik
- careersinpoland.com — GDPR consent examples
- apcinstytut.pl — GDPR-compliant recruitment
