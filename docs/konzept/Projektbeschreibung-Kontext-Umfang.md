# hautkrebs_app – Abschnitte 1 und 3

## 1. Projektbeschreibung und Kontext

### In einem Satz

[App-Name] ist eine Smartphone-App, die Fotos von Hautveränderungen mit KI auswertet, das Hautkrebsrisiko in drei Stufen einschätzt und bei Auffälligkeiten den Besuch bei einem Arzt empfiehlt.

### Ausgangslage und Zielgruppe

Im Rahmen unseres Projektes haben wir entschieden, eine Objekterkennungsanwendung zu entwickeln. Dafür haben wir uns vorgenommen, das Thema Hautkrebs zu untersuchen und die Erkennung maligner Hautläsionen in einer Smartphone-Anwendung umzusetzen. Eine genauere Analyse der Hautkrebserkrankungen hat gezeigt, dass ältere Menschen häufiger an dieser Art der Erkrankung leiden. Aus diesem Grund soll die Anwendung vor allem für Menschen dieser Altersgruppe konzipiert werden. Sie soll aber auch allen anderen Menschen, die sich um die Gesundheit ihrer Haut kümmern wollen, im Alltag helfen. Im Rahmen der Marktanalyse wurden mehrere Anwendungen identifiziert, die die Erkennung von Hautkrebs umsetzen. Nach der Analyse ihrer Funktionalitäten haben wir festgestellt, dass unsere App keine Diagnose liefern soll, sondern eine Einschätzung und auf dieser Grundlage gegebenenfalls die Empfehlung, einen Arzt aufzusuchen.

### Vision

Langfristig soll die App ein digitaler Begleiter für die Hautkrebsvorsorge werden. Nutzer dokumentieren ihre Muttermale regelmäßig, Veränderungen werden automatisch erkannt, und die Ergebnisse lassen sich als Bericht an Hautärzte weitergeben. Über den Kurs hinaus wären eine Anbindung an Teledermatologie-Dienste sowie eine klinische Validierung und Zulassung als Medizinprodukt denkbar.

### Nutzungskontext

Die App wird vor allem im Alltag zu Hause genutzt, etwa bei der regelmäßigen Selbstuntersuchung der Haut alle drei Monate. Zusätzlich kann sie in der Freizeit hilfreich sein, zum Beispiel im Sommer oder im Urlaub bei hoher UV-Belastung. Da die Zielgruppe vor allem ältere Menschen sind, legen wir Wert auf eine einfache Bedienung: große Schaltflächen, eine klare Sprache und eine Schritt-für-Schritt-Anleitung bei der Fotoaufnahme.

### Ähnliche Apps und Abgrenzung

Zu den bekanntesten Anwendungen gehören SkinVision und SkinScreener, die eine KI-basierte Risikoeinschätzung anbieten, sowie Miiskin, das sich auf die Dokumentation von Muttermalen konzentriert. Teledermatologie-Dienste wie Dermanostic und OnlineDoctor verbinden Nutzer dagegen direkt mit Hautärzten. Unsere App unterscheidet sich vor allem durch die Ausrichtung auf ältere Nutzer und durch die Verbindung von Risikoeinschätzung und Verlaufsbeobachtung in einer einfachen Oberfläche. [Weiteres Unterscheidungsmerkmal, z. B. kostenlos, Datenverarbeitung auf dem Gerät oder Arztsuche in der Nähe]

## 3. Umfang des MVP

### Kleinste nützliche Version

Die kleinste nützliche Version der App ermöglicht es, eine Hautstelle zu fotografieren, eine Risikoeinschätzung zu erhalten und daraus eine klare Handlungsempfehlung abzuleiten. Schon damit erfüllt die App ihren Kernzweck: Nutzer erkennen, ob eine Hautveränderung ärztlich abgeklärt werden sollte.

### Anwendungsfälle

