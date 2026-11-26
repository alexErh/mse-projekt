## Android-Entwicklung

Die Android-Anwendung befindet sich in diesem Vezeichnis.

### Voraussetzungen

- Android Studio
- JDK 17
- Android SDK

Das Verzeichnis `android/` kann direkt als Android-Studio-Projekt geöffnet werden.

Vor einem Commit sollten die folgenden Prüfungen lokal erfolgreich durchlaufen:

```bash

./gradlew assembleDebug
./gradlew test
./gradlew lint
```

## Git-Workflow

Die Entwicklung erfolgt in separaten Branches. Änderungen sollten nicht direkt auf `main` entwickelt werden.

Für eine neue Funktion:

```bash
git checkout main
git pull
git checkout -b feature/<kurze-beschreibung>
```

Beispiel:

```bash
git checkout -b feature/camera-screen
```

Für eine Fehlerbehebung:

```bash
git checkout main
git pull
git checkout -b fix/<kurze-beschreibung>
```

Beispiel:

```bash
git checkout -b fix/camera-permission
```

Nach Abschluss der Änderungen:

```bash
git add .
git commit -m "Änderung kurz beschreiben"
git push -u origin <branch-name>
```

Anschließend wird ein Pull Request nach `main` erstellt.

## Continuous Integration

Für das Projekt wird GitHub Actions verwendet. Die Android-CI-Pipeline wird automatisch ausgeführt bei:

- Pushes auf `feature/**`
- Pushes auf `fix/**`
- Pushes auf `main`
- Pull Requests nach `main`

Die Pipeline prüft automatisch:

- ob die Debug-Version gebaut werden kann (`assembleDebug`)
- ob die Unit-Tests erfolgreich durchlaufen (`test`)
- ob Android Lint ohne Fehler durchläuft (`lint`)

Ein Pull Request sollte erst nach erfolgreichem Durchlauf der CI-Pipeline in `main` gemergt werden.