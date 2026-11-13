1. Projektbeschreibung und Kontext
In einem Satz
[App-Name] ist eine Smartphone-App, die Fotos von Hautveränderungen mit KI auswertet, das Hautkrebsrisiko in drei Stufen einschätzt und bei Auffälligkeiten den Besuch bei einem Arzt empfiehlt.

Ausgangslage und Zielgruppe
Im Rahmen unseres Projektes haben wir entschieden, eine Objekterkennungsanwendung zu entwickeln. Dafür haben wir uns vorgenommen, das Thema Hautkrebs zu untersuchen und die Erkennung maligner Hautläsionen in einer Smartphone-Anwendung umzusetzen. Eine genauere Analyse der Hautkrebserkrankungen hat gezeigt, dass ältere Menschen häufiger an dieser Art der Erkrankung leiden. Aus diesem Grund soll die Anwendung vor allem für Menschen dieser Altersgruppe konzipiert werden. Sie soll aber auch allen anderen Menschen, die sich um die Gesundheit ihrer Haut kümmern wollen, im Alltag helfen. Im Rahmen der Marktanalyse wurden mehrere Anwendungen identifiziert, die die Erkennung von Hautkrebs umsetzen. Nach der Analyse ihrer Funktionalitäten haben wir festgestellt, dass unsere App keine Diagnose liefern soll, sondern eine Einschätzung und auf dieser Grundlage gegebenenfalls die Empfehlung, einen Arzt aufzusuchen.

Vision
Langfristig soll die App ein digitaler Begleiter für die Hautkrebsvorsorge werden. Nutzer dokumentieren ihre Muttermale regelmäßig, Veränderungen werden automatisch erkannt, und die Ergebnisse lassen sich als Bericht an Hautärzte weitergeben. Über den Kurs hinaus wären eine Anbindung an Teledermatologie-Dienste sowie eine klinische Validierung und Zulassung als Medizinprodukt denkbar.

Nutzungskontext
Die App wird vor allem im Alltag zu Hause genutzt, etwa bei der regelmäßigen Selbstuntersuchung der Haut alle drei Monate. Zusätzlich kann sie in der Freizeit hilfreich sein, zum Beispiel im Sommer oder im Urlaub bei hoher UV-Belastung. Da die Zielgruppe vor allem ältere Menschen sind, legen wir Wert auf eine einfache Bedienung: große Schaltflächen, eine klare Sprache und eine Schritt-für-Schritt-Anleitung bei der Fotoaufnahme.

Ähnliche Apps und Abgrenzung
Zu den bekanntesten Anwendungen gehören SkinVision und SkinScreener, die eine KI-basierte Risikoeinschätzung anbieten, sowie Miiskin, das sich auf die Dokumentation von Muttermalen konzentriert. Teledermatologie-Dienste wie Dermanostic und OnlineDoctor verbinden Nutzer dagegen direkt mit Hautärzten. Unsere App unterscheidet sich vor allem durch die Ausrichtung auf ältere Nutzer und durch die Verbindung von Risikoeinschätzung und Verlaufsbeobachtung in einer einfachen Oberfläche. [Weiteres Unterscheidungsmerkmal, z. B. kostenlos, Datenverarbeitung auf dem Gerät oder Arztsuche in der Nähe]

1. Motivation
1.1 Ausgangsproblem
Ein Muttermal fällt auf, und plötzlich stellt sich die Frage: Sah das schon immer so aus? Ohne ältere Aufnahmen lässt sich das aus der Erinnerung oft schwer beantworten. Einzelne Fotos in der Smartphone-Galerie helfen nur bedingt, wenn sie zwischen anderen Bildern verschwinden oder später nicht mehr klar ist, welche Körperstelle fotografiert wurde. Genau hier setzt unsere Projektidee an: Hautstellen sollen sich einfach dokumentieren und über einen längeren Zeitraum wiederfinden lassen.

Neben der Dokumentation geht es um den Umgang mit Unsicherheit. Wer eine Hautstelle fotografiert, möchte ein verständliches Ergebnis und wissen, was damit gemeint ist. Die geplante KI-Risikoeinstufung soll deshalb nicht allein stehen, sondern durch eine Erklärung ihrer Grenzen und Hinweise zum weiteren Vorgehen ergänzt werden. Im Studienprojekt untersuchen wir, wie sich dieser Ablauf technisch und in der Benutzeroberfläche umsetzen lässt. Eine verlässliche medizinische Beurteilung können wir mit dem Prototyp nicht anbieten.

1.2 Nutzen der App
Unser Ziel ist es, die Beobachtung der eigenen Haut übersichtlicher und im Alltag einfacher zu machen. Dafür verbindet die App mehrere Schritte, die sonst getrennt stattfinden würden:

Hautstellen gezielt festhalten: Eine geführte Kameraaufnahme unterstützt beim Fotografieren. Die Qualitätsprüfung soll ungeeignete Aufnahmen erkennen und zu einer erneuten Aufnahme auffordern.
Aufnahmen wiederfinden: Fotos werden einer Hautstelle zugeordnet und mit ihrem Aufnahmedatum gespeichert. Eine einfache Körperübersicht hilft bei der Orientierung.
Einen Verlauf aufbauen: Frühere Aufnahmen bleiben verfügbar. Nutzer müssen sich dadurch nicht allein auf ihre Erinnerung verlassen. Eine automatische Erkennung von Veränderungen ist damit noch nicht gemeint.
Beobachtung nicht vergessen: Einstellbare Erinnerungen unterstützen dabei, die Dokumentation fortzuführen.
Das Smartphone bietet sich dafür an, weil Kamera, Speicher und Benachrichtigungen bereits vorhanden sind. Zusätzliche Hardware ist für den geplanten Ablauf nicht vorgesehen. Der Verzicht auf ein Nutzerkonto und die zunächst lokale Speicherung sollen den Einstieg erleichtern. Gleichzeitig ist es bei persönlichen Hautfotos wichtig, dass Nutzer nachvollziehen können, wo ihre Bilder gespeichert werden.

1.3 Motivation im Studienprojekt
Für das Modul Mobile Software Engineering ist das Thema interessant, weil es mehrere typische Aufgaben mobiler Entwicklung in einem zusammenhängenden Anwendungsfall verbindet: Kamerazugriff, lokale Datenhaltung, Benachrichtigungen und die Einbindung eines KI-Modells auf dem Gerät. Dabei reicht es nicht, dass die einzelnen Funktionen technisch funktionieren. Auch die Bedienung muss verständlich sein, besonders bei Aufnahmefehlern oder einer nicht möglichen Auswertung.

Der Schwerpunkt liegt auf einem nachvollziehbaren mobilen Prototyp. Wir wollen zeigen, wie Aufnahme, experimentelle Auswertung und Dokumentation zusammenspielen. Ob die KI medizinisch zuverlässige Ergebnisse liefert, lässt sich daraus nicht ableiten. Die App ersetzt keine ärztliche Untersuchung; auch eine niedrige angezeigte Risikostufe darf nicht als Entwarnung dargestellt werden.

2. Zielgruppe
2.1 Primäre Zielgruppe
Die geplante App richtet sich an erwachsene Privatpersonen, die einzelne Muttermale oder andere Hautstellen bewusst dokumentieren möchten. Für das MVP konzentrieren wir uns auf deutschsprachige Nutzer mit einem Android-Smartphone. Medizinische Vorkenntnisse sollen für die Bedienung nicht erforderlich sein.

Im Vordergrund stehen zwei Nutzungssituationen:

Regelmäßige Dokumentation: Eine Person möchte bestimmte Hautstellen über längere Zeit festhalten. Wichtig sind für sie eine einfache Zuordnung, eine übersichtliche Bildhistorie und Erinnerungen.
Dokumentation aus einem konkreten Anlass: Einer Person fällt eine Hautstelle auf, die sie bisher nicht bewusst beobachtet hat. Sie möchte eine Aufnahme speichern und benötigt klare Hinweise dazu, was die App leisten kann und wo ihre Grenzen liegen.
Auch ältere Personen gehören ausdrücklich zur Zielgruppe. Die App soll für sie ebenso verständlich und einfach bedienbar sein wie für jüngere Nutzer. Wir legen deshalb keine enge Altersgruppe fest, sondern orientieren uns am Bedürfnis, Hautstellen zu dokumentieren. Für die Bedienung setzen wir lediglich grundlegende Smartphone-Kenntnisse voraus.

