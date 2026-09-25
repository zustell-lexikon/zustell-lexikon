# CLAUDE.md — Digitales Zustell-Lexikon

Diese Datei ist die Übergabe-Dokumentation für Claude Code. Sie beschreibt den Stand des Projekts, die Vorgaben, alle bisher getroffenen Design-/Inhalts-Entscheidungen und was als Nächstes zu tun ist. Claude Code hat dieses Gespräch nicht gesehen — alles Wichtige steht hier.

---

## Projektübersicht

**Titel (offiziell, aus der Projektskizze):** „Erstellung eines internen Support-Wörterbuchs in verständlicher Sprache"
**Arbeitsname / sichtbarer Titel auf der Seite:** „Digitales Zustell-Lexikon"

Valentino Cioffo ist 18 Jahre alt und im 3. Lehrjahr Kaufmann/-frau EFZ bei der Schweizerischen Post CH AG, Distributionsgebiet Hinwil (Studbachstrasse 11, 8640 Hinwil). Das Projekt ist der Transferauftrag "Mein Projekt" des überbetrieblichen Kurses (ÜK) und wird auf der Konvink-Plattform dokumentiert.

Verantwortliche Person: Valentino Cioffo (valentino.cioffo@post.ch, 079 662 20 08)
Vorgesetzte/Ausbildnerin: Manuela Corgnale (manuela.corgnale@post.ch)
Gewählter Schwerpunkt: „Entwicklung von Content"

**Ziel des Projekts:** Ein internes, verständlich geschriebenes Nachschlagewerk (Glossar) für Post-Begriffe rund um Zustellung/Logistik, damit sich neue Mitarbeitende schneller zurechtfinden, Missverständnisse reduziert werden und das Büroteam weniger Rückfragen beantworten muss.

**Zielgruppen:** neue Mitarbeitende in Hinwil, bestehende Mitarbeitende/Logistiker, Lernende.

**Geplante Kategorien der Begriffe:** Logistik, System, Support (siehe „Bekannte Probleme" — Kategorie „System" ist aktuell noch leer).

