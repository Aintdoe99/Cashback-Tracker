# Cashback-Tracker

Diese Repository enthält die BBVA Saveback HTML-App als PWA, so dass du sie leicht als Handy‑App (Android/iOS) verpacken kannst.

Was ich erstellt habe

- index.html (dein HTML, leicht erweitert für PWA/Service Worker)
- manifest.json (Web App Manifest)
- sw.js (einfache Service-Worker-Cache-Strategie)
- icons/ (Platzhalter‑SVGs, auf Wunsch ersetze ich sie durch PNGs)
- package.json (Start-Skript über `serve`)
- capacitor.config.json (Template für Capacitor)

Schnellstart (lokal testen)

1. Klone das Repo:

   git clone https://github.com/Aintdoe99/Cashback-Tracker.git
   cd Cashback-Tracker

2. Starte einen statischen Server (mit npx):

   npm run start

   Die App ist dann unter http://localhost:8080 erreichbar.

PWA / Offline

- Öffne die App im Chrome (oder einem anderen Browser) und du kannst die App als PWA installieren ("Zum Startbildschirm hinzufügen"). Der Service Worker cached die wichtigsten Dateien.

Als native Handy-App (Android / iOS) mit Capacitor verpacken

Hinweis: Das folgende sind die grundlegenden Schritte — du kannst die Dateien anpassen (Icons, appId, Name) bevor du sie verpackst.

1. Lokale Vorbereitung

   npm install --save @capacitor/core @capacitor/cli

2. Capacitor initialisieren (nur einmal)

   npx cap init cashback-tracker com.aintdoe99.cashbacktracker

   Falls du bereits `capacitor.config.json` anpasst hast, prüfe die `webDir` (wir verwenden hier `./` weil die Seite statisch im Repo liegt).

3. Android hinzufügen

   npx cap add android

4. Erstelle (keine Build-Step nötig für statische Dateien), danach synchronisieren

   npx cap copy android
   npx cap open android

   Öffne das Projekt in Android Studio und baue die APK / App-Bundle.

5. iOS (Mac nötig)

   npx cap add ios
   npx cap copy ios
   npx cap open ios

   Öffne das Projekt in Xcode und baue/deploye auf einem Gerät.

Wichtige Hinweise

- Ersetze die Platzhalter-Icons in /icons durch echte PNGs (192x192, 512x512) für bessere Kompatibilität mit Android/iOS.
- Passe `capacitor.config.json` und `manifest.json` an (appId, name, start_url) bevor du die App veröffentlichst.
- Wenn deine App Assets aus externen Domains lädt, passe die Service-Worker-Strategie entsprechend an.

Wenn du möchtest übernehme ich:

- Icons in PNG-Größen erstellen und hinzufügen
- Capacitor-Setup direkt im Repo (npm deps, initialisierung, android/ios config) und die ersten Schritte ausführen
- Ein GitHub Action workflow zum Deploy der statischen Seite auf GitHub Pages

Sag mir, welche dieser Optionen ich für dich jetzt ausführen soll.
