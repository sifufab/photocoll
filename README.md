# Bild-Collage für Publikationen

Eine einzelne HTML-Seite (`index.html`), die Bilder zu einer Collage zusammensetzt, wie sie in chemischen Fachartikeln üblich ist. Das Ergebnis kann direkt in Word eingefügt werden. Es gibt keinen Server und keine Installation, und die Bilder verlassen den Rechner nicht.

## Nutzung

- Lokal: `index.html` doppelklicken (Chrome, Edge oder Firefox).
- Online: über GitHub Pages hosten (siehe unten).

1. Bilder hineinziehen. Sie werden nach Dateiname sortiert (natürliche Sortierung: `P1_T2_U10` kommt nach `P1_T2_U9`).
   Die Reihenfolge lässt sich per Drag & Drop ändern. „Leerfeld +“ fügt eine leere Zelle ein.
2. Raster wählen (Voreinstellung oder freie Eingabe für Zeilen × Spalten), dazu zeilen- oder spaltenweise Nummerierung.
3. Breite festlegen: 8,5 cm (einspaltig, ACS/RSC) oder 17 cm (volle Textbreite).
   Mit **max. Höhe** wird die Breite automatisch reduziert, wenn die Collage sonst nicht auf die Seite passt.
4. Optional: Zuschnitt (Seitenverhältnis, Zoom, Position), Panel-Buchstaben, neuer Maßstabsbalken, Zeilen- und Spaltentitel.
5. **Collage exportieren**: Die Datei bekommt eine DPI-Angabe, damit Word sie direkt in der richtigen Größe einfügt.

Die Einstellungen werden im Browser gespeichert (localStorage), die Bilder nicht.

## Voreinstellungen (orientiert an ACS/RSC/Elsevier)

| Parameter | Wert |
|---|---|
| Breite | 8,5 cm bzw. 17 cm |
| Auflösung | 600 dpi (Fotos: mind. 300 dpi, kombinierte Grafiken: 600 dpi) |
| Schrift | Arial/Helvetica, Panel-Buchstaben 10 pt fett, Maßstab 8 pt (im Druck nie unter ca. 6 pt) |
| Panel-Buchstaben | (a), (b), … oben links |
| Format | JPEG 95 % (PNG optional, aber 5–10× größer) |

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
- Ein im Bild eingebrannter Maßstab skaliert mit. In kleinen Panels wird seine Schrift unleserlich.
  Dann besser Bilder ohne eingebrannten Balken exportieren und den Balken hier einblenden.
- Ab dem 27. Panel geht die Beschriftung mit (aa), (ab), … weiter.
