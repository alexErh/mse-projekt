# Android-App

Dieser Ordner ist das Root des Android-Studio-Projekts.

## Projekt anlegen

1. Android Studio → **New Project** → **Empty Activity** (Jetpack Compose)
2. Language: **Kotlin**, Build configuration language: **Kotlin DSL**
3. **Save location:** diesen Ordner `android/` wählen
4. Danach diese README behalten und alles committen (die mitgenerierte `.gitignore` ist ok)

## Supabase anbinden

Abhängigkeiten (aktuelle Version siehe [supabase-kt](https://github.com/supabase-community/supabase-kt)):

```kotlin
implementation(platform("io.github.jan-tennert.supabase:bom:<VERSION>"))
implementation("io.github.jan-tennert.supabase:postgrest-kt")
implementation("io.github.jan-tennert.supabase:auth-kt")
implementation("io.ktor:ktor-client-android:<KTOR_VERSION>")
```

URL und Anon-Key aus `local.properties` lesen und per `BuildConfig` bereitstellen – nie im Code einchecken.
