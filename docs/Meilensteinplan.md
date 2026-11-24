# Meilensteinplan SkinSentry

24.11.2026 bis Abgabe am 05.02.2027.

| | Zeitraum | Ziel | Umfang |
|---|---|---|---|
| **M1 Fundament** | 24.11.–04.12. | App startet, Daten lassen sich lokal speichern | Projekt-Setup, CI |
| **M2 Prüfablauf ohne echte KI** | 05.12.–18.12. | UC-01 mit Dummy-Modell durchklickbar | F1, F2, F4, F5 |
| *Puffer* | 19.12.–03.01. | Feiertage, nichts eingeplant | |
| **M3 KI und Verlauf** | 04.01.–15.01. | Echte Einstufung, Hautstellen mit Historie: kleinste nützliche Version | F3, F6 |
| **M4 Bodymap und Erinnerungen** | 16.01.–24.01. | MVP vollständig, danach **Feature-Freeze** | F7, F8 |
| **M5 Abschluss** | 25.01.–05.02. | Getestete Abgabeversion | Test, Doku |
| **M6 Präsentation** | nach dem 05.02., Termin offen | Vorführbereite App | Demo, Folien |

## M1 Fundament (24.11.–04.12.)

- Compose-Projekt mit MVVM und drei Schichten, Theme nach Mock, Navigation
- Alle Texte auf Deutsch in `strings.xml`, keine festen Texte im Code
- Room-Schema, privater Fotospeicher, Ausschluss aus der Android-Datensicherung
- Schnittstelle für das KI-Modell mit Dummy
- CI mit Build, Lint und Tests; Branch `develop`
- KI: Datensatz festlegen (Lizenz prüfen), Aufteilung in Trainings- und Testdaten

**Fertig, wenn:**

- die App im Emulator läuft und die CI grün ist
- eine gespeicherte Hautstelle einen Neustart der App übersteht

## M2 Prüfablauf ohne echte KI (05.12.–18.12.)

- Eignungsprüfung und Arztverweis (UC-02, UC-07)
- CameraX mit Overlay, Kameraberechtigung samt Ablehnung (UC-03)
- Schärfe- und Belichtungsprüfung (UC-04)
- Ergebnis mit Empfehlung und Hinweis „keine Diagnose“ (UC-06)
- KI: erstes nachtrainiertes Modell, Export nach LiteRT

**Zu entscheiden: Wann wird die Körperstelle bei einer neuen Hautstelle angegeben?**

- **Weg A (Mock-Reihenfolge, Speichern erst am Ende) – Empfohlen:** Körperstelle wählen → Alter und Hauttyp → Foto → Ergebnis → Stelle bestätigen und speichern. Bei einem Abbruch wird nichts gespeichert.
- **Weg B (Konzept):** Alter, Hauttyp und Körperstelle in der Eignungsprüfung → Foto → Ergebnis → Stelle markieren (vorausgewählt) und speichern. Entspricht genau UC-01, weicht aber vom Mock ab.

In M2 und M3 ist die Auswahl eine Regionsliste, ab M4 die Bodymap.

**Anmerkung zu den Ausschlussgründen:** Der Mock nennt zusätzlich offene Wunden und durch Haare oder Tattoos verdeckte Haut. Diese Gründe werden als Ergänzung zu UC-02 umgesetzt, das Konzept bleibt unverändert.

**Fertig, wenn:**

- Ausschlussfälle und schlechte Fotos nie zu einer Einstufung führen
- ein Abbruch keine leere Hautstelle hinterlässt

## M3 KI und Verlauf (04.01.–15.01.)

- LiteRT einbinden, Schwellenwerte für drei Stufen, Verhalten bei Analysefehlern (UC-05)
- Modell evaluieren (vor allem Sensitivität bei Melanomen), Test mit Smartphone-Fotos, Grenzen dokumentieren
- Hautstelle mit Regionsliste anlegen (UC-08), Verlauf und Folgeprüfung (UC-09), Löschen (UC-12)

**Fertig, wenn:** UC-01 im Flugmodus auf einem echten Gerät durchläuft und das Ergebnis im Verlauf steht

## M4 Bodymap und Erinnerungen (16.01.–24.01.)

- Bodymap mit Vorder- und Rückseite auf Compose Canvas (UC-08, UC-09)
- Erinnerungen mit WorkManager, Ersatzanzeige ohne Benachrichtigungsrecht (UC-10, UC-11)
- Löschen entfernt auch die Erinnerung (UC-12)
- **Entscheidung am 20.01.:** Ist die Bodymap nicht absehbar fertig, bleibt es bei der Liste aus M3.

**Fertig, wenn:** UC-01 bis UC-12 umgesetzt sind, gegebenenfalls mit Liste statt Bodymap

## M5 Abschluss (25.01.–05.02.)

- Systemtest aller UCs, Barrierefreiheit (Schriftgröße, Kontrast, TalkBack)
- Kurzer Nutzertest, auch mit älteren Personen
- Fehlerbehebung, Doku, Release-APK
- Code-Stopp am 01.02., danach nur kritische Fehler
- Optional bei freier Zeit: englische Übersetzung, F9 (Arztsuche), F10 (UV-Index)

**Fertig, wenn:** die Release-APK alle UCs besteht, keine kritischen Fehler offen sind und die Abgabe eingereicht ist

## M6 Präsentation (nach dem 05.02.)

- Demo-Ablauf mit Testdaten, Ersatz-Video, Folien, Probedurchlauf

**Fertig, wenn:** der Demo-Ablauf einmal vollständig geprobt ist

## Aufteilung auf 4 Personen (Vorschlag)

| Strang | M1 | M2 | M3 | M4 | M5 |
|---|---|---|---|---|---|
| A: UI | Theme, Navigation | Eignung, Ergebnis | Verlauf | Bodymap | Barrierefreiheit |
| B: Kamera | CI, Projekt-Setup | Kamera, Bildqualität | Gerätetests | Bodymap | Systemtest |
| C: KI | Datensatz | Training, Export | Einbindung, Evaluation | Modell verbessern | Doku der Grenzen |
| D: Daten | Room, Fotospeicher | Speichern in UC-01 | UC-08, UC-12 | Erinnerungen | Release, Nutzertest |
