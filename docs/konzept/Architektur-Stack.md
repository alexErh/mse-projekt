## 6. Architektur und Technologiestack

Drei Eigenschaften des MVP prägen die Architektur. Die App verarbeitet Hautfotos und damit Gesundheitsdaten im Sinne von Art. 9 DSGVO [1]. Der Hauptanwendungsfall hängt von Kamera und Bildanalyse ab. Und das MVP sieht kein Nutzerkonto vor. Aus der Evaluation in diesem Kapitel ergibt sich daraus eine Grundentscheidung: Die App arbeitet vollständig auf dem Gerät und kommt ohne eigenes Backend aus.

### 6.1 Komponenten

Aus den Anwendungsfällen ergeben sich acht Komponenten. Die Benutzeroberfläche umfasst alle Screens, die Navigation und die Zustandsverwaltung. Die Kameraaufnahme stellt Vorschau, Overlay und Auslöser bereit (UC-03), die Qualitätsprüfung bewertet Schärfe und Belichtung (UC-04). Die Eignungsprüfung gleicht die Angaben des Nutzers mit den Ausschlussregeln ab (UC-02, UC-07). Die KI-Einstufung ordnet ein Foto einer Risikostufe zu und leitet die Empfehlung ab (UC-05, UC-06). Die Datenhaltung speichert und löscht Hautstellen, Ergebnisse und Fotos (UC-01, UC-08, UC-09, UC-12). Über die Körperübersicht verortet und wählt der Nutzer Hautstellen (UC-08, UC-09), und die Erinnerungskomponente plant Termine und löst Benachrichtigungen aus (UC-10, UC-11).

Die App folgt dem Architekturmuster Model-View-ViewModel (MVVM) mit drei Schichten. Die UI-Schicht enthält Screens und ViewModels, die Domänenschicht die Eignungsregeln und die Risikologik, die Datenschicht die Repositories für den Datenzugriff. KI-Modell und Speicher liegen hinter Schnittstellen und bleiben so austauschbar.

### 6.2 Bewertungskriterien

Alle Komponenten werden nach denselben fünf Kriterien bewertet. Beim **Datenschutz** zählt, wie viele Gesundheitsdaten das Gerät verlassen. Die **Offline-Fähigkeit** beschreibt, ob der Anwendungsfall ohne Netzverbindung funktioniert. Der **Aufwand** umfasst Umsetzung und Einarbeitung im Rahmen des Moduls, die **Kosten** laufende Ausgaben für Betrieb und Hosting. Die **Eignung** gibt an, ob eine Lösung den Anwendungsfall vollständig abdeckt. Scheidet eine Option an einem Kriterium eindeutig aus, werden die übrigen nicht weiter betrachtet.

### 6.3 Evaluation und Entscheidung

#### 6.3.1 Benutzeroberfläche

Zur Wahl standen die native Entwicklung mit Kotlin, wahlweise mit Jetpack Compose oder klassischen XML-Layouts, sowie die plattformübergreifenden Frameworks Flutter und Kotlin Multiplatform. Plattformübergreifende Ansätze bringen keinen Vorteil, da das MVP nur Android unterstützt (Abschnitt 3.1). Flutter bindet Kamera und KI zudem nur über Plugins an und erfordert mit Dart eine weitere Sprache. Unter den nativen Varianten benötigt das deklarative Jetpack Compose weniger Boilerplate-Code als XML-Layouts, und für ein neues Projekt spricht nichts für die ältere Technik.

**Entscheidung: Kotlin mit Jetpack Compose.**

#### 6.3.2 Kameraaufnahme

Android bietet drei Wege zur Kamera. Der Aufruf der System-Kamera per Intent ist am einfachsten, erlaubt aber kein Overlay und damit keine geführte Aufnahme. Camera2 gibt volle Kontrolle über die Hardware, verursacht aber hohen Aufwand und gerätespezifische Fehlerquellen. Die Jetpack-Bibliothek CameraX stellt Vorschau, Aufnahme und Bildanalyse als fertige Bausteine bereit und lässt sich mit einem eigenen Overlay kombinieren.

**Entscheidung: CameraX.**

#### 6.3.3 Qualitätsprüfung

