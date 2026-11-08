# Hautkrebs-Erkennungs-Apps: Marktanalyse & MVP-Features

Nov 3, 2026 · @Al

## Kurzfazit

Ein MVP für eine Hautkrebs-App braucht genau sechs Dinge: geführte Fotoaufnahme mit Qualitätsprüfung, KI-Risikoeinstufung in drei Stufen, klare Handlungsempfehlung, Läsions-Verlauf mit Erinnerungen, Bericht zum Teilen mit dem Arzt sowie DSGVO-konforme Datenhaltung. Alles Weitere (Ganzkörper-Mapping, Dermatoskop-Anbindung, Telemedizin-Rezepte, Integrationen) gehört in spätere Releases.

- **Der Markt teilt sich in vier Modelle:** KI-Selbsttest für Verbraucher (SkinVision, SkinScreener), reine Muttermal-Dokumentation (Miiskin, UMSkinCheck), Teledermatologie mit echten Hautärzten (Dermanostic, OnlineDoctor) und professionelle Klinik-Tools (Skin Analytics DERM, DermaSensor, DermEngine).
- **Die eigentliche Hürde ist nicht die Technik, sondern die Zulassung:** Jede App mit Risikoaussage ist ein Medizinprodukt. Die Marktführer sind nach EU-MDR mindestens Klasse IIa zertifiziert; Skin Analytics hat als einziger Anbieter Klasse III für autonome Entscheidungen.
- **Vertrauen entscheidet:** Dermatologen-Verbände in Deutschland sehen reine KI-Diagnosen kritisch. Ein MVP sollte daher als Triage- und Dokumentationswerkzeug positioniert sein, nicht als Diagnose.

## Marktüberblick

Analysiert wurden zehn Anwendungen aus vier Kategorien; die Tabelle ist nach Kategorie sortiert, Verbraucher-KI zuerst.

