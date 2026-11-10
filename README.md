# Bild-Collage für Publikationen

Eine einzelne HTML-Seite (`index.html`), die Bilder zu einer Collage zusammensetzt, wie sie in chemischen Fachartikeln üblich ist. Das Ergebnis kann direkt in Word eingefügt werden. Es gibt keinen Server und keine Installation, und die Bilder verlassen den Rechner nicht.

## Nutzung

- Lokal: `index.html` doppelklicken (Chrome, Edge oder Firefox).
- Online: über GitHub Pages hosten (siehe unten).

1. Bilder hineinziehen. Sie werden nach Dateiname sortiert (natürliche Sortierung: `P1_T2_U10` kommt nach `P1_T2_U9`).
   Die Reihenfolge lässt sich per Drag & Drop ändern. „Leerfeld +“ fügt eine leere Zelle ein.
2. Raster wählen (Voreinstellung oder freie Eingabe für Zeilen × Spalten), dazu zeilen- oder spaltenweise Nummerierung.
3. Seite bzw. Breite wählen: **A4 hoch** (16 cm), **A4 quer** (24,7 cm), Journal einspaltig (8,5 cm) oder zweispaltig (17 cm).
   Mit **max. Höhe** wird die Breite automatisch reduziert, wenn die Collage sonst nicht auf die Seite passt.
   Die Vorlage setzt die max. Höhe passend (hoch 22 cm, quer 14 cm), damit Platz für die Bildunterschrift bleibt.
4. Optional: Zuschnitt (Seitenverhältnis, Zoom, Position), Panel-Buchstaben, neuer Maßstabsbalken, Zeilen- und Spaltentitel.
5. **Collage exportieren**: Die Datei bekommt eine DPI-Angabe, damit Word sie direkt in der richtigen Größe einfügt.

Die Einstellungen werden im Browser gespeichert (localStorage), die Bilder nicht.

## Voreinstellungen (orientiert an ACS/RSC/Elsevier)

| Parameter | Wert |
|---|---|
| Breite | Word A4 hoch 16 cm, A4 quer 24,7 cm (Standardränder 2,5 cm); Journal 8,5 cm bzw. 17 cm |
| Auflösung | 600 dpi (Fotos: mind. 300 dpi, kombinierte Grafiken: 600 dpi) |
| Schrift | Arial/Helvetica, Panel-Buchstaben 10 pt fett, Maßstab 8 pt (im Druck nie unter ca. 6 pt) |
| Panel-Buchstaben | (a), (b), … oben links |
| Format | JPEG 95 % (PNG optional, aber 5–10× größer) |

## Querformat-Seite mit Hochformat-Fotos

Mit der Schnellvorlage **„Seite A4 quer · Fotos hochkant“** wird A4 quer eingestellt, die Bilder werden auf 3:4 zugeschnitten
und das Raster automatisch gewählt (siehe unten).

Die Vorlage schaltet **„Raster automatisch an Bildanzahl anpassen“** ein: Alle Bilder kommen auf die Seite,
und das Raster wird so gewählt, dass die Panels möglichst groß bleiben. Gerechnet mit 3:4-Zuschnitt, 24,7 cm Breite und 14 cm max. Höhe:

| Bilder | Raster | Panelgröße | Lesbarkeit |
|---|---|---|---|
| 5 | 2 × 3 | 5,2 × 6,9 cm | gut |
| 10 | 2 × 5 | 4,9 × 6,5 cm | gut |
| 20 | 3 × 7 | 3,4 × 4,6 cm | Hinweis (gelb) |
| 30 | 4 × 8 | 2,6 × 3,4 cm | Hinweis (gelb) |
| 40 | 4 × 10 | 2,4 × 3,2 cm | Warnung (rot) |

Die Lesbarkeitswarnung richtet sich nach der kurzen Seite eines Panels: unter 3,5 cm ein gelber Hinweis,
unter 2,5 cm eine rote Warnung. Das ist eine Faustregel für gedruckte Fotos, keine Journal-Vorgabe.
Wer das Raster von Hand ändert, schaltet die automatische Anpassung damit aus.

