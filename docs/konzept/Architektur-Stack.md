# Architektur und Technologiestack (Draft)

> **Status:** Entwurf für das Team. Die Datenhaltung (Abschnitt 3.6) steht unter dem Vorbehalt, ob das Modul ein Backend verlangt. Die Alternative ist in Abschnitt 5 ausgearbeitet.

Die Architektur leitet sich aus den [Anwendungsfällen](UseCases.md) ab. Prägend sind drei Eigenschaften des MVP:

- Die App verarbeitet Hautfotos, also Gesundheitsdaten nach Art. 9 DSGVO.
- Der Hauptanwendungsfall hängt von Kamera und Bildanalyse ab.
- Das MVP sieht kein Nutzerkonto vor.

## 1. Komponenten

| Komponente | Aufgabe | Use Cases |
| --- | --- | --- |
| App und Benutzeroberfläche | Screens, Navigation, Zustandsverwaltung | alle |
| Kameraaufnahme | Vorschau, Overlay, Auslöser | UC-03 |
| Qualitätsprüfung | Schärfe, Licht und Ausschnitt bewerten | UC-04 |
| Eignungsprüfung | Selbstauskunft gegen Ausschlussregeln prüfen | UC-02, UC-07 |
| KI-Einstufung | Foto einer von drei Risikostufen zuordnen, Empfehlung ableiten | UC-05, UC-06 |
| Datenhaltung | Läsionen, Ergebnisse und Fotos speichern | UC-01, UC-08, UC-09 |
| Bodymap | Läsionen am Körper verorten und auswählen | UC-08, UC-09 |
| Erinnerungen | Termine planen und Benachrichtigungen auslösen | UC-10, UC-11 |

Die App folgt dem MVVM-Muster mit drei Schichten: Die UI-Schicht enthält Screens und ViewModels, die Domänenschicht Eignungsregeln und Risikologik, die Datenschicht Repositories. KI-Modell und Speicher liegen hinter Schnittstellen, damit sie austauschbar bleiben.

## 2. Bewertungskriterien

| Kriterium | Bedeutung |
| --- | --- |
| Datenschutz | Wie viele Gesundheitsdaten verlassen das Gerät? |
| Offline-Fähigkeit | Funktioniert der Anwendungsfall ohne Netz? |
| Aufwand | Umsetzbar im Rahmen des Moduls, inklusive Einarbeitung |
| Kosten | Laufende Kosten für Betrieb und Hosting |
| Eignung | Deckt die Lösung den Anwendungsfall vollständig ab? |

## 3. Evaluation und Entscheidung

### 3.1 App und Benutzeroberfläche

| Option | Bewertung |
| --- | --- |
| Kotlin + Jetpack Compose | Nativer, direkter Zugriff auf CameraX und LiteRT; aktueller Android-Standard; deklarative UI |
| Kotlin + XML-Views | Gleiche Plattformzugriffe, aber mehr Boilerplate und kein Vorteil für ein neues Projekt |
| Flutter | Plattformübergreifend, aber Kamera und KI laufen über Plugins; zusätzliche Sprache |
| Kotlin Multiplatform | Teilt Logik mit iOS, was das rein auf Android ausgerichtete MVP nicht braucht |

**Entscheidung: Kotlin mit Jetpack Compose.** Plattformübergreifende Ansätze bringen ohne iOS-Ziel keinen Nutzen, während der Hauptanwendungsfall von einem direkten Zugriff auf Kamera und KI profitiert.

### 3.2 Kameraaufnahme

| Option | Bewertung |
| --- | --- |
| CameraX | Vorschau, Aufnahme und Bildanalyse als fertige Anwendungsfälle; Overlay möglich |
| Camera2 | Volle Kontrolle, aber hoher Aufwand und gerätespezifische Fehlerquellen |
| System-Kamera per Intent | Minimaler Aufwand, aber keine geführte Aufnahme und damit kein UC-03 |

**Entscheidung: CameraX.** Die geführte Aufnahme schließt den System-Intent aus, und die Kontrolle von Camera2 wird nicht benötigt.

### 3.3 Qualitätsprüfung

| Option | Bewertung |
| --- | --- |
| Eigene Metriken | Schärfe über Laplace-Varianz, Licht über Helligkeit; schlank und erklärbar |
| OpenCV | Mächtig, vergrößert aber die App deutlich für wenige benötigte Funktionen |
| Eigenes KI-Modell | Könnte auch Haare und Ausschnitt erkennen, braucht aber gelabelte Daten |

**Entscheidung: eigene Metriken, ausgeführt nach der Aufnahme.** Die Prüfung läuft unabhängig von der Datenhaltung immer auf dem Gerät. Eine Live-Prüfung über die CameraX-Bildanalyse ist eine spätere Erweiterung.

### 3.4 Eignungsprüfung

Die Ausschlussregeln (Alter, Hauttyp, Körperstelle) sind feste Bedingungen und werden als Kotlin-Regeln in der Domänenschicht umgesetzt. Da keine weitere Lösung sinnvoll infrage kommt, entfällt eine Evaluation.

