# MSE-Projekt

Projektarbeit im Modul **Mobile Software Engineering** (WS 26/27, THM, Fachbereich MNI).

> Kurzbeschreibung der App: _TODO_

## Struktur

| Ordner | Inhalt |
|---|---|
| `android/` | Android-App (Kotlin, Jetpack Compose) |
| `supabase/` | Backend: Datenbank-Migrationen, Edge Functions, Seed-Daten, Supabase-Konfiguration |
| `docs/konzept/` | Projektkonzept (Prüfungsleistung, LaTeX + BibTeX) |
| `docs/ui-mock/` | UI-Mocks / Skizzen |

## Setup

### Voraussetzungen

- [Android Studio](https://developer.android.com/studio)
- [Supabase CLI](https://supabase.com/docs/guides/local-development/cli/getting-started) (oder per `npx supabase ...`)
- Docker (nur für lokale Supabase-Instanz nötig)

### Backend (Supabase)

```bash
npx supabase login
npx supabase link --project-ref <PROJECT_REF>
npx supabase db pull          # bestehendes Schema als Migration übernehmen
```

Neue Schema-Änderungen immer als Migration anlegen:

```bash
npx supabase migration new <name>
npx supabase db push
```

### Android-App

Siehe [`android/README.md`](android/README.md).

Supabase-URL und Anon-Key gehören in `android/local.properties` (wird nicht eingecheckt):

```properties
SUPABASE_URL=https://<PROJECT_REF>.supabase.co
SUPABASE_ANON_KEY=<anon-key>
```

## Team

- _Name_ – _Rolle_