| # | Anwendungsfall | Kategorie |
|---|---|---|
| UC1 | Hautstelle mit geführter Kamera fotografieren | MVP |
| UC2 | Risikoeinschätzung mit Handlungsempfehlung erhalten | MVP |
| UC3 | Verlauf einer Hautstelle ansehen | MVP |
| UC4 | Erinnerung an die nächste Kontrolle erhalten | MVP |
| UC5 | Hautarzt in der Nähe über Google Maps finden | Nicht MVP |
| UC6 | Warnung bei hohem UV-Index erhalten | Nicht MVP |

Verbindlich im Kurs setzen wir die Anwendungsfälle UC1 bis UC4 um. UC5 und UC6 gehören zur langfristigen Vision und werden nur umgesetzt, wenn Zeit bleibt.

### MVP-Funktionalitäten

Im Laufe der Marktanalyse wurden weitere Funktionalitäten identifiziert, die zu unserem Minimum Viable Product (MVP) gehören sollen. Sie bilden die technischen Bausteine der Anwendungsfälle UC1 bis UC4:

| # | Bereich | Feature | Beschreibung | Gesehen bei | Anwendungsfall |
|---|---|---|---|---|---|
| 1 | Bildaufnahme | Geführte Kameraaufnahme | Overlay, Abstand, Fokus, automatischer Auslöser | SkinVision, SkinScreener, DERM Zero | UC1 |
| 2 | Bildaufnahme | Bildqualitätsprüfung | Unschärfe, Licht, Haare und Ausschnitt erkennen und eine Neuaufnahme verlangen | SkinVision, DermEngine | UC1 |
| 3 | KI-Analyse | Risikoeinstufung | 3 Stufen (niedrig / mittel / hoch, Ampel) | SkinVision, SkinScreener, Skinive | UC2 |
| 4 | KI-Analyse | Ausschluss ungeeigneter Fälle | Kinder, Hauttyp V–VI, Schleimhaut, Nägel → direkt zum Arzt | SkinScreener (Hauttyp I–IV), NICE-Auflage bei DERM | UC2 |
| 5 | Ergebnis | Handlungsempfehlung | „In 3 Monaten erneut prüfen“ vs. „Dringend einen Arzt aufsuchen“ | SkinVision, SkinScreener, DERM Zero | UC2 |
| 6 | Monitoring | Läsionsprofil und Verlauf | Jede Hautstelle mit eigener Bildhistorie | SkinVision, Miiskin, MoleScope | UC3 |
| 7 | Monitoring | 2D/3D-Bodymap | Läsionen am Körper verorten | SkinVision, MoleScope, DermEngine | UC3 |
| 8 | Engagement | Erinnerungen | Push/E-Mail/SMS, Intervall von 0 bis 6 Monaten einstellbar | SkinVision, UMSkinCheck, MoleScope | UC4 |

Zusätzliche Funktionalitäten, die eventuell implementiert werden, sind:

- UV-Index-Warnung (UC6)
- Arztsuche über Google Maps (UC5)

### Kriterien für die MVP-Auswahl

Bei der Auswahl der MVP-Funktionen haben wir uns an vier Kriterien orientiert:

1. **Kernnutzen:** Trägt die Funktion direkt dazu bei, verdächtige Hautveränderungen zu erkennen?
2. **Sicherheit:** Verhindert die Funktion Fehleinschätzungen, etwa durch schlechte Bildqualität oder ungeeignete Fälle?
3. **Machbarkeit:** Lässt sich die Funktion mit unserem Wissensstand im Kurszeitraum umsetzen?
4. **Abhängigkeiten:** Bauen andere Funktionen darauf auf?

### Machbarkeit im Kurszeitraum

Der MVP-Umfang ist im Kurszeitraum von [X Wochen] mit 4 Personen realistisch, wenn wir für die KI-Analyse auf ein vortrainiertes Modell zurückgreifen und es mit einem öffentlichen Datensatz wie HAM10000 oder dem ISIC-Archiv nachtrainieren. Das größte Risiko liegt in der Genauigkeit des Modells bei Fotos, die mit dem Smartphone aufgenommen wurden. Die 2D/3D-Bodymap ist der aufwendigste Teil. Falls die Zeit knapp wird, ersetzen wir sie durch eine einfache Auswahl der Körperregion aus einer Liste.
