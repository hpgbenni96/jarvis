# Jarvis 1.0 – dein persönlicher Wissensraum

Eine eigenständige, kostenlose PWA: keine Installation von Entwicklerpaketen, keine API-Schlüssel, kein Server-Backend und kein kostenpflichtiges Abo erforderlich. Die App besteht aus bearbeitbarem HTML, CSS und JavaScript. Stand: 6. November 2026.

## Was funktioniert?

- Dashboard mit echten lokalen Zahlen: Karten, fällige Wiederholungen, gefestigte Begriffe und heutige Übungen.
- Lernbegriffe erstellen, bearbeiten, löschen und durchsuchen; Kategorien und eigene Erklärungen.
- Stille Übungen: eigene Antwort formulieren, Musterantwort aufdecken, selbst bewerten.
- Wiederholung in 10 Minuten bei „Noch unsicher“, morgen bei „Mit Mühe“, nach 1/3/7/14/30 Tagen bei „Sicher erklärt“. Stufe 3–5 zählt als gefestigt. Das ist eine Selbsteinschätzung, keine objektive Wissensdiagnose.
- Sechs Modi: Wissen erweitern, Wissen wiederholen, Englisch, Rhetorik, Diskussion, Didaktik / Methodik. Kein Bereich „Alltag & Projekte“.
- Rollen und Prompts bearbeiten, eigene Modi hinzufügen oder löschen. Mindestens ein Modus bleibt erhalten.
- Startprompt für ChatGPT vorbereiten, prüfen und kopieren. Optional höchstens 20 fällige Karten einbeziehen.
- Lernjournal für manuell zurückübernommene Ergebnisse.
- Gerätestimmen auswählen, Vorschau anhören und Sprechtempo speichern.
- Großer Mikrofonknopf: Start nur nach Tippen und Hinweisbestätigung. Browser-Spracherkennung, wenn verfügbar; sonst Hinweis auf Tastaturdiktat. Keine Audiospeicherung in Jarvis.
- Lokale Speicherung, JSON-Backup und geprüfter Import mit Ersetzungsbestätigung.
- Homescreen-Manifest, App-Icons und Offline-App-Shell über Service Worker.

## Schnellstart am Computer

1. ZIP entpacken.
2. Terminal im entpackten Ordner `jarvis` öffnen.
3. Mit installiertem Python 3 starten:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

4. Im Browser `http://127.0.0.1:8765/` öffnen.
5. Beenden im Terminal mit Strg+C.

Nicht einfach `index.html` doppelklicken: JavaScript-Module und Offline-Funktionen brauchen HTTP/HTTPS. Python gehört auf manchen Computern nicht zur Standardausstattung. Für die Bereitstellung über GitHub brauchst du Python nicht.

Die Adresse `127.0.0.1` gilt nur auf dem Computer, auf dem der Server läuft. Sie ist keine iPhone-Adresse. Für die iPhone-Installation nutze die folgende HTTPS-Bereitstellung.

## Kostenlose Bereitstellung mit GitHub Pages

GitHub Pages ist derzeit für öffentliche Repositorys mit GitHub Free verfügbar. Du brauchst keine Kreditkarte, keine eigene Domain und keinen kostenpflichtigen Tarif. Konditionen eines fremden Anbieters können sich künftig ändern.

1. Auf https://github.com ein kostenloses Konto verwenden bzw. selbst anlegen.
2. Ein neues **öffentliches** Repository namens `jarvis` erstellen. Eine kostenpflichtige private Pages-Variante ist nicht nötig.
3. Über **Add file → Upload files** die App-Dateien aus dem entpackten Ordner hochladen. `index.html` muss direkt im Hauptverzeichnis liegen, nicht in einem zusätzlichen Unterordner.
4. Mindestens diese Dateien hochladen:
   - `index.html`, `style.css`, `app.js`, `core.js`
   - `sw.js`, `manifest.webmanifest`
   - `icon.svg`, `icon-192.png`, `icon-512.png`
   - `.nojekyll` (leere Datei; alternativ im Repository anlegen)
