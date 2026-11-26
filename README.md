# MSE-Projekt

Projektarbeit im Modul **Mobile Software Engineering** (WS 26/27, THM, Fachbereich MNI).

SkinSentry ist eine Android-Anwendung zur lokalen Unterstützung bei der Dokumentation und Einschätzung von Hautstellen. Die Verarbeitung erfolgt möglichst direkt auf dem Gerät; für den MVP ist kein Backend vorgesehen.

## Struktur

| Ordner | Inhalt |
|---|---|
| `android/` | Android-App (Kotlin, Jetpack Compose) |
| `docs/konzept/` | Projektkonzept (Prüfungsleistung, LaTeX + BibTeX) |
| `docs/ui-mock/` | UI-Mocks / Skizzen |
| `.github/workflows/` | GitHub-Actions-Workflows für Continuous Integration |

## Setup

### Voraussetzungen

- [Android Studio](https://developer.android.com/studio)
- JDK 17
- Android SDK

### Android-App

Siehe [`android/README.md`](android/README.md).

## Git-Workflow

Die Entwicklung erfolgt in separaten Branches.

Für neue Funktionen:

```bash
git checkout -b feature/<kurze-beschreibung>
```

Für Fehlerbehebungen:

```bash
git checkout -b fix/<kurze-beschreibung>
```

Änderungen werden anschließend über einen Pull Request nach `main` integriert.

## Continuous Integration

GitHub Actions prüft automatisch:

- den Debug-Build
- die Unit-Tests
- Android Lint

Die CI-Pipeline wird bei Pushes auf `feature/**`, `fix/**` und `main` sowie bei Pull Requests nach `main` ausgeführt.

## Team

- _Name_ – _Rolle_