**Wichtig zur Chronologie (siehe auch „Wichtige Entscheidungen"):** Der Transferauftrag wurde dem Jahrgang **Ende März** angekündigt/informiert — das ist der einzige legitime Bezug auf "März/April" im Text. Die tatsächliche Umsetzung als Webseite (dieser Code) hat **im September 2026** begonnen. Diese Unterscheidung ist bewusst so gewählt und darf nicht verändert oder vermischt werden.

---

## Anforderungen und Vorgaben

Aus den ÜK-Unterlagen (Transferauftrag 2 „Mein Projekt" und Beurteilungsbogen):

**Teilaufgaben des Transferauftrags:**
1. Ausgangslage beschreiben
2. Projektplanung / Projektskizze (als PDF hochladen)
3. Umsetzung dokumentieren
4. Projektergebnis dokumentieren
5. Reflexion — 4 Fragen, je 1 Erfolgsfaktor + 1 Stolperstein
6. Learnings — 3 begründete Aspekte
7. Einreichen mit Eigenständigkeitserklärung

**Bewertungskriterien (Beurteilungsbogen, je 0–3 Punkte):**
1. Beschreibung der Ausgangslage
2. Qualität der Planung
3. Beschreibung der Projektumsetzung
4. Beschreibung des Projektergebnisses
5. Reflexion
6. Learnings
7. Verständlichkeit
8. Datenschutz (u. a. korrekte Zitierweise, Bildrechte/Recht am eigenen Bild, klare Trennung Eigen- vs. Fremdleistung)

**Datenschutz-Vorgaben (explizit im Transferauftrag):**
- Keine Bilder von Personen ohne deren Einverständnis.
- Keine Kundennamen, keine Mitarbeiternamen (ausser der eigenen Person), keine internen Kennzahlen.
- Die Eigenständigkeitserklärung verlangt: selbstständig verfasst, Quellen angegeben, KI-Tool-Nutzung kritisch geprüft und deklariert.
- Zeitbudget: 20 Stunden im Betrieb. Verspätete Einreichung gibt Abzug. Ausdrücklicher Plagiat-Hinweis.

**Woraus das für die Webseite folgt:**
- Kein Foto mit erkennbaren, nicht einwilligenden Gesichtern ausser dem eigenen Porträt (mit Einverständnis).
- Keine sichtbaren Post-Logos/Wortmarken in verwendeten Fotos verwenden (Markenrecht/Bildrechte).
- Die Chronologie im Text muss wahrheitsgetreu bleiben (siehe oben) — sonst Risiko bei Kriterium 8.

---

## Technik

- **Reine Frontend-Technik**, keine Build-Tools, kein Framework: HTML5, CSS3 (inline `<style>` im `<head>`), Vanilla JavaScript (inline `<script>` vor `</body>`).
- **Eine einzige HTML-Datei** enthält alles — Struktur, Styling, Logik, sowie alle Bilder als Base64-Data-URIs (kein separater `/images`-Ordner, keine externen `.css`/`.js`-Dateien).
- Einzige externe Ressource: **Google Fonts** (`Fraunces` für Überschriften, `Inter` für Fliesstext), per `<link>` geladen.
- Kein Server, keine Datenbank, kein Login — rein statische Seite.
- **Hosting:** GitHub Pages, unter einer Organisation (siehe „Aktueller Stand").
- **Nicht verwendet / nicht nötig:** React, Vue, Tailwind, Bootstrap, npm/Build-Pipeline, Backend jeglicher Art. Bewusst so gehalten, damit die Seite in einem einzigen Schritt (Datei hochladen) veröffentlicht werden kann und im ÜK leicht erklärbar bleibt.
- Für Bild-/QR-Bearbeitung wurden während der Entwicklung Python-Tools (Pillow/PIL für Transparenz, `qrcode`-Bibliothek für den QR-Code, Playwright für automatisierte Screenshot-/PDF-Tests) verwendet — das sind reine Entwicklungswerkzeuge, sie sind **nicht** Teil der ausgelieferten Webseite und hinterlassen keine Spuren im HTML ausser dem fertigen Bild-Base64 bzw. dem fertigen QR-Code-Bild.

---

## Dateistruktur

| Datei | Zweck |
|---|---|
| `zustell-lexikon-offiziell.html` | **Die aktuelle, einzige echte Projektdatei.** Vollständige Webseite (HTML+CSS+JS+Bilder als Base64) — hier arbeitet Claude Code ausschliesslich weiter. ~1,6 MB, davon der grösste Teil Bild-Daten. |
| `zustell-lexikon.html` | **Veraltet / überholt.** Ein früherer Entwurf vor dem grossen Redesign (~318 KB). Nur zur Historie aufbewahrt — **nicht** weiterverwenden, nicht damit verwechseln. |
| `Projektskizze_Zustell-Lexikon.docx` | Projektskizze (Word) für die ÜK-Dokumentation — Ausgangslage, Ziele, Phasenplan, Ressourcen, Projektorganisation. Kein Code, aber inhaltlich relevant für die Doku auf Konvink. |
| `Projektplanung_Zustell-Lexikon.docx` | Ergänzende Projektplanung (Word). |
| `Projektplanung_Zustell-Lexikon_Monate.docx` | Projektplanung nach Monaten gegliedert (Word). |

Es gibt aktuell **keinen Ordner für Bilder** — alle Bilder (Favicon, Hintergrundfoto, Porträtfoto, QR-Code) sind direkt als `data:image/...;base64,...` im HTML eingebettet.

---

## Design-Entscheidungen

**Farben (CSS-Variablen in `:root`):**
```css
--ink: #1c1f22;          /* Haupttextfarbe, fast Schwarz */
--paper: #f7f7f5;        /* Seitenhintergrund */
--panel: #ffffff;        /* Karten/Panels */
--line: #e4e3df;         /* Trennlinien */
--yellow: #ffcc00;       /* Post-Gelb, Hauptakzent */
--yellow-deep: #e0ad00;  /* dunkleres Gelb für Hover/Kontrast */
--yellow-soft: #fff6d9;  /* helles Gelb für Flächen */
--muted: #6b6f76;        /* gedämpfter Grauton für Nebentext */
--grey-bg: #f1f1ef;      /* helle Graufläche */
--accent: #ffcc00;
--accent-ink: #1c1f22;
--radius-sm: 8px;
--radius-md: 14px;
--radius-lg: 18px;
--shadow-sm: 0 1px 3px rgba(20,20,18,0.06), 0 1px 2px rgba(20,20,18,0.04);
--shadow-md: 0 6px 20px rgba(20,20,18,0.08);
--space-1: 8px;  --space-2: 16px; --space-3: 24px; --space-4: 40px; --space-5: 64px;
--font-head: 'Fraunces', Georgia, 'Times New Roman', serif;
--font-body: 'Inter', 'Helvetica Neue', Helvetica, Arial, sans-serif;
```

**Kategorie-Farben** (Labels für Logistik/System/Support):
```css
.cat-label.logistik { background:#fff1cc; color:#7a5b00; }
.cat-label.system   { background:#e4eefb; color:#1f4e79; }
.cat-label.support  { background:#eae7fb; color:#4a3b8a; }
```

**Schriften:** Überschriften in `Fraunces` (Serif, wirkt hochwertig/redaktionell), Fliesstext in `Inter` (Sans-Serif, sehr gut lesbar). Beide über Google Fonts geladen.

**Layout / Navigation:**
- Eine SPA-artige Struktur: 4 Hauptbereiche laufen in einem durchgehenden Scroll-Container (`#scrollpage`): Home, Lexikon, Kategorien, Über das Projekt.
- Zusätzlich 5 „Overlay"-Vollbild-Ansichten, die den Scrollbereich ausblenden: die 3 Kategorie-Detailseiten (`cat-logistik`, `cat-system`, `cat-support`), die Porträt-/Über-mich-Seite (`portrait`) und die Suchergebnis-Detailseite (`result`).
- Navigation läuft über Hash-Routing (`#lexikon`, `#kategorien`, …) mit `history.pushState`/`popstate`, sodass Links direkt teilbar/verlinkbar sind. Fest mit try/catch abgesichert (siehe „Bekannte Probleme" → iOS-Bug, ist bereits behoben).
- **Navbar ist transparent** (`background: transparent; border-bottom: none;`), schwebt über dem Hero-Bild auf der Startseite. Das Logo/Wortmarke „Zustell-Lexikon" oben links wurde auf Wunsch entfernt (CSS-Klasse `.brand` bleibt im Code, wird aber nicht mehr im HTML verwendet).
- Aktiver Menüpunkt bekommt eine „Pillen"-Hervorhebung: `.nav-links a.active { background: rgba(255,255,255,0.85); box-shadow: var(--shadow-sm); }`.
- **Mobile Navigation (≤800px):** Hamburger-Button (`#navBurger`), öffnet ein aufklappendes Menü (`.nav-links.open`) mit weissem Hintergrund. Menü schliesst sich automatisch nach Klick auf einen Link.

**Hintergrundbild-Konzept („Idee 1", vom Nutzer ausdrücklich als „fröhlich" gewünscht und bestätigt):**
- Auf der **Startseite** ist das Luftaufnahme-Foto des Paketzentrums Härkingen (vom Nutzer selbst fotografiert) als fixer Hintergrund voll sichtbar (`.site-bg`, `position: fixed`, `z-index: -2`), leicht mit `.site-bg-tint` überlagert für Textlesbarkeit.
- Auf **allen anderen Seiten/Overlays** liegt eine fast-weisse, halbtransparente Fläche darüber (`rgba(247,247,245,0.94)`), sodass das Foto nur noch ganz schwach als „Wasserzeichen" (~4–8 %) durchschimmert — Text bleibt voll lesbar, aber die Bildatmosphäre der Startseite bleibt spürbar.
- Dies wurde bewusst so gewählt, nachdem eine frühere Variante („Bild nur auf Startseite, sonst reines Weiss") vom Nutzer ausdrücklich abgelehnt wurde.

**Stilrichtung insgesamt:** freundlich, hell, „Post-Gelb" als Wiedererkennungsfarbe, redaktionell/hochwertig wirkende Serifen-Überschriften kombiniert mit klarer, gut lesbarer Sans-Serif — bewusst kein reines Corporate-Blau-Weiss, sondern etwas persönlicher/wärmer, weil die Zielgruppe „neue Mitarbeitende" sich willkommen fühlen soll.

**Favicon:** aktuelle Version ist ein vom Nutzer hochgeladenes gelbes Rundicon (Buch + Zustellfahrzeug-Symbol), bei dem der ursprünglich weisse Hintergrund per Bildbearbeitung vollständig transparent gemacht wurde (nicht schwarz, nicht weiss — echte Transparenz).

**Barrierefreiheit (Accessibility):**
- „Zum Inhalt springen"-Skip-Link als erstes Element im `<body>`.
- Sichtbare `:focus-visible`-Umrandung (gelb) auf Links, Buttons, Inputs, Karten.
- `role="img"` + `aria-label` auf den Hintergrund- und Porträtbildern.
- `aria-label` auf beiden Suchfeldern.
- Tastaturbedienung (Enter/Space) auch für klickbare `<div>`-Elemente (z. B. Avatar/Name in der Byline).

**Druckansicht:** eigenes `@media print`-Stylesheet, das Navigation/Suche/Footer ausblendet und die vier Hauptbereiche auf separate Druckseiten verteilt (`break-after: page`), damit ein Ausdruck wie „Startseite / Lexikon / Kategorien / Über das Projekt" auf vier getrennten Blättern erscheint statt als eine lange Seite.

**SEO/Sharing:** `<meta name="description">`, Open-Graph- und Twitter-Card-Tags im `<head>` sind gesetzt, falls die Seite einmal geteilt/verlinkt wird.

---

## Aktueller Stand

- Die Seite ist **live** unter `https://zustell-lexikon.github.io` (GitHub Pages, Organisation `zustell-lexikon`, Repository `zustell-lexikon.github.io`, Datei im Repo heisst `index.html`).
- Der GitHub-Workflow ist aktuell **rein manuell**: Datei lokal exportieren → in GitHub hochladen → sicherstellen, dass sie `index.html` heisst → committen. Es gibt **kein** automatisches Deployment/CI.
- Das Repository ist **öffentlich** (auf dem kostenlosen GitHub-Tier ist das für GitHub Pages nötig) — der Nutzer wollte ursprünglich einen internen/nur-mit-Link-Zugriff, das ist mit dem Gratis-Tier von GitHub Pages so nicht möglich und wurde ihm entsprechend erklärt.
- Struktur und Design sind laut Nutzer-Feedback in einem guten, „fröhlichen" Zustand (Idee-1-Hintergrundkonzept wurde ausdrücklich bestätigt).
- Mobile Darstellung und Navigation funktionieren (Hamburger-Menü + iOS-Crash-Bug behoben, siehe unten).
- **Inhalt ist bewusst noch Platzhalter**: aktuell genau 6 Lexikon-Einträge (PLZ, Avisierung, Tourenplan, RX/Rollboxen, Retoure — alle Kategorie „Logistik" — sowie Nachnahme, Kategorie „Support"). Kategorie „System" hat **noch keine** Einträge. Der Nutzer hat ausdrücklich gesagt, dass echter Inhalt erst zum Schluss eingepflegt wird (nach Gesprächen mit den Fachbereichen Support/Logistik/System).

---

## Offene Aufgaben

Reihenfolge = empfohlene Bearbeitungsreihenfolge:

1. [x] **QR-Code aus dem Footer entfernt** — zeigte auf die alte private Claude-Artifact-URL statt auf die Live-Seite. Statt die URL zu korrigieren, wurde der QR-Code auf Wunsch ganz entfernt (Footer zeigt jetzt nur noch Claim + Copyright). Der zugehörige, jetzt ungenutzte `.footer-qr`-CSS-Block wurde ebenfalls entfernt.
2. [ ] **Echten Lexikon-Inhalt einpflegen** — Begriffe aus den drei geplanten Fachbereichs-Gesprächen (Support, Logistik, System) sammeln und ins `lexikon`-Array im `<script>` eintragen. Kategorie „System" ist komplett leer und braucht als Erstes Inhalt.
3. [ ] **Bildrechte/Datenschutz für neue Fotos prüfen**, sobald weitere Bilder hinzukommen (keine erkennbaren, nicht einwilligenden Personen; keine Post-Logos in eigenen Fotos, falls das markenrechtlich relevant ist — im Zweifel bei der Ausbildnerin nachfragen).
4. [ ] **Totes/unbenutztes CSS aufräumen** (niedrige Priorität): `.brand`, `.brand .mark`, `.hero-photo`, `.hero-shape`, `.hero-illustration` sind definiert, werden aber nicht mehr sichtbar verwendet — könnten entfernt werden, sobald das Design final steht.
5. [ ] **Automatisiertes Deployment prüfen** (optional): Falls gewünscht, könnte ein einfacher GitHub-Actions-Workflow das manuelle Umbenennen zu `index.html` überflüssig machen — aktuell nicht eingerichtet, nicht dringend.
6. [ ] **Für die Konvink-Dokumentation**: Screenshots/Reflexion/Learnings gemäss Transferauftrag-Teilaufgaben 3–6 verfassen (ausserhalb dieser HTML-Datei, aber Teil der Gesamtabgabe).

---

## Bekannte Probleme

- **Kategorie „System" ist leer** — es gibt aktuell keinen einzigen Lexikon-Eintrag mit `kategorie: "system"`. Die entsprechende Kategorie-Kachel/-Seite existiert im UI, zeigt aber „keine Einträge".
- **`zustell-lexikon.html` ist veraltet** — nicht versehentlich als aktuelle Datei verwenden.
- **Kein automatisches Deployment** — jede Änderung muss manuell in GitHub hochgeladen und die Datei erneut in `index.html` umbenannt werden (leicht fehleranfällig, siehe frühere Verwechslung mit `zustell-lexikon-offiziell (42).html`).
- **Öffentliches Repository**: Jeder mit dem Link kann die Seite sehen (kein Login, keine IP-Beschränkung) — das ist eine bewusst in Kauf genommene Einschränkung des kostenlosen GitHub-Pages-Tiers, kein Bug, aber sollte im Bewusstsein bleiben (Datenschutz-Kriterium 8: keine sensiblen/internen Daten einbauen, solange das Repo öffentlich ist).

---

## Wichtige Entscheidungen aus unserem Gespräch

Diese Punkte sind **bewusste, bereits diskutierte Entscheidungen** — bitte nicht ohne Rücksprache wieder rückgängig machen:

1. **Chronologie/Zeitangaben (sehr wichtig, Datenschutz-/Eigenständigkeits-Kriterium):** Der Text darf **nirgends** behaupten, das Projekt/die Webseite sei vor September 2026 entstanden oder „gestartet" worden. Die einzige zulässige Formulierung mit Bezug auf März/April ist: **„Ende März wurden wir konkret über den Transferauftrag «Mein Projekt» informiert"** — das bezieht sich nur auf die Ankündigung des Auftrags an den ganzen Jahrgang, nicht auf den Beginn der eigentlichen Umsetzung. Diese Unterscheidung wurde mehrfach im Gespräch explizit erarbeitet und darf nicht verwässert werden, auch nicht durch andere Formulierungen wie „erste Gedanken im März" o. Ä.
2. **Kein Logo/Wortmarke oben in der Navigation** — wurde auf ausdrücklichen Wunsch entfernt, nicht versehentlich vergessen.
3. **Hintergrundbild-Konzept „Idee 1"** (volles Bild auf Startseite, schwaches Wasserzeichen sonst) wurde nach Ablehnung einer Vorgängerversion bewusst gewählt und vom Nutzer als „sehr gut, soll eine fröhliche Seite sein" bestätigt — nicht ohne neuen Auftrag durch eine andere Variante ersetzen.
4. **Inhalt (echte Lexikon-Begriffe) wird bewusst zuletzt eingepflegt** — der Nutzer hat das ausdrücklich so gewollt („content kommt bewusst am Schluss"), das ist kein vergessener Punkt.
5. **GitHub Pages über eine Organisation, nicht über den privaten Account** — damit im Browser/Link nicht der persönliche GitHub-Benutzername des Nutzers erscheint, sondern der Projektname (`zustell-lexikon`).
6. **Druckversion trennt die vier Hauptbereiche auf vier separate Blätter** — war ein expliziter Wunsch, nicht Standardverhalten von `@media print`.
7. **Bei Rückmeldungen wie „das war vorher besser"** hat der Nutzer den Wunsch geäussert, dass frühere Versionen im Gespräch grundsätzlich wiederherstellbar sein sollen. In diesem Handoff gibt es dafür (noch) keine Versionsverwaltung im eigentlichen Sinne ausser einem `versions/`-Ordner mit einzelnen Backup-Kopien — falls Claude Code weiterarbeitet, wäre ein echtes Git-Repository mit Commit-Historie die sauberere Lösung dafür (aktuell ist der Arbeitsordner **kein** Git-Repository).
8. **Porträt-/Bio-Text sowie „Über das Projekt"-Text sind bewusst in Fliesstext geschrieben, nicht stichpunktartig** — der Nutzer hat das ausdrücklich so gewünscht, nachdem eine stichpunktartige Version nicht gefiel.

---

## Arbeitsweise

Für die Zusammenarbeit mit Claude Code (und damit der Nutzer die Änderungen im ÜK selbst erklären kann):

- Änderungen bitte **kurz und in einfachen Worten erklären** (was wurde geändert, wo im Code, und warum) — nicht nur der Diff, sondern eine kurze Begründung in ein bis zwei Sätzen.
- Der Nutzer ist Kaufmann-Lernender, kein Informatiker — technische Begriffe wenn möglich kurz einordnen (z. B. „Base64 = eine Methode, Bilder direkt als Text im Code zu speichern, damit keine separaten Bilddateien nötig sind").
- Vor grösseren strukturellen Änderungen (Layout, Navigation, Farbschema) lieber kurz nachfragen bzw. 2–3 Optionen vorschlagen, statt direkt umzusetzen — das hat sich im bisherigen Gespräch bewährt (siehe „Wichtige Entscheidungen" Punkt 3).
- Inhaltliche Änderungen an Kategorien/Begriffen sind unkritisch und können direkt umgesetzt werden, sobald der Nutzer den Inhalt liefert.
- Bei sicherheits-/datenschutzrelevanten Punkten (Bilder, Namen, Chronologie) im Zweifel lieber zurückfragen statt selbstständig zu entscheiden — diese Punkte fliessen direkt in die ÜK-Bewertung ein (Kriterium 8).

---

## Offene Fragen

Diese Punkte konnten aus dem bisherigen Gespräch nicht abschliessend geklärt werden — bitte den Nutzer bei Bedarf danach fragen:

1. Ist eine **echte Versionsverwaltung mit Git** gewünscht (Repository lokal mit `git init`, Commits statt manuellem Datei-Upload auf GitHub)? Das würde das manuelle Umbenennen zu `index.html` überflüssig machen und Änderungen nachvollziehbar machen.
2. Sind für die Kategorie „System" bereits Begriffe/Notizen aus einem Fachgespräch vorhanden, die nur noch nicht eingetragen wurden, oder muss das Gespräch mit dem Fachbereich erst noch stattfinden?
3. ~~Soll der QR-Code sofort auf die Live-URL korrigiert werden, oder soll das bewusst bis zum Schluss liegen bleiben?~~ **Geklärt:** Der Nutzer hat entschieden, den QR-Code stattdessen ganz zu entfernen (siehe „Offene Aufgaben" Punkt 1).
4. Gibt es eine Vorgabe der Post/des Lehrbetriebs, ob ein öffentlich zugängliches GitHub-Pages-Repository überhaupt zulässig ist, oder muss letztlich doch eine interne/zugriffsbeschränkte Lösung (z. B. via Post-internem Hosting) gefunden werden? Das wurde im Gespräch als Wunsch geäussert, aber mit den Grenzen des kostenlosen GitHub-Tiers nicht vollständig gelöst.
5. Ist die Verwendung des Luftaufnahme-Fotos vom Paketzentrum Härkingen (Nutzer-eigenes Foto) intern bei der Post freigegeben/abgeklärt, oder muss das noch offiziell bestätigt werden (relevant für Beurteilungskriterium 8)?
6. Soll `zustell-lexikon.html` (die alte, überholte Version) gelöscht oder archiviert werden, oder bewusst als Verlaufs-Nachweis aufbewahrt bleiben?