5. Änderungen mit **Commit changes** speichern.
6. **Settings → Pages → Build and deployment** öffnen.
7. Bei **Source**: **Deploy from a branch**; Branch `main`, Ordner `/(root)` wählen und speichern.
8. Warten, bis GitHub die Adresse anzeigt, üblicherweise `https://DEIN-NAME.github.io/jarvis/`. Diese angezeigte Adresse verwenden. Die Bereitstellung kann einige Minuten dauern.
9. HTTPS verwenden; falls verfügbar **Enforce HTTPS** aktivieren.
10. Die Adresse zuerst im Browser öffnen und kontrollieren, ob das Dashboard erscheint.

Der Quellcode und die Website sind dann öffentlich. Deine Lernkarten werden ausschließlich im jeweiligen Browser gespeichert und nicht ins Repository hochgeladen. **Keine Backup-Dateien, Journale oder vertraulichen Inhalte ins Repository laden.** Der Hostinganbieter verarbeitet normale Webanfragen. Jarvis selbst enthält keine Tracker, externen Schriften oder Analysedienste.

Diese Ausgabe enthält Quellcode und Anleitung, aber noch keine veröffentlichte Website und keine eingerichteten Drittanbieter-Konten.

## Auf dem iPhone installieren

1. Die fertige HTTPS-Adresse in **Safari** auf dem iPhone öffnen.
2. **Teilen → Zum Home-Bildschirm** wählen (gegebenenfalls unter „Mehr“ bzw. den Teilen-Aktionen suchen).
3. Falls angezeigt: **Als Web-App öffnen** aktivieren.
4. Name „Jarvis“ bestätigen und **Hinzufügen** wählen.
5. Jarvis vom Homescreen einmal online starten. Unter Einstellungen sollte „Offline-Version installiert“ erscheinen. Danach App erneut öffnen.
6. Mit einer Testkarte im Flugmodus prüfen: App öffnen, Karte anzeigen, stille Übung durchführen. ChatGPT und manche Sprachdienste bleiben onlineabhängig.

Safari und die installierte App können getrennte Speicher haben. Wenn Karten fehlen: im ursprünglichen Browser exportieren und in der Homescreen-App importieren. Auch ein anderer Hostname oder Repository-Pfad kann einen getrennten Datenbestand bedeuten; vor Umzügen sichern.

## Ein Gespräch führen

1. Unter „Gespräch“ einen Modus auswählen und bei Bedarf „Rolle bearbeiten“ öffnen.
2. Anliegen tippen oder per Mikrofon diktieren. Ohne unterstützte Browsererkennung die Diktierfunktion der iPhone-Tastatur nutzen.
3. Optional fällige Lernbegriffe einbeziehen; diese werden dann Teil des Texts für ChatGPT.
4. „Startprompt vorbereiten“, Text prüfen, „Prompt kopieren“ drücken.
5. „ChatGPT öffnen“ führt zu `https://chatgpt.com/`. iOS kann Safari oder die ChatGPT-App öffnen. Der Link erzwingt keinen bestimmten App-Start und startet keinen Sprachmodus.
6. Prompt in ChatGPT einfügen und absenden. Sprachgespräch dort manuell beginnen, soweit in deinem Konto verfügbar.
7. Zurück über den App-Umschalter oder das Jarvis-Homescreen-Symbol. Ergebnisse ins Journal kopieren und speichern; Begriffe als Karten ergänzen.

**Keine automatische Synchronisation:** Jarvis liest keine ChatGPT-Chats und bekommt keine Antworten zurück. Es gibt weder eine unsichtbare Einbettung noch Zugriff auf Apple Intelligence oder einen kostenlosen KI-Server. Die Qualität kommt aus dem gewählten ChatGPT-Angebot und deinem Rollenprompt. Für ChatGPT gelten eigene Verfügbarkeit und Nutzungslimits. Ein Jarvis-Abo oder API-Guthaben ist nicht nötig.