### 3.5 KI-Einstufung

| Kriterium | LiteRT on-device | Eigener Python-Dienst (FastAPI + ONNX) | Externe API |
| --- | --- | --- | --- |
| Datenschutz | Fotos bleiben auf dem Gerät | Fotos gehen an den eigenen Server | Fotos gehen an Dritte |
| Offline-Fähigkeit | ja | nein | nein |
| Aufwand | Modell konvertieren und einbinden | zusätzlich Dienst und Hosting betreiben | gering, aber kein passender, frei nutzbarer Dienst bekannt |
| Kosten | keine | Hosting | nutzungsabhängig |
| Eignung | begrenzt auf kompakte Modelle | auch große Modelle möglich | vom Anbieter abhängig |

Supabase Edge Functions scheiden für die Inferenz aus: Sie sind auf 256 MB Speicher, 2 s CPU-Zeit pro Anfrage und 20 MB Paketgröße begrenzt [1].

**Entscheidung: LiteRT on-device.** Das Modell (z. B. MobileNet oder EfficientNet-Lite) wird extern auf einem öffentlichen Datensatz wie HAM10000 [2] oder ISIC trainiert, nach LiteRT konvertiert und mit der App ausgeliefert. Die drei Risikostufen entstehen über Schwellenwerte auf der Modellausgabe.

Einschränkung: Solche Datensätze zeigen überwiegend helle Haut. Das stützt den Ausschluss von Hauttyp V–VI in UC-02. Das Modell ist nicht klinisch validiert, die App bleibt ein Prototyp.

### 3.6 Datenhaltung

| Kriterium | Room + App-Speicher | Supabase (Postgres + Storage) |
| --- | --- | --- |
| Datenschutz | Daten bleiben auf dem Gerät | Gesundheitsdaten auf einem Server, Auftragsverarbeitung und Löschkonzept nötig |
| Offline-Fähigkeit | ja | nur mit zusätzlichem lokalem Cache |
| Aufwand | gering, keine Authentifizierung | Login, Zugriffsregeln (Row Level Security), Synchronisation |
| Kosten | keine | kostenloser Tarif für den Prototyp, danach nutzungsabhängig |
| Eignung | deckt alle MVP-Use-Cases ab | zusätzlich Gerätewechsel und Sync, die nicht im MVP sind |

**Entscheidung (vorläufig): Room für strukturierte Daten, Fotos als Dateien im privaten App-Speicher.** Die Fotos und die Datenbank werden vom Android-Backup ausgeschlossen, damit keine Gesundheitsdaten ungewollt in die Cloud gelangen.

### 3.7 Bodymap

| Option | Bewertung |
| --- | --- |
| Compose Canvas | 2D-Körperumriss mit Vorder- und Rückseite, Treffererkennung selbst umgesetzt; keine Abhängigkeit |
| WebView mit SVG | Einfache Grafik, aber zusätzliche Brücke zwischen Web und App |
| 3D-Bibliothek | Über den MVP-Umfang hinaus |

**Entscheidung: Compose Canvas.** Die Lösung fügt sich ohne zusätzliche Abhängigkeit in die UI ein.

### 3.8 Erinnerungen

| Option | Bewertung |
| --- | --- |
| WorkManager | Bleibt über Neustarts bestehen, ideal für Intervalle von Wochen bis Monaten |
| AlarmManager | Exakte Zeitpunkte, die hier nicht nötig sind; zusätzliche Berechtigung |
| Firebase Cloud Messaging | Braucht einen Server, der die Termine kennt |

**Entscheidung: WorkManager.** Termine werden lokal geplant, und der Zeitpunkt muss nicht minutengenau sein.

## 4. Gewählter Stack

| Komponente | Technologie |
| --- | --- |
| App und Benutzeroberfläche | Kotlin, Jetpack Compose, MVVM |
| Kameraaufnahme | CameraX |
| Qualitätsprüfung | eigene Metriken |
| Eignungsprüfung | Kotlin-Regeln |
| KI-Einstufung | LiteRT, extern trainiertes Modell |
| Datenhaltung | Room, privater App-Speicher |
| Bodymap | Compose Canvas |
| Erinnerungen | WorkManager |

## 5. Alternative mit Backend

Verlangt das Modul ein Backend, bleibt die KI-Einstufung auf dem Gerät. Die Datenhaltung wechselt dann zu Supabase mit Auth, Postgres und Storage in einer EU-Region. Die Use Cases erweitern sich um „Anmelden“ (Feature 27), und Datenschutz (Feature 28) wird Teil des MVP. Room bleibt als lokaler Cache sinnvoll, damit der Verlauf offline lesbar ist.

## Quellen

- [1] Supabase: Edge Functions Limits, https://supabase.com/docs/guides/functions/limits; Bundle-Größe: https://supabase.com/docs/guides/troubleshooting/edge-function-fails-deploy
- [2] Tschandl, P., Rosendahl, C., Kittler, H. (2018): The HAM10000 dataset. Scientific Data 5, 180161.
