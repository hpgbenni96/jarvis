# Jarvis 1.0 – Prüfbericht

Stand: 6. November 2026. Tests mit künstlichen Testdaten, keine persönlichen Lerninhalte. Das ausgelieferte Projekt startet ohne Beispielkarten und ohne erfundenen Fortschritt.

## Automatische Prüfungen: 18 bestanden

Die beiliegende Datei `tests/core.test.mjs` wurde in der vorhandenen Node-JavaScript-Umgebung ausgeführt. Sie lässt sich mit Node.js 20+ erneut ausführen; keine zusätzlichen Pakete nötig.

1. Genau sechs Ausgangsmodi, kein „Alltag & Projekte“, leere Lernstatistik.
2. JSON-Export/Import-Rundlauf erhält alle Daten im Datenmodell.
3. Nicht unterstützte Backup-Version abgelehnt.
4. Fehlende Backup-Struktur abgelehnt.
5. Doppelte Karten-IDs abgelehnt.
6. Doppelte Modus-IDs abgelehnt.
7. Ungültige Stufen, Zeitwerte und leere/ungültige Inhalte abgelehnt.
8. Ungültiges Sprechtempo abgelehnt.
9. Ungültige Lernbewertungen abgelehnt.
10. Erfolgreiche Wiederholungen: Intervalle 1/3/7/14/30 Tage; Stufe höchstens 5.
11. Unsicher: Stufe 0 und nächste Wiederholung in 10 Minuten.
12. Mit Mühe: eine Stufe zurück, nie unter 0; nächste Wiederholung morgen.
13. Bewertung verändert die ursprüngliche Karte nicht.
14. Dashboard zählt Gesamtbestand, Fälligkeit, gefestigte Karten und heutige Bewertungen korrekt.
15. Prompt enthält gewählte Rolle, Auftrag, Thema und den fehlenden App-Zugriff.
16. Lernkartenkontext wird nur bei expliziter Übergabe eingebunden.
17. JavaScript-Syntax der Benutzeroberfläche.
18. JavaScript-Syntax des Service Workers.

Zusätzlich statisch geprüft: Manifest als gültiges JSON, vorhandene Offline-Assets, PNG-Abmessungen, relative Dateiverweise und ZIP-Integrität.

## Im Browser tatsächlich geprüft

- Startseite und Navigation laden.
- Lernkarte „Metakognition“ anlegen, speichern und nach Neuladen wiederfinden.
- Stille Übung starten, eigene Antwort tippen, Musterantwort aufdecken, „Sicher erklärt“ bewerten.
- Dashboard danach: 1 Lernbegriff, 0 fällig, 0 gefestigt, 1 heute geübt.
- Rollenbeschreibung bearbeiten; angepasste Rolle nach Neuladen im generierten Startprompt wiederfinden.
- Thema in Startprompt übernehmen; ChatGPT-Ziel zeigt auf die gewöhnliche HTTPS-Adresse, keine erfundene Deep-Link-Integration.
- Lernjournal speichern und nach Neuladen wiederfinden.
- Verfügbare Gerätestimmen anzeigen, „Anna“ auswählen und Speicherung nach Neuladen prüfen.
- Backup-Download erzeugt eine JSON-Datei.
- Offline-Registrierung meldet eine installierte Version.
- Mobiles Layout: 390 CSS-Pixel breit, Dokumentbreite ebenfalls 390 Pixel, kein horizontaler Überlauf. Vorschau in separater Bilddatei.
- Abschließende Browser-Konsole: keine erfassten Fehler.

Bei der Prüfung wurden ein fehlender optionaler Zugriff auf die Sprachfunktion, die Darstellung versteckter Schaltflächen, ein doppeltes Neuzeichnen nach Rollenänderungen und die Navigation/Überschrift auf schmalen Bildschirmen verbessert.

## Noch nicht vollständig nachgewiesen

- **Echtes iPhone:** Installation, App-Umschalter, Tastatur, Safe-Area und Safari-spezifische Speicherung müssen auf dem Gerät geprüft werden. Eine schmale Browseransicht ersetzt keinen iPhone-Test.
- **Dateiimport über die Oberfläche:** Der Export wurde heruntergeladen. Die automatisierte Dateiauswahl für den Rückimport ließ sich nicht bis zur bestätigten Wiederherstellung beobachten. Datenprüfung und JSON-Rundlauf bestehen automatisch; der vollständige Dateiauswahl-/Bestätigungsweg bleibt manuell zu testen.
- **Offline-Kaltstart:** Die Offline-Version ist installiert, ein vollständig netzloser Neustart auf dem iPhone ist noch zu prüfen.
- **Mikrofon und echte Audioausgabe:** Kein Audio aufgenommen; keine Mikrofonberechtigung erteilt. Stimmenauflistung und gespeicherte Auswahl geprüft, tatsächliche Wiedergabe/Spracherkennung geräteabhängig.
- **ChatGPT:** Kein Prompt abgesendet. Automatisches Öffnen einer bestimmten iOS-App und automatische Rücksynchronisation werden ausdrücklich nicht zugesagt.
- **GitHub Pages:** Anleitung anhand offizieller Dokumentation geprüft; keine Website veröffentlicht und kein Konto eingerichtet.
- Kartenlöschung, Moduslöschung, Speicherkontingentfehler, Zwei-Fenster-Konflikte und vollständiger Service-Worker-Updatewechsel sind implementiert, aber nicht jeweils durch einen Browser-End-to-End-Test bestätigt.

## Kurzer Abnahmetest auf deinem iPhone

1. Kostenlos bereitstellen, in Safari öffnen und zum Homescreen hinzufügen.
2. Testkarte anlegen, App schließen und erneut öffnen: Karte noch vorhanden?
3. Stille Übung durchführen: zählen Statistik und Fälligkeit richtig?
4. Backup in „Dateien“ speichern; eine weitere Testkarte anlegen; Backup importieren. Nach Ersetzungsbestätigung muss der alte Stand wieder da sein.
5. Ungültige JSON-Datei versuchen: Fehlermeldung, bisherige Daten unverändert?
6. App einmal online öffnen, schließen, Flugmodus einschalten und erneut starten. Bibliothek und Übungen müssen verfügbar sein.
7. Stimme auswählen und anhören. Mikrofon erst auf Druck testen, Erlaubnis verweigern und anschließend Tippen prüfen.
8. Prompt kopieren, ChatGPT öffnen, einfügen; zurück zu Jarvis wechseln und Ergebnis manuell speichern.
9. Vor Nutzung mit wichtigen Daten ein weiteres Backup anlegen.