Für die Qualitätsprüfung kommen eigene Bildmetriken, die Bibliothek OpenCV oder ein eigenes KI-Modell infrage. OpenCV deckt die benötigten Funktionen ab, vergrößert die App aber deutlich für wenige genutzte Funktionen. Ein eigenes Modell könnte auch Haare oder einen falschen Bildausschnitt erkennen, setzt aber gelabelte Trainingsdaten voraus. Für das MVP genügen eigene Metriken: Die Schärfe lässt sich über die Varianz des Laplace-gefilterten Bildes messen, die Belichtung über die mittlere Helligkeit. Die Prüfung läuft nach der Aufnahme. Eine Live-Prüfung in der Vorschau über die Bildanalyse von CameraX bleibt eine spätere Erweiterung.

**Entscheidung: eigene Metriken für Schärfe und Belichtung, geprüft nach der Aufnahme.**

#### 6.3.4 Eignungsprüfung

Die Ausschlussregeln sind feste Bedingungen über Alter, Hauttyp und Körperstelle. Sie werden als einfache Regeln in der Domänenschicht umgesetzt. Eine Bibliothek oder ein externer Dienst würde hier keinen Mehrwert bringen, weshalb eine Evaluation entfällt.

#### 6.3.5 KI-Einstufung

Die Einstufung kann auf dem Gerät, auf einem eigenen Server oder über einen externen Dienst laufen. Tabelle [X] vergleicht die drei Optionen.

| Kriterium | LiteRT auf dem Gerät | Eigener Server (z. B. FastAPI mit ONNX Runtime) | Externer Dienst |
| --- | --- | --- | --- |
| Datenschutz | Fotos bleiben auf dem Gerät | Fotos gehen an den eigenen Server | Fotos gehen an Dritte |
| Offline-Fähigkeit | ja | nein | nein |
| Aufwand | Modell konvertieren und einbinden | zusätzlich Dienst und Hosting betreiben | gering, aber uns ist kein passender, frei nutzbarer Dienst bekannt |
| Kosten | keine | Hosting | nutzungsabhängig |
| Eignung | nur kompakte Modelle | auch große Modelle | vom Anbieter abhängig |

Auch Backend-as-a-Service-Plattformen eignen sich nicht für die Inferenz. Supabase begrenzt seine Edge Functions beispielsweise auf 256 MB Arbeitsspeicher, 2 s CPU-Zeit pro Anfrage und 20 MB Paketgröße [2].

Die Entscheidung fällt auf LiteRT, die Laufzeitumgebung für Modelle auf dem Gerät, die Google bis 2024 unter dem Namen TensorFlow Lite entwickelt hat [3]. Ausschlaggebend sind Datenschutz und Offline-Fähigkeit: Die Fotos verlassen das Smartphone nicht, und es entsteht kein Server, der betrieben und abgesichert werden muss. Als Modell eignet sich eine für Mobilgeräte entworfene Architektur wie MobileNet [4]. Ein vortrainiertes Modell wird auf einem öffentlichen Datensatz wie HAM10000 [5] oder dem ISIC-Archiv nachtrainiert (Abschnitt 4.5), nach LiteRT konvertiert und mit der App ausgeliefert. Die drei Risikostufen entstehen über Schwellenwerte auf der Modellausgabe.

Zwei Einschränkungen nehmen wir dabei bewusst in Kauf. HAM10000 besteht aus dermatoskopischen Aufnahmen [5], die unter anderen Bedingungen entstehen als Smartphone-Fotos; darin liegt das in Abschnitt 4.5 genannte Genauigkeitsrisiko. Zudem sind dunkle Hauttypen in öffentlichen Datensätzen stark unterrepräsentiert [6], was den Ausschluss von Hauttyp V–VI in der Eignungsprüfung stützt. Das Modell ist nicht klinisch validiert.

**Entscheidung: LiteRT auf dem Gerät mit einem nachtrainierten, kompakten Modell.**

#### 6.3.6 Datenhaltung

Für die Datenhaltung wurden eine lokale Lösung und die Backend-Plattform Supabase verglichen. Supabase bietet eine Postgres-Datenbank, Dateispeicher und Authentifizierung und würde Synchronisation sowie Gerätewechsel ermöglichen. Dafür wären ein Login, Zugriffsregeln auf Datenbankebene und eine Synchronisation nötig. Zudem lägen Gesundheitsdaten auf einem Server, was eine Auftragsverarbeitung und ein Löschkonzept erfordert. Ohne Netz wäre der Verlauf nur mit einem zusätzlichen lokalen Zwischenspeicher lesbar. Die Vorteile von Supabase betreffen also Funktionen außerhalb des MVP, während die Nachteile jeden Anwendungsfall belasten.

