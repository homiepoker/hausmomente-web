# Hausmomente Web
Installierbares, lokal speicherndes Bautagebuch für iPhone und Android. Erste Testversion; noch nicht auf einem Gerät oder in einem Browser getestet.

## Funktionen
- Tagebucheinträge erstellen, bearbeiten, löschen und durchsuchen; Filter nach Gewerk.
- Bis zu 8 Fotos je Eintrag, auf maximal 1600 Pixel verkleinert.
- Aufgaben, 8 manuell abhakbare Bauphasen, Projektname und Ort.
- IndexedDB-Speicherung auf dem Gerät. Keine Konten, keine Synchronisierung.
- JSON-Sicherung einschließlich Fotos, validierter Import nach Bestätigung.
- Service Worker für Offline-Nutzung, App-Manifest und PNG-Symbole.
- Keine externen Bibliotheken, Analyse-Skripte oder kostenpflichtigen APIs.

## GitHub Pages
Dieses öffentliche Repository enthält ausschließlich die Web-App. Das native iPhone-Projekt bleibt im separaten privaten Repository.
In Settings > Pages: Deploy from a branch, main, /(root), Save. Die Website über die dort angezeigte HTTPS-Adresse öffnen.
Die Dateien benötigen keinen Build und keinen eigenen Actions-Workflow.

## iPhone
In Safari öffnen, Teilen > Zum Home-Bildschirm > Als Web-App öffnen > Hinzufügen. Danach immer über dasselbe App-Symbol verwenden. Im Tab Projekt wird der Offline-Status angezeigt. Nach dem ersten vollständigen Laden die App online erneut öffnen und erst danach offline testen.

## Daten und Grenzen
Daten bleiben ausschließlich im lokalen Browser-/App-Speicher. Es gibt keine automatische Sicherung oder gemeinsame Nutzung. Safari und Home-Bildschirm-App können getrennte Speicher haben.
Regelmäßig eine Sicherung exportieren und außerhalb der App ablegen. Beim Löschen von Website-Daten, App-Daten oder bei automatischer Speicherbereinigung können Einträge verloren gehen.
Das Löschen der Website-Dateien auf GitHub ist keine Datensicherung.
JSON-Sicherungen enthalten private Daten und dürfen nicht ins öffentliche Repository hochgeladen werden.
Import akzeptiert nur das Web-Format schema=1, maximal 100 MB. Native iPhone-Sicherungen werden noch nicht importiert.
Viele Fotos können hohen Speicherbedarf verursachen. Originalfotos separat aufbewahren.
Kein Passwortschutz, keine Verschlüsselung durch die App; Zugriff erfolgt über das entsperrte Gerät.
GitHub erhält übliche Anfragen für die statischen App-Dateien; Tagebuchinhalte werden von dieser App nicht versendet.
Ein späterer kommerzieller Dienst benötigt eine erneute Hosting- und Datenschutzprüfung.

## Prüfung vom 16. November 2026
Erfolgreich geprüft: JavaScript-Syntax der App und des Service Workers, JSON-Backup-Roundtrip, Ablehnung unmöglicher Datumswerte, doppelter Eintrags-IDs, unerlaubter Foto-URLs, fremder Schema-Versionen und falscher Aufgabentypen.
Noch offen: Browser-/iPhone-Test, IndexedDB-Verhalten, Fotos, installierter Offline-Start, Export/Import über die iOS-Dateien-App und visuelle Prüfung. Eine lokale Ausführungsumgebung stand beim Erstellen nicht zur Verfügung.

### Abnahme auf dem Gerät
1. Testeintrag mit Umlauten, Notizen und Foto erstellen, bearbeiten, App schließen und wieder öffnen.
2. Aufgabe und Bauphase abhaken; Zustand nach Neustart prüfen.
3. Sicherung exportieren, Testdaten ändern, Sicherung importieren und vergleichen.
4. Ungültige JSON-Datei importieren: vorhandene Daten müssen erhalten bleiben.
5. Als Home-Bildschirm-App starten, online vollständig laden, erneut öffnen; dann im Flugmodus schließen und neu öffnen.
6. Zweites Fenster öffnen; nach einer Änderung im ersten darf eine veraltete Änderung im zweiten nicht still überschreiben.
7. Erst nach diesen Tests echte Baudaten erfassen.

## Updates
Bei Änderungen den Cache-Namen in sw.js erhöhen. Eine neue Version aktiviert sich, nachdem alle alten App-Fenster geschlossen wurden. Bestehende IndexedDB-Daten werden bei App-Updates nicht gelöscht.