## Daten sichern und wiederherstellen

Einstellungen → **Backup exportieren** speichert eine JSON-Datei mit Karten, Rollen, Journal, Bewertungen und Stimmoptionen. iOS legt Downloads je nach Browserkonfiguration in „Dateien“ ab oder zeigt eine Speicher-/Teilen-Ansicht.

Einstellungen → **Backup importieren** → Datei wählen → Anzahl prüfen → Ersetzen bestätigen. Der Import ersetzt den gesamten aktuellen Stand; vorher exportieren. Ein beschädigtes oder unpassendes Backup wird abgelehnt. Die Dateien sind unverschlüsselt; entsprechend privat aufbewahren.

Lokale Speicherung ist kein garantiertes Backup: Browserdaten löschen, privater Modus, Speicherbereinigung, Neuinstallation oder Geräteverlust können die Daten entfernen. Jarvis meldet Schreibfehler und überschreibt beim Erkennen beschädigter Bestandsdaten diese nicht stillschweigend. In diesem Fall lassen sich die Rohdaten unter Einstellungen sichern. Bei Änderungen in einem zweiten Fenster wird Schreiben bis zum Neuladen gesperrt. Diese Sperre ist kein vollständiges Mehrbenutzer-System; möglichst nur ein Jarvis-Fenster gleichzeitig bearbeiten.

## Weiterentwickeln

- `index.html`: Grundgerüst und Navigation.
- `style.css`: Farben, Typografie, mobile Darstellung.
- `core.js`: Ausgangsmodi, Datenprüfung, Wiederholungslogik, Prompt-Erstellung.
- `app.js`: Bedienoberfläche, Speicher, Karten, Journal, Sprache und Backup.
- `sw.js`: Offline-Dateiliste und Cache-Version.
- `manifest.webmanifest`: Homescreen-Name, Farben und Icons.
- `tests/core.test.mjs`: ausführbare Tests ohne externe Pakete.

Neue Modi kannst du bereits in der Oberfläche ergänzen. Änderungen an den Ausgangsmodi in `core.js` betreffen nur neue Datenbestände; bestehende Rollen bleiben erhalten. Das schützt persönliche Anpassungen.

Bei Codeänderungen die Cache-Version in `sw.js` erhöhen, z. B. `jarvis-shell-v2` → `jarvis-shell-v3`. Alle geänderten Dateien auf denselben Host/Pfad hochladen. In Einstellungen nach Updates suchen, dann **alle** offenen Jarvis-Fenster schließen und erneut öffnen. Keine Browserdaten löschen, um Updates zu erzwingen. Die lokalen Karten bleiben bei einem normalen Update erhalten.

Für spätere Datenmodelländerungen explizite Migrationen schreiben: nicht einfach den Speicher-Schlüssel wechseln oder bestehende Daten mit Standardwerten ersetzen. Stimme und Spracheingabe sind Browserfunktionen; eine künftige echte KI-Sprachintegration wäre ein separates Projekt und darf nicht stillschweigend kostenpflichtige APIs aktivieren.

## Tests

Optional mit Node.js 20 oder neuer:

```sh
node tests/core.test.mjs
```

Keine Installation von npm-Paketen nötig. Ergebnisse und noch offene Gerätetests siehe `TESTBERICHT.md`.

## Offizielle Anleitungen

- GitHub Pages / kostenlose öffentliche Repositorys: https://docs.github.com/en/pages/getting-started-with-github-pages
- Veröffentlichungsquelle auswählen: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- Apple: Website als iPhone-Web-App: https://support.apple.com/guide/iphone/open-as-web-app-iphea86e5236/27/ios/27

Die Schritte beziehen sich auf die derzeitigen Oberflächen; Bezeichnungen können je nach Sprache und Betriebssystemversion variieren.
