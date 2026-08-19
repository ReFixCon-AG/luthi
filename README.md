# Lüthi Aufzüge — Landingpage

Statische Landingpage (v2, Editorial-Depth-Layer) für https://www.lüthi-aufzüge.ch
(Punycode: `www.xn--lthi-aufzge-thbi.ch`).

## Deployment

Gehostet auf **Cloudflare Pages**, verbunden mit diesem GitHub-Repository.

**Jeder Push auf `main` veröffentlicht die Seite automatisch.** Es sind keine
Befehle, kein Build und kein Login bei Cloudflare nötig — Änderungen committen
und pushen genügt. Der Stand ist nach ein bis zwei Minuten live.

Es gibt keinen Build-Schritt: die Dateien werden so ausgeliefert, wie sie hier
im Repository liegen.

## Struktur

- `index.html` — Landingpage v2
- `support.js` — dc-runtime (generiert, nicht von Hand ändern)
- `vendor/` — React und ReactDOM, lokal statt von unpkg.com (siehe unten)
- `_ds/` — Design-System Nocturne
- `assets/` — Bilder
- `_headers` — Security- und Cache-Header für Cloudflare Pages

## Worauf beim Bearbeiten zu achten ist

**Meta-Tags stehen im `<head>`, nicht im `<helmet>`-Block.** Titel,
Beschreibung, Canonical-URL und die Open-Graph-Tags für Link-Vorschauen müssen
im echten `<head>` bleiben. WhatsApp, LinkedIn und Facebook führen kein
JavaScript aus — was erst zur Laufzeit eingehängt wird, sehen sie nicht.

**React wird lokal geladen.** `window.__resources` im `<head>` leitet die
unpkg.com-URLs auf `/vendor/` um. Ohne diese Umleitung wäre die Seite bei einem
CDN-Ausfall komplett leer. Der Block muss vor `support.js` stehen.

**Bilder vor dem Einchecken verkleinern.** `assets/` wird ungefiltert
ausgeliefert. Kameradateien mit mehreren MB gehören nicht ins Repository.

## Offene Punkte

- Alle Navigations- und CTA-Links zeigen auf `href="#"` und sind ohne Funktion.
- Es fehlen Kontaktangaben, Impressum und Datenschutzerklärung.
- Die Herkunft von `assets/lift-primary.jpg` ist nicht belegt (siehe Kommentar
  in `index.html`).