Die App speichert daher alle Daten lokal. Strukturierte Daten wie Hautstellen, Ergebnisse und Erinnerungen liegen in einer SQLite-Datenbank, auf die die App über die Jetpack-Bibliothek Room zugreift. Room prüft SQL-Abfragen bereits beim Kompilieren und vereinfacht Migrationen. Fotos liegen als Dateien im privaten Speicher der App. Datenbank und Fotos werden von der Android-Datensicherung ausgeschlossen, damit keine Gesundheitsdaten ungewollt in die Cloud gelangen.

**Entscheidung: Room und privater App-Speicher, ohne Backend.**

#### 6.3.7 Körperübersicht

Die Körperübersicht lässt sich mit der Zeichenfläche (Canvas) von Jetpack Compose, als SVG-Grafik in einer WebView oder mit einer 3D-Bibliothek umsetzen. Eine 3D-Darstellung geht über den MVP-Umfang hinaus, und eine WebView erfordert eine zusätzliche Brücke zwischen Web- und App-Code. Auf dem Canvas lassen sich Vorder- und Rückseite eines Körperumrisses zeichnen, die Erkennung angetippter Körperregionen wird selbst umgesetzt. Diese Lösung kommt ohne zusätzliche Abhängigkeit aus. Reicht die Zeit nicht, ersetzt eine Auswahlliste der Körperregionen die Grafik (Abschnitt 4.5).

**Entscheidung: Compose Canvas.**

#### 6.3.8 Erinnerungen

Erinnerungen lassen sich mit WorkManager, mit AlarmManager oder als Push-Nachricht über Firebase Cloud Messaging umsetzen. Push-Nachrichten setzen einen Server voraus, der die Termine kennt, und scheiden ohne Backend aus. AlarmManager löst zu exakten Zeitpunkten aus, benötigt dafür aber ab Android 12 eine besondere Berechtigung, die Nutzer widerrufen können. Diese Genauigkeit ist bei Intervallen von Wochen bis Monaten unnötig. WorkManager speichert geplante Aufgaben in einer internen Datenbank und plant sie auch nach einem Neustart des Geräts erneut ein.

**Entscheidung: WorkManager.**

### 6.4 Gewählter Stack

Tabelle [X] fasst die Entscheidungen zusammen.

| Komponente | Anwendungsfälle | Technologie |
| --- | --- | --- |
| Benutzeroberfläche | alle | Kotlin, Jetpack Compose, MVVM |
| Kameraaufnahme | UC-03 | CameraX |
| Qualitätsprüfung | UC-04 | eigene Metriken |
| Eignungsprüfung | UC-02, UC-07 | Regeln in der Domänenschicht |
| KI-Einstufung | UC-05, UC-06 | LiteRT, nachtrainiertes Modell |
| Datenhaltung | UC-01, UC-08, UC-09, UC-12 | Room, privater App-Speicher |
| Körperübersicht | UC-08, UC-09 | Compose Canvas |
| Erinnerungen | UC-10, UC-11 | WorkManager |

Die optionalen Anwendungsfälle aus Abschnitt 4.2 ändern an dieser Architektur nichts Grundlegendes. Die Arztsuche kann eine installierte Karten-App über einen Intent öffnen, und die UV-Warnung benötigt nur den Abruf eines öffentlichen UV-Index-Dienstes. Ein eigenes Backend ist für keinen der beiden nötig.

## Quellen

Online-Quellen abgerufen am 13.11.2026.

- [1] Verordnung (EU) 2016/679 (Datenschutz-Grundverordnung), Art. 9.
- [2] Supabase: Edge Functions Limits. https://supabase.com/docs/guides/functions/limits; zur Paketgröße: https://supabase.com/docs/guides/troubleshooting/edge-function-fails-deploy
- [3] Google Developers Blog (2024): TensorFlow Lite is now LiteRT. https://developers.googleblog.com/en/tensorflow-lite-is-now-litert/
- [4] Howard, A. G. et al. (2017): MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications. arXiv:1704.04861.
- [5] Tschandl, P., Rosendahl, C., Kittler, H. (2018): The HAM10000 dataset, a large collection of multi-source dermatoscopic images of common pigmented skin lesions. Scientific Data 5, 180161. doi:10.1038/sdata.2018.161
- [6] Wen, D. et al. (2022): Characteristics of publicly available skin cancer image datasets: a systematic review. The Lancet Digital Health 4(1), e64–e74. doi:10.1016/S2589-7500(21)00252-1

