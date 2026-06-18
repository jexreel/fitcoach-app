# FitCoach APK — Instrucciones de compilación

## Requisitos previos
- **Android Studio** (descargar en https://developer.android.com/studio)
- **JDK 17+** (incluido con Android Studio)
- **Node.js 18+**

---

## Pasos para generar la APK

### 1. Instalar dependencias
```bash
npm install
```

### 2. Opción A — Android Studio (recomendado)
```bash
npx cap open android
```
Esto abre el proyecto en Android Studio. Luego:
- Menú **Build → Build Bundle(s) / APK(s) → Build APK(s)**
- La APK se genera en `android/app/build/outputs/apk/debug/app-debug.apk`

### 3. Opción B — Línea de comandos
```bash
cd android
./gradlew assembleDebug
```
APK resultante: `android/app/build/outputs/apk/debug/app-debug.apk`

### 4. APK firmada para producción
```bash
cd android
./gradlew assembleRelease
```

---

## Instalar en Android directamente
```bash
# Con el teléfono conectado por USB (modo desarrollador activado)
adb install android/app/build/outputs/apk/debug/app-debug.apk
```

---

## Estructura del proyecto
```
fitcoach-native/
├── www/                  ← App web (HTML/CSS/JS)
│   ├── index.html        ← App completa
│   ├── manifest.json
│   └── sw.js
├── android/              ← Proyecto Android nativo (Capacitor)
│   └── app/
│       ├── src/main/
│       │   ├── assets/public/  ← Web assets copiados aquí
│       │   └── AndroidManifest.xml
│       └── build.gradle
├── capacitor.config.json
└── package.json
```

## App Info
- **Package ID:** com.fitcoach.app
- **Min Android:** 5.1 (API 22)
- **Target Android:** 14 (API 34)
- **Version:** 1.0.0