| Anwendung | Kategorie | Zielgruppe | Kernansatz | Zulassung / Evidenz | Preismodell |
| --- | --- | --- | --- | --- | --- |
| [SkinVision](https://healthify.nz/apps/s/skinvision-app) (NL) | KI-Selbsttest | Verbraucher, Versicherte | Foto eines Flecks → KI-Risiko in Stufen, bei hohem Risiko Prüfung durch Dermatologen innerhalb 48 h | EU-MDR Klasse IIa (Aug. 2025); laut eigenen Angaben über 3,5 Mio. Checks | Einzelcheck oder 3/12-Monats-Pakete; Vertrieb stark über Krankenversicherer |
| [SkinScreener](https://apps.apple.com/DE/app/id6446895764) (AT) | KI-Selbsttest | Erwachsene, Hauttyp I–IV; auch betriebliche Gesundheitsförderung | Foto → Ampel grün/gelb/rot | MDR Klasse IIa, ISO 13485; Studie MedUni Graz mit >95 % Sensitivität/Spezifität | 2 Test-Scans gratis, dann Abo (6 Monate 24,99 €) |
| [Skinive / Skin Scanner](https://www.similarweb.com/app/apple/1633219654/germany/) | KI-Selbsttest + Hautpflege | Verbraucher | Hautanalyse, Risiko, Pflegeempfehlungen, UV-Hinweise | CE-markiert | Freemium |
| [Miiskin](https://www.molemap.net.au/skin-cancer/skin-check-app) (DK) | Monitoring + Teledermatologie | Verbraucher | Muttermal-Mapping, Vergleich, Größenmessung, freihändige Ganzkörperfotos; keine KI-Risikoaussage | – | Abo, Arztbesuche (Rx) |
| [UMSkinCheck](https://www.molemap.net.au/skin-cancer/skin-check-app) (US) | Selbstuntersuchung | Verbraucher | Anleitung zur Selbstuntersuchung, Erinnerungen | kein Medizinprodukt mit Risikoaussage | kostenlos |
| [Dermanostic](https://www.dm.de/services/gesundheitsdienstleistungen/dermanostic) (DE) | Teledermatologie | Patienten, auch über dm | 3 Fotos + Anamnese → Diagnose, Therapie und ggf. Rezept durch deutsche Fachärzte in 24 h; zusätzlich KI-Hauttyp-Analyse | Online-Arztpraxis | ca. 25 € pro Fall |
| [OnlineDoctor](https://www.kkh.de/leistungen/praevention-vorsorge/vorsorgeuntersuchungen/onlinedoctor) (DE/CH) | Teledermatologie | Patienten, Krankenkassen | Foto-Einsendung an Hautarztpraxen; mit dem BVDD gegründet; Server in Deutschland | ärztliche Leistung | Selbstzahler oder Kasse |
| [MoleScope / DermEngine](https://www.dermengine.com/molescope) (CA) | Dermatoskopie + Klinik-Software | Patienten und Praxen | Aufsteck-Dermatoskop, 3D-Bodymap, Ganzkörperfotografie, automatisches Mole-Matching | Klinik-Software | Hardware + Lizenz |
| [Skin Analytics DERM / DERM Zero](https://www.prnewswire.com/no/pressemeldinger/the-ai-from-skin-analytics-that-caught-20-000-cancers-in-the-uk-is-now-certified-for-use-on-a-standard-smartphone-302800754.html) (UK) | Autonome KI im Versorgungspfad | NHS, Versicherer, Provider | Läsion → Entscheidung „keine weitere Maßnahme“ oder Überweisung; DERM Zero seit Juni 2026 ohne Dermatoskop | Einziges KI-Medizinprodukt mit CE Klasse III; >230.000 NHS-Patienten, >20.000 Krebsfälle erkannt | B2B |
| [DermaSensor](https://mdedge.com/content/fda-clears-ai-powered-device-noninvasive-skin-cancer-testing) (US) | Handgerät für Hausärzte | Primärversorgung | Spektroskopie + KI für Melanom, BCC, SCC | FDA-Freigabe Jan. 2024; Sensitivität 95,5 % in der Zulassungsstudie | Abo 199–399 $/Monat |

Wichtig für die Einordnung: Ältere, nicht validierte Apps schnitten in Studien teils katastrophal ab – ein [systematischer Review](https://nottingham-repository.worktribe.com/output/3950182) fand für SkinScan 0 % Sensitivität bei Melanomen. Klinische Validierung ist deshalb kein Extra, sondern Marktvoraussetzung.

## Feature-Katalog

Aus den zehn Anwendungen ergeben sich 30 Features in sieben Bereichen. Spalte „Gesehen bei“ zeigt, welche Anbieter das Feature umsetzen.

| # | Bereich | Feature | Beschreibung | Gesehen bei |
| --- | --- | --- | --- | --- |
| 1 | Bildaufnahme | Geführte Kameraaufnahme | Overlay, Abstand, Fokus, automatischer Auslöser | SkinVision, SkinScreener, DERM Zero |
| 2 | Bildaufnahme | Bildqualitätsprüfung | Unschärfe, Licht, Haare, Ausschnitt erkennen und Neuaufnahme verlangen | SkinVision, DermEngine |
| 3 | Bildaufnahme | Mehrere Perspektiven pro Läsion | z. B. 3 Fotos (Nah, Übersicht, Kontext) | Dermanostic, OnlineDoctor |
| 4 | Bildaufnahme | Dermatoskop-Anbindung | Aufsteck-Dermatoskop für Auflicht-Bilder | MoleScope, DERM |
| 5 | Bildaufnahme | Ganzkörperfotografie | Standardisierte Posen, „Ghost“-Vorlage, freihändig | Miiskin, DermEngine |
| 6 | KI-Analyse | Risikoeinstufung | 3 Stufen (niedrig / mittel / hoch, Ampel) | SkinVision, SkinScreener, Skinive |
| 7 | KI-Analyse | Multiklassen-Klassifikation | Melanom, BCC, SCC, benigne Läsionen getrennt | DERM, DermaSensor |
| 8 | KI-Analyse | Symptom-Fragebogen | Juckreiz, Blutung, Veränderung fließen ins Ergebnis | SkinVision („niedrig mit Symptomen“) |
| 9 | KI-Analyse | Erklärbarkeit / ABCDE-Hinweise | Zeigt, welche Merkmale auffällig sind | MoleScope (ABCD-Lernanalyse) |
| 10 | KI-Analyse | Ausschluss ungeeigneter Fälle | Kinder, Hauttyp V–VI, Schleimhaut, Nägel → direkt zum Arzt | SkinScreener (Hauttyp I–IV), NICE-Auflage bei DERM |
| 11 | Ergebnis | Handlungsempfehlung | „Beobachten in 3 Monaten“ vs. „Arzt aufsuchen mit Dringlichkeit“ | SkinVision, SkinScreener, DERM Zero |
| 12 | Ergebnis | Dermatologen-Zweitprüfung | Hautarzt prüft Hochrisiko-Ergebnisse (z. B. binnen 48 h) | SkinVision |
| 13 | Ergebnis | PDF-Bericht / Export | Ergebnis zum Arzt mitnehmen oder teilen | SkinVision |
| 14 | Monitoring | Läsions-Profil & Verlauf | Jede Stelle mit eigener Bildhistorie | SkinVision, Miiskin, MoleScope |
| 15 | Monitoring | 2D/3D-Bodymap | Läsionen am Körper verorten | SkinVision, MoleScope, DermEngine |
| 16 | Monitoring | Seitenvergleich & Vergrößerung | Alt vs. neu nebeneinander | Miiskin, DermEngine |
| 17 | Monitoring | Größenmessung | Durchmesser über die Zeit | Miiskin, DermEngine |
| 18 | Monitoring | Automatische Änderungserkennung | Neue oder veränderte Male finden, nach Änderung priorisiert | DermEngine (Mole-Match), CORDIS-Projekt |
| 19 | Engagement | Erinnerungen | Push/E-Mail/SMS, 0–6 Monate einstellbar | SkinVision, UMSkinCheck, MoleScope |
| 20 | Engagement | Risikoprofil-Quiz & Hauttyp | Fitzpatrick-Typ, Risikofaktoren | SkinVision, MoleMap, Dermanostic |
| 21 | Engagement | UV-Index & Prävention | Lokaler UV-Wert, Schutzhinweise | SkinVision, Skinive |
| 22 | Engagement | Wissen / Hautlexikon | ABCDE-Regel, Krankheitsbilder | Dermanostic, UMSkinCheck |
| 23 | Versorgung | Teledermatologie-Fall | Fall an Facharzt mit Anamnese senden | Dermanostic, OnlineDoctor, Miiskin |
| 24 | Versorgung | E-Rezept & Therapieplan | Verordnung nach Online-Diagnose | Dermanostic |
| 25 | Versorgung | Arzt-/Praxisportal | Web-Dashboard, Patientenverwaltung, Überweisung | DermEngine, DERM |
| 26 | Versorgung | Integration in Versicherer/KIS | Zugang über Kassen-App, NHS-Pfade | SkinVision, DERM, OnlineDoctor |
| 27 | Plattform | Konto & Einwilligung | Registrierung, Einwilligungen, Altersprüfung | alle |
| 28 | Plattform | Datenschutz & Sicherheit | Verschlüsselung, EU-Server, ISO 27001 | SkinVision, OnlineDoctor, DERM |
| 29 | Plattform | Bezahlung | Einzelkauf, Abo, B2B-Lizenz | alle kommerziellen |
| 30 | Plattform | Post-Market-Surveillance | Ergebnis-Feedback, Biopsie-Abgleich, Modell-Monitoring | DERM, DermaSensor |

## MVP-Einstufung

Ins MVP gehören 11 der 30 Features: alles, was nötig ist, damit ein Nutzer eine Stelle sicher fotografieren, eine verantwortbare Einschätzung erhalten und den Verlauf beobachten kann. Annahme: Verbraucher-App (B2C) im DACH-Raum mit KI-Risikoeinstufung.

| Priorität | Feature (# aus Katalog) | Begründung |
| --- | --- | --- |
| **MVP – Muss** | Geführte Kameraaufnahme (1) | Bildqualität bestimmt die KI-Genauigkeit; Laien-Fotos sind die größte Fehlerquelle |
| **MVP – Muss** | Bildqualitätsprüfung (2) | Verhindert falsche Ergebnisse aus unscharfen Bildern; wird von Prüfstellen erwartet |
| **MVP – Muss** | Risikoeinstufung in 3 Stufen (6) | Kernnutzen; Ampel ist Marktstandard und leicht verständlich |
| **MVP – Muss** | Ausschluss ungeeigneter Fälle (10) | Sicherheitsanforderung: Kinder, dunkle Hauttypen, Sonderlokalisationen direkt an den Arzt |
| **MVP – Muss** | Handlungsempfehlung (11) | Ohne klare nächste Schritte ist die Risikoaussage wertlos oder gefährlich |
| **MVP – Muss** | Läsions-Profil & Verlauf (14) | Veränderung ist das stärkste Melanom-Signal; begründet wiederholte Nutzung |
| **MVP – Muss** | Erinnerungen (19) | Treibt Retention und regelmäßige Kontrolle (typisch alle 3 Monate) |
| **MVP – Muss** | PDF-Bericht / Export (13) | Brücke zum Hautarzt; stärkt Akzeptanz bei Ärzten |
| **MVP – Muss** | Konto & Einwilligung (27) | Gesundheitsdaten nach Art. 9 DSGVO brauchen ausdrückliche Einwilligung |
| **MVP – Muss** | Datenschutz & Sicherheit (28) | EU-Hosting und Verschlüsselung sind in Deutschland Kaufkriterium |
| **MVP – Muss** | Post-Market-Surveillance, Basis (30) | MDR-Pflicht; mindestens Feedback „Arztbefund erhalten?“ und Fehlerlogging |
| Release 2 – Sollte | Symptom-Fragebogen (8), Seitenvergleich (16), einfache 2D-Bodymap (15), Risikoprofil & Hauttyp (20), Bezahlung/Abo (29) | Verbessern Genauigkeit, Bedienung und Monetarisierung, sind aber für den Nachweis des Kernnutzens nicht zwingend |
| Release 2 – Sollte | Dermatologen-Zweitprüfung (12) | Großer Vertrauensgewinn; braucht aber Ärzte-Netzwerk und Prozesse |
| Release 3 – Kann | UV-Index (21), Wissen/Lexikon (22), Erklärbarkeit/ABCDE (9), Mehrere Perspektiven (3), Größenmessung (17) | Nette Ergänzungen für Engagement und Differenzierung |
| Später | Ganzkörperfotografie (5), automatische Änderungserkennung (18), 3D-Bodymap (15), Dermatoskop (4), Multiklassen-KI (7) | Technisch aufwendig, teils höhere Risikoklasse |
| Später | Teledermatologie (23), E-Rezept (24), Arztportal (25), Versicherer-/KIS-Integration (26) | Eigenes Geschäftsmodell (Arztpraxis, B2B); erst nach Produkt-Markt-Fit |

Wer ohne eigene KI-Zulassung starten will, kann das MVP auch als reine Dokumentations-App (Modell Miiskin) bauen: dann entfallen 6, 10 und 11, und Feature 23 (Teledermatologie über Partnerpraxen) rückt ins MVP.

## Regulatorik und Risiken

Sobald die App eine Risikoaussage trifft, ist sie Medizinprodukt-Software nach EU-MDR und braucht realistisch Klasse IIa mit Benannter Stelle – das ist der längste Pfad im MVP-Plan.

- **Zulassung:** Vergleichbare Apps (SkinVision, SkinScreener) sind MDR Klasse IIa; Voraussetzung sind QMS nach ISO 13485, Risikomanagement nach ISO 14971, Software-Lebenszyklus nach IEC 62304 und eine klinische Bewertung. Hinzu kommen Pflichten aus dem EU AI Act für Hochrisiko-KI.
- **Klinische Evidenz:** Eine prospektive Studie mit Laien-Fotos und histologischer Referenz ist faktisch Pflicht; SkinScreener wurde etwa an der MedUni Graz mit 238 Patienten validiert.
- **Hauttyp-Bias:** Trainingsdaten sind überwiegend hellhäutig. SkinScreener schließt Hauttyp V–VI aus, und die NICE-Leitlinie verlangt bei DERM ärztliche Prüfung für schwarze und braune Haut.
- **Akzeptanz bei Ärzten:** Der BVDD sieht die Beurteilung neuer oder veränderter Muttermale allein per App sehr kritisch. Positionierung als Triage mit Arzt-Bericht entschärft das.
- **Fehlalarme:** Zu viele Hochrisiko-Ergebnisse überlasten Praxen und frustrieren Nutzer; Spezifität muss neben Sensitivität ein Zielwert sein.
- **Datenschutz:** Gesundheitsdaten nach Art. 9 DSGVO, EU-Hosting, Löschkonzept und keine Weitergabe an Tracking-SDKs.

## Quellen

- [SkinVision – Healthify NZ App-Review (2025)](https://healthify.nz/apps/s/skinvision-app)
- [SkinVision über Benenden Health](https://www.benenden.co.uk/health/skinvision/)
- [SkinVision im App Store](https://apps.apple.com/sa/app/id545293136)
- [SkinScreener im App Store (DE)](https://apps.apple.com/DE/app/id6446895764)
- [MedUni Graz – Presseinfo SkinScreener-Studie](https://typo3-migration.medunigraz.at/frontend/user_upload/themen-pr/presseinformationen/2023/presseinfo-hautkrebs-skinscreener_WEB.pdf)
- [MoleMap – Wie effektiv sind Skin-Check-Apps?](https://www.molemap.net.au/skin-cancer/skin-check-app)
- [Skin Analytics – DERM Zero Pressemitteilung (Juni 2026)](https://www.prnewswire.com/no/pressemeldinger/the-ai-from-skin-analytics-that-caught-20-000-cancers-in-the-uk-is-now-certified-for-use-on-a-standard-smartphone-302800754.html)
- [Skin Analytics – Übersicht inkl. NICE-Auflagen](https://yespress.io/skin-analytics.md)
- [DermaSensor FDA-Freigabe – MDedge](https://mdedge.com/content/fda-clears-ai-powered-device-noninvasive-skin-cancer-testing)
- [DermEngine / MoleScope](https://www.dermengine.com/molescope)
- [MoleScope App-Features](https://apps.appfollow.io/ios/molescopetm/1003576096?country=br)
- [Dermanostic bei dm](https://www.dm.de/services/gesundheitsdienstleistungen/dermanostic)
- [OnlineDoctor bei der KKH](https://www.kkh.de/leistungen/praevention-vorsorge/vorsorgeuntersuchungen/onlinedoctor)
- [Apotheke adhoc – BVDD zu Hautcheck-Apps](https://www.apotheke-adhoc.de/nachrichten/detail/pta-live/hautkrebsdiagnose-per-app-besser-zum-dermatologen/)
- [Systematischer Review zur Genauigkeit von Hautkrebs-Apps (Dinnes et al.)](https://nottingham-repository.worktribe.com/output/3950182)
