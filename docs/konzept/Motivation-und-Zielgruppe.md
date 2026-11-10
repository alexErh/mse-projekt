# Motivation und Zielgruppe (Draft)

## 1. Motivation

### 1.1 Ausgangsproblem

Ein Muttermal fällt auf, und plötzlich stellt sich die Frage: Sah das schon immer so aus? Ohne ältere Aufnahmen lässt sich das aus der Erinnerung oft schwer beantworten. Einzelne Fotos in der Smartphone-Galerie helfen nur bedingt, wenn sie zwischen anderen Bildern verschwinden oder später nicht mehr klar ist, welche Körperstelle fotografiert wurde. Genau hier setzt unsere Projektidee an: Hautstellen sollen sich einfach dokumentieren und über einen längeren Zeitraum wiederfinden lassen.

Neben der Dokumentation geht es um den Umgang mit Unsicherheit. Wer eine Hautstelle fotografiert, möchte ein verständliches Ergebnis und wissen, was damit gemeint ist. Die geplante KI-Risikoeinstufung soll deshalb nicht allein stehen, sondern durch eine Erklärung ihrer Grenzen und Hinweise zum weiteren Vorgehen ergänzt werden. Im Studienprojekt untersuchen wir, wie sich dieser Ablauf technisch und in der Benutzeroberfläche umsetzen lässt. Eine verlässliche medizinische Beurteilung können wir mit dem Prototyp nicht anbieten.

### 1.2 Nutzen der App

Unser Ziel ist es, die Beobachtung der eigenen Haut übersichtlicher und im Alltag einfacher zu machen. Dafür verbindet die App mehrere Schritte, die sonst getrennt stattfinden würden:

- **Hautstellen gezielt festhalten:** Eine geführte Kameraaufnahme unterstützt beim Fotografieren. Die Qualitätsprüfung soll ungeeignete Aufnahmen erkennen und zu einer erneuten Aufnahme auffordern.
- **Aufnahmen wiederfinden:** Fotos werden einer Hautstelle zugeordnet und mit ihrem Aufnahmedatum gespeichert. Eine einfache Körperübersicht hilft bei der Orientierung.
- **Einen Verlauf aufbauen:** Frühere Aufnahmen bleiben verfügbar. Nutzer müssen sich dadurch nicht allein auf ihre Erinnerung verlassen. Eine automatische Erkennung von Veränderungen ist damit noch nicht gemeint.
- **Beobachtung nicht vergessen:** Einstellbare Erinnerungen unterstützen dabei, die Dokumentation fortzuführen.

Das Smartphone bietet sich dafür an, weil Kamera, Speicher und Benachrichtigungen bereits vorhanden sind. Zusätzliche Hardware ist für den geplanten Ablauf nicht vorgesehen. Der Verzicht auf ein Nutzerkonto und die zunächst lokale Speicherung sollen den Einstieg erleichtern. Gleichzeitig ist es bei persönlichen Hautfotos wichtig, dass Nutzer nachvollziehen können, wo ihre Bilder gespeichert werden.

### 1.3 Motivation im Studienprojekt

Für das Modul Mobile Software Engineering ist das Thema interessant, weil es mehrere typische Aufgaben mobiler Entwicklung in einem zusammenhängenden Anwendungsfall verbindet: Kamerazugriff, lokale Datenhaltung, Benachrichtigungen und die Einbindung eines KI-Modells auf dem Gerät. Dabei reicht es nicht, dass die einzelnen Funktionen technisch funktionieren. Auch die Bedienung muss verständlich sein, besonders bei Aufnahmefehlern oder einer nicht möglichen Auswertung.

**Der Schwerpunkt liegt auf einem nachvollziehbaren mobilen Prototyp.** Wir wollen zeigen, wie Aufnahme, experimentelle Auswertung und Dokumentation zusammenspielen. Ob die KI medizinisch zuverlässige Ergebnisse liefert, lässt sich daraus nicht ableiten. Die App ersetzt keine ärztliche Untersuchung; auch eine niedrige angezeigte Risikostufe darf nicht als Entwarnung dargestellt werden.

