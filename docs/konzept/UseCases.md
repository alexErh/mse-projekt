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
