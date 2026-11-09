# freeslots-apk

APK Android (WebView plein écran) pour [freeslots.com](https://www.freeslots.com/) — « Free Slots ».

## Fonctionnement

- Package `com.freeslots.app`, minSdk 24 (Android 7.0+), targetSdk 34.
- Charge `https://www.freeslots.com/` en plein écran (JS, DOM storage, cache activés).
- La navigation reste dans l'app sur `*.freeslots.com` ; les liens externes s'ouvrent dans le navigateur.
- Bouton retour géré via l'historique WebView ; état restauré après rotation.

## Build

Prérequis : JDK 17 et Android SDK (`platforms;android-34`, `build-tools;34.0.0`).

```bash
./gradlew assembleRelease
```

L'APK signé est produit dans `app/build/outputs/apk/release/`.
La signature release attend `app/keystore.jks` + `app/keystore.properties` (non versionnés) :

```bash
keytool -genkeypair -keystore app/keystore.jks -alias freeslots -keyalg RSA -keysize 2048 -validity 10000 -dname "CN=FreeSlots, O=FreeSlots, C=FR"
```

## Installation

Transférer l'APK sur l'appareil et l'installer en autorisant les « sources inconnues » (sideload).

> Remarque : ce type de contenu (casino / jeux) ne peut pas être publié tel quel sur le Google Play Store.