## 2. Zielgruppe

### 2.1 Primäre Zielgruppe

Die geplante App richtet sich an erwachsene Privatpersonen, die einzelne Muttermale oder andere Hautstellen bewusst dokumentieren möchten. Für das MVP konzentrieren wir uns auf deutschsprachige Nutzer mit einem Android-Smartphone. Medizinische Vorkenntnisse sollen für die Bedienung nicht erforderlich sein.

Im Vordergrund stehen zwei Nutzungssituationen:

- **Regelmäßige Dokumentation:** Eine Person möchte bestimmte Hautstellen über längere Zeit festhalten. Wichtig sind für sie eine einfache Zuordnung, eine übersichtliche Bildhistorie und Erinnerungen.
- **Dokumentation aus einem konkreten Anlass:** Einer Person fällt eine Hautstelle auf, die sie bisher nicht bewusst beobachtet hat. Sie möchte eine Aufnahme speichern und benötigt klare Hinweise dazu, was die App leisten kann und wo ihre Grenzen liegen.

Auch ältere Personen gehören ausdrücklich zur Zielgruppe. Die App soll für sie ebenso verständlich und einfach bedienbar sein wie für jüngere Nutzer. Wir legen deshalb keine enge Altersgruppe fest, sondern orientieren uns am Bedürfnis, Hautstellen zu dokumentieren. Für die Bedienung setzen wir lediglich grundlegende Smartphone-Kenntnisse voraus.

### 2.2 Anforderungen aus der Zielgruppe

Aus diesen Nutzungssituationen ergeben sich folgende Anforderungen:

- **Einfache Sprache:** Begriffe wie „Läsion“ müssen erklärt oder in der Oberfläche durch „Hautstelle“ ersetzt werden.
- **Kurzer, geführter Ablauf:** Von der Auswahl einer Hautstelle bis zur gespeicherten Aufnahme sollen möglichst wenige, verständliche Schritte nötig sein.
- **Gut erkennbare Bedienelemente:** Gut lesbare Schrift, deutliche Kontraste und ausreichend große Schaltflächen sollen die Bedienung auch bei eingeschränktem Sehvermögen oder motorischen Schwierigkeiten erleichtern.
- **Lesbare Ergebnisse:** Risikostufen müssen zusätzlich zur Farbe mit Text erläutert werden. Eine Ampelfarbe allein erklärt weder das Ergebnis noch dessen Unsicherheit.
- **Kontrolle über die eigenen Bilder:** Nutzer sollen gespeicherte Aufnahmen leicht wiederfinden und löschen können.
- **Verständliche Grenzen:** Wenn eine Aufnahme nicht ausgewertet werden kann, muss die App den Grund nennen, statt trotzdem ein Ergebnis anzuzeigen.

### 2.3 Abgrenzung

Hautärzte und medizinische Einrichtungen sind keine primäre Zielgruppe des MVP. Es sind weder eine Praxisverwaltung noch eine direkte ärztliche Beratung innerhalb der App vorgesehen. Angehörige können bei schwer erreichbaren Körperstellen beim Fotografieren helfen; eine eigene Rolle oder ein separates Konto ist dafür zunächst nicht geplant.

Für die KI-Auswertung sieht der Architekturentwurf zusätzliche Einschränkungen nach Alter, Hauttyp und Körperstelle vor. Diese sind als technische Grenzen des geplanten Modells zu verstehen. Ob die konkrete Eingrenzung sachlich ausreicht, muss anhand der verwendeten Daten und der Evaluation geprüft werden. Ein Ausschluss bestimmter Gruppen belegt keine Zuverlässigkeit für die übrigen Nutzer.

**Die beschriebene Zielgruppe ist die Zielgruppe des Konzepts.** Der Studienprototyp ist für die Demonstration und Erprobung der Abläufe gedacht, nicht für medizinische Entscheidungen im Alltag.