2.2 Anforderungen aus der Zielgruppe
Aus diesen Nutzungssituationen ergeben sich folgende Anforderungen:

Einfache Sprache: Begriffe wie „Läsion“ müssen erklärt oder in der Oberfläche durch „Hautstelle“ ersetzt werden.
Kurzer, geführter Ablauf: Von der Auswahl einer Hautstelle bis zur gespeicherten Aufnahme sollen möglichst wenige, verständliche Schritte nötig sein.
Gut erkennbare Bedienelemente: Gut lesbare Schrift, deutliche Kontraste und ausreichend große Schaltflächen sollen die Bedienung auch bei eingeschränktem Sehvermögen oder motorischen Schwierigkeiten erleichtern.
Lesbare Ergebnisse: Risikostufen müssen zusätzlich zur Farbe mit Text erläutert werden. Eine Ampelfarbe allein erklärt weder das Ergebnis noch dessen Unsicherheit.
Kontrolle über die eigenen Bilder: Nutzer sollen gespeicherte Aufnahmen leicht wiederfinden und löschen können.
Verständliche Grenzen: Wenn eine Aufnahme nicht ausgewertet werden kann, muss die App den Grund nennen, statt trotzdem ein Ergebnis anzuzeigen.
2.3 Abgrenzung
Hautärzte und medizinische Einrichtungen sind keine primäre Zielgruppe des MVP. Es sind weder eine Praxisverwaltung noch eine direkte ärztliche Beratung innerhalb der App vorgesehen. Angehörige können bei schwer erreichbaren Körperstellen beim Fotografieren helfen; eine eigene Rolle oder ein separates Konto ist dafür zunächst nicht geplant.

Für die KI-Auswertung sieht der Architekturentwurf zusätzliche Einschränkungen nach Alter, Hauttyp und Körperstelle vor. Diese sind als technische Grenzen des geplanten Modells zu verstehen. Ob die konkrete Eingrenzung sachlich ausreicht, muss anhand der verwendeten Daten und der Evaluation geprüft werden. Ein Ausschluss bestimmter Gruppen belegt keine Zuverlässigkeit für die übrigen Nutzer.

Die beschriebene Zielgruppe ist die Zielgruppe des Konzepts. Der Studienprototyp ist für die Demonstration und Erprobung der Abläufe gedacht, nicht für medizinische Entscheidungen im Alltag.

3. Umfang des MVP
Kleinste nützliche Version
Die kleinste nützliche Version der App ermöglicht es, eine Hautstelle zu fotografieren, eine Risikoeinschätzung zu erhalten und daraus eine klare Handlungsempfehlung abzuleiten. Schon damit erfüllt die App ihren Kernzweck: Nutzer erkennen, ob eine Hautveränderung ärztlich abgeklärt werden sollte.

Anwendungsfälle
#	Anwendungsfall	Kategorie
UC1	Hautstelle mit geführter Kamera fotografieren	MVP
UC2	Risikoeinschätzung mit Handlungsempfehlung erhalten	MVP
UC3	Verlauf einer Hautstelle ansehen	MVP
UC4	Erinnerung an die nächste Kontrolle erhalten	MVP
UC5	Hautarzt in der Nähe über Google Maps finden	Nicht MVP
UC6	Warnung bei hohem UV-Index erhalten	Nicht MVP
Verbindlich im Kurs setzen wir die Anwendungsfälle UC1 bis UC4 um. UC5 und UC6 gehören zur langfristigen Vision und werden nur umgesetzt, wenn Zeit bleibt.

MVP-Funktionalitäten
Im Laufe der Marktanalyse wurden weitere Funktionalitäten identifiziert, die zu unserem Minimum Viable Product (MVP) gehören sollen. Sie bilden die technischen Bausteine der Anwendungsfälle UC1 bis UC4:

#	Bereich	Feature	Beschreibung	Gesehen bei	Anwendungsfall
1	Bildaufnahme	Geführte Kameraaufnahme	Overlay, Abstand, Fokus, automatischer Auslöser	SkinVision, SkinScreener, DERM Zero	UC1
2	Bildaufnahme	Bildqualitätsprüfung	Unschärfe, Licht, Haare und Ausschnitt erkennen und eine Neuaufnahme verlangen	SkinVision, DermEngine	UC1
3	KI-Analyse	Risikoeinstufung	3 Stufen (niedrig / mittel / hoch, Ampel)	SkinVision, SkinScreener, Skinive	UC2
4	KI-Analyse	Ausschluss ungeeigneter Fälle	Kinder, Hauttyp V–VI, Schleimhaut, Nägel → direkt zum Arzt	SkinScreener (Hauttyp I–IV), NICE-Auflage bei DERM	UC2
5	Ergebnis	Handlungsempfehlung	„In 3 Monaten erneut prüfen“ vs. „Dringend einen Arzt aufsuchen“	SkinVision, SkinScreener, DERM Zero	UC2
6	Monitoring	Läsionsprofil und Verlauf	Jede Hautstelle mit eigener Bildhistorie	SkinVision, Miiskin, MoleScope	UC3
7	Monitoring	2D/3D-Bodymap	Läsionen am Körper verorten	SkinVision, MoleScope, DermEngine	UC3
8	Engagement	Erinnerungen	Push/E-Mail/SMS, Intervall von 0 bis 6 Monaten einstellbar	SkinVision, UMSkinCheck, MoleScope	UC4
Zusätzliche Funktionalitäten, die eventuell implementiert werden, sind:

UV-Index-Warnung (UC6)
Arztsuche über Google Maps (UC5)
Kriterien für die MVP-Auswahl
Bei der Auswahl der MVP-Funktionen haben wir uns an vier Kriterien orientiert:

Kernnutzen: Trägt die Funktion direkt dazu bei, verdächtige Hautveränderungen zu erkennen?
Sicherheit: Verhindert die Funktion Fehleinschätzungen, etwa durch schlechte Bildqualität oder ungeeignete Fälle?
Machbarkeit: Lässt sich die Funktion mit unserem Wissensstand im Kurszeitraum umsetzen?
Abhängigkeiten: Bauen andere Funktionen darauf auf?
Machbarkeit im Kurszeitraum
Der MVP-Umfang ist im Kurszeitraum von [X Wochen] mit 4 Personen realistisch, wenn wir für die KI-Analyse auf ein vortrainiertes Modell zurückgreifen und es mit einem öffentlichen Datensatz wie HAM10000 oder dem ISIC-Archiv nachtrainieren. Das größte Risiko liegt in der Genauigkeit des Modells bei Fotos, die mit dem Smartphone aufgenommen wurden. Die 2D/3D-Bodymap ist der aufwendigste Teil. Falls die Zeit knapp wird, ersetzen wir sie durch eine einfache Auswahl der Körperregion aus einer Liste.

# Anwendungsfälle und Akteure

MVP-Umfang: Features 1, 2, 6, 10, 11, 14, 15, 19 aus der [Marktanalyse](Hautkrebs-Erkennungs-Apps%20Marktanalyse%20&%20MVP-Features.md). Die App ist ein Prototyp und kein zugelassenes Medizinprodukt.

Diagramm: [use-case-diagramm.puml](use-case-diagramm.puml)

## Akteure

| Akteur | Art | Beschreibung |
| --- | --- | --- |
| Nutzer:in | primär | Erwachsene Person, die Hautstellen selbst fotografiert, einschätzen lässt und über die Zeit beobachtet |
| KI-Dienst | sekundär, nur falls extern | Liefert die Risikoeinstufung zu einem Foto; läuft das Modell on-device, gehört es zum System und entfällt als Akteur |

## Übersicht

| ID | Use Case | Akteur | Beziehungen | Feature |
| --- | --- | --- | --- | --- |
| UC-01 | Hautstelle prüfen (Hauptanwendungsfall) | Nutzer:in | include: UC-02, UC-03, UC-05, UC-06; extend: UC-07, UC-08 | – |
| UC-02 | Eignung prüfen | – | Teil von UC-01 | 10 |
| UC-03 | Foto aufnehmen | – | Teil von UC-01; include: UC-04 | 1 |
| UC-04 | Bildqualität prüfen | – | Teil von UC-03 | 2 |
| UC-05 | Risiko einstufen | KI-Dienst (falls extern) | Teil von UC-01 | 6 |
| UC-06 | Handlungsempfehlung anzeigen | – | Teil von UC-01 | 11 |
| UC-07 | An Arzt verweisen | – | erweitert UC-01 | 10 |
| UC-08 | Läsion anlegen und verorten | Nutzer:in | erweitert UC-01, auch direkt nutzbar | 14, 15 |
| UC-09 | Verlauf einsehen | Nutzer:in | – | 14, 15 |
| UC-10 | Erinnerung einstellen | Nutzer:in | – | 19 |
| UC-11 | An Kontrolle erinnert werden | Nutzer:in | – | 19 |