Zwei Wege zum Hochformat:
- **Zuschnitt 3:4 / 2:3 / 1:2** (empfohlen): Die volle Bildhöhe bleibt erhalten, links und rechts wird beschnitten.
  Mit „Position horizontal“ wählst du den Ausschnitt. Der eingebrannte Maßstab rechts unten wird dabei meist angeschnitten,
  deshalb den Balken neu einblenden.
- **Drehen um 90°**: Das ganze Bild bleibt erhalten, aber der eingebrannte Maßstab steht dann senkrecht.
  Für eine Publikation ist das nur mit Bildern ohne eingebrannten Balken sinnvoll.

## HEIC/HEIF (iPhone-Fotos)

HEIC-Dateien können direkt hineingezogen werden:
- **Safari** (Mac, iPhone) liest HEIC selbst.
- **Chrome, Edge, Firefox:** Die Seite lädt bei Bedarf den Decoder [heic-to](https://github.com/hoppergee/heic-to)
  (basiert auf libheif) und wandelt die Fotos lokal im Browser um. Es wird nichts hochgeladen.
  Der Decoder liegt in `vendor/heic-to.js` und funktioniert damit auch offline, wenn der ganze Ordner heruntergeladen wurde.
  Fehlt die Datei (z. B. wenn nur `index.html` heruntergeladen wurde), wird er von cdn.jsdelivr.net geladen. Dafür ist Internet nötig.

Lizenz: heic-to und libheif stehen unter der LGPL-3.0 (siehe `vendor/heic-to.LICENSE`). Die Datei ist unverändert übernommen (Version 1.6.7).

## Kalibrierung des Maßstabsbalkens

Der Wert gilt pro Pixel des **Originalbildes**. Er hängt nur von Objektiv und Vergrößerung ab, nicht vom Zuschnitt.
Für die getesteten 2000 × 1498 px Mikroskopbilder: Der eingebrannte 0,5-mm-Balken ist ca. 334 px lang, also **1,497 µm/px**.
Neu bestimmen: Länge des eingebrannten Balkens in Pixeln messen (z. B. in ImageJ/Fiji oder Paint), dann µm ÷ px rechnen.

## Wichtig für Word

Word komprimiert eingefügte Bilder standardmäßig auf ca. 220 ppi. Abschalten unter
*Datei → Optionen → Erweitert → Bildgröße und -qualität*: „Bilder in Datei nicht komprimieren“ aktivieren
und „Standardauflösung“ auf „High Fidelity“ stellen.

## Hosting über GitHub Pages

1. Neues Repository anlegen und `index.html` hochladen (Root oder Ordner `docs/`).
2. *Settings → Pages → Build and deployment → Source: Deploy from a branch*, Branch `main`, Ordner `/ (root)` bzw. `/docs` wählen.
3. Nach ca. 1 Minute ist die Seite unter `https://<benutzername>.github.io/<repo>/` erreichbar.

Hinweis: GitHub Pages ist bei kostenlosen Accounts nur für **öffentliche** Repositories verfügbar. Die Seite ist dann
öffentlich, die Bilder aber nicht, weil sie nur lokal im Browser verarbeitet werden.

## Bekannte Grenzen

- TIFF können Chrome, Edge und Firefox nicht lesen. Vorher in JPG/PNG umwandeln.
- HEIC-Umwandlung dauert ca. 2–3 s pro iPhone-Foto (12 MP) und braucht viel Arbeitsspeicher. Bei sehr vielen Fotos lieber in Etappen laden.
- Ein im Bild eingebrannter Maßstab skaliert mit. In kleinen Panels wird seine Schrift unleserlich.
  Dann besser Bilder ohne eingebrannten Balken exportieren und den Balken hier einblenden.
- Ab dem 27. Panel geht die Beschriftung mit (aa), (ab), … weiter.

## Unterstützen

Das Tool ist kostenlos. Wenn es dir Zeit spart, kannst du mir über den Button „☕ Kaffee spendieren“ oben rechts
einen Kaffee auf Ko-fi spendieren. Der Button ist ein einfacher Link: Es werden keine Skripte von Ko-fi geladen,
und erst beim Klick wird ko-fi.com geöffnet.