## Beschreibungen

Alle Use Cases sind Kategorie MVP und Typ funktional.

### UC-01 Hautstelle prüfen

- **Ziel:** Die Person erhält zu einer Hautstelle eine Risikoeinstufung und einen klaren nächsten Schritt.
- **Vorbedingung:** App ist installiert, Kamerazugriff ist erlaubt.
- **Nachbedingung:** Foto und Ergebnis sind einer Läsion zugeordnet und gespeichert.
- **Hauptablauf:**
  1. Nutzer:in startet die Prüfung für eine neue oder eine bestehende Läsion.
  2. System prüft die Eignung (UC-02).
  3. Nutzer:in nimmt das Foto auf (UC-03).
  4. System stuft das Risiko ein (UC-05).
  5. System zeigt Einstufung und Handlungsempfehlung an (UC-06).
  6. System speichert das Ergebnis bei der bestehenden Läsion oder legt eine neue an (UC-08).
- **Alternativen:**
  - 2a. Fall ist ungeeignet: Verweis an Arzt (UC-07), Prüfung endet ohne Einstufung.
  - 4a. Analyse schlägt fehl: System zeigt keine Einstufung und bietet einen neuen Versuch an.
- **Akzeptanzkriterien:**
  - [ ] Eine Einstufung erscheint nur nach bestandener Eignungs- und Qualitätsprüfung.
  - [ ] Das Ergebnis ist danach im Verlauf der Läsion sichtbar.

### UC-02 Eignung prüfen

- **Ziel:** Fälle, für die die Einstufung nicht verantwortbar ist, werden vor der Analyse aussortiert.
- **Ablauf:** Nutzer:in gibt Alter, Hauttyp und Körperstelle an, das System bewertet die Angaben.
- **Ungeeignet:** unter 18 Jahre, Hauttyp V–VI, Schleimhaut oder Nägel.
- **Akzeptanzkriterien:**
  - [ ] Jeder der vier Ausschlussgründe führt zu UC-07.

### UC-03 Foto aufnehmen

- **Ziel:** Ein für die Analyse brauchbares Foto der Hautstelle.
- **Ablauf:** System führt per Overlay zu Abstand und Ausschnitt, Nutzer:in oder automatischer Auslöser nimmt das Foto auf, danach folgt UC-04.
- **Alternative:** Kamerazugriff verweigert: System erklärt, wie er erteilt wird.
- **Akzeptanzkriterien:**
  - [ ] Overlay ist während der gesamten Aufnahme sichtbar.

### UC-04 Bildqualität prüfen

- **Ziel:** Unbrauchbare Fotos erreichen die Analyse nicht.
- **Ablauf:** System prüft Schärfe, Licht und Ausschnitt.
- **Alternative:** Prüfung nicht bestanden: System nennt den Grund und verlangt eine Neuaufnahme.
- **Akzeptanzkriterien:**
  - [ ] Unscharfe oder zu dunkle Fotos werden abgelehnt.

### UC-05 Risiko einstufen

- **Ziel:** Das Foto wird einer von drei Stufen zugeordnet: niedrig, mittel oder hoch.
- **Ablauf:** System übergibt das Foto dem KI-Modell und übernimmt die Stufe.
- **Akzeptanzkriterien:**
  - [ ] Das Ergebnis ist immer genau eine der drei Stufen oder ein Fehler.

### UC-06 Handlungsempfehlung anzeigen

- **Ziel:** Die Person weiß, was sie als Nächstes tun soll.
- **Ablauf je Stufe:**
  - niedrig: beobachten, Kontrolle in 3 Monaten
  - mittel: zeitnah ärztlich abklären lassen
  - hoch: dringend Arzt aufsuchen
- **Akzeptanzkriterien:**
  - [ ] Jede Stufe zeigt ihre Empfehlung und den Hinweis, dass das Ergebnis keine Diagnose ist.

### UC-07 An Arzt verweisen

- **Ziel:** Ungeeignete Fälle bleiben nicht ohne nächsten Schritt.
- **Bedingung:** Eignungsprüfung nicht bestanden.
- **Ablauf:** System nennt den Grund und empfiehlt eine ärztliche Abklärung.
- **Akzeptanzkriterien:**
  - [ ] Der Verweis nennt den konkreten Ausschlussgrund.

### UC-08 Läsion anlegen und verorten

- **Ziel:** Jede beobachtete Stelle ist eindeutig am Körper hinterlegt.
- **Bedingung bei Erweiterung von UC-01:** Das Ergebnis gehört zu einer neuen Läsion.
- **Ablauf:** Nutzer:in markiert die Stelle auf der 2D-Bodymap und vergibt optional einen Namen. Die Körperstelle aus UC-02 ist vorbelegt.
- **Akzeptanzkriterien:**
  - [ ] Die Läsion erscheint an der markierten Stelle der Bodymap.

### UC-09 Verlauf einsehen

- **Ziel:** Die Person erkennt, wie sich eine Läsion über die Zeit entwickelt.
- **Vorbedingung:** Mindestens eine Läsion ist angelegt.
- **Ablauf:** Nutzer:in wählt eine Läsion auf der Bodymap, System zeigt Fotos und Einstufungen chronologisch an.
- **Alternative:** Von hier startet eine Folgeprüfung (UC-01) für diese Läsion.
- **Akzeptanzkriterien:**
  - [ ] Einträge sind nach Datum sortiert und zeigen Foto und Stufe.

### UC-10 Erinnerung einstellen

- **Ziel:** Kontrollen einer Läsion werden nicht vergessen.
- **Vorbedingung:** Läsion ist angelegt.
- **Ablauf:** Nutzer:in wählt für die Läsion ein Intervall von bis zu 6 Monaten oder deaktiviert die Erinnerung.
- **Akzeptanzkriterien:**
  - [ ] Das Intervall lässt sich ändern und deaktivieren.

### UC-11 An Kontrolle erinnert werden

- **Ziel:** Die Person wird zum fälligen Zeitpunkt zur Kontrolle aufgefordert.
- **Auslöser:** Der Termin der Erinnerung ist erreicht.
- **Ablauf:** System zeigt eine Benachrichtigung, Antippen öffnet die Folgeprüfung (UC-01) der Läsion.
- **Alternative:** Benachrichtigungen nicht erlaubt: Fällige Kontrolle wird in der App angezeigt.
- **Akzeptanzkriterien:**
  - [ ] Die Benachrichtigung erscheint zum eingestellten Termin und führt zur richtigen Läsion.

## Nicht im MVP

| Use Case | Feature |
| --- | --- |
| Bericht als PDF exportieren | 13 |
| Symptome angeben | 8 |
| Risikoprofil und Hauttyp pflegen | 20 |
| Läsionsfotos direkt vergleichen | 16 |
| Ergebnis von Dermatolog:in prüfen lassen | 12 |
| Fall an Teledermatologie senden | 23 |
| Registrieren und Einwilligung verwalten | 27 |

## Offene Entscheidungen

| Frage | Auswirkung auf die Use Cases | Auswirkung auf den Stack |
| --- | --- | --- |
| KI on-device oder im Backend/extern? | KI-Dienst ist Akteur oder entfällt; UC-01 braucht ggf. Offline-Fall | LiteRT oder eigener Python-Dienst/externe API |
| Daten lokal oder in Supabase? | Bei Cloud-Speicherung kommt „Anmelden“ ins MVP (Feature 27) | Room oder Supabase Auth/DB/Storage |
| Erinnerung lokal oder per Push? | keine | WorkManager/AlarmManager oder FCM |
| Qualitätsprüfung live oder nach dem Foto? | Auslöser in UC-03 automatisch oder manuell | CameraX-Analyse oder Prüfung des fertigen Bilds |
| Selbstauskunft je Prüfung oder einmalig? | Ablauf von UC-02 | Speicherung der Angaben |

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
