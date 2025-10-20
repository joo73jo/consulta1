# 📱 Implementación de APK con Ionic Angular

Este proyecto corresponde a la **implementación de una aplicación móvil desarrollada con Ionic Angular (standalone)**. Incluye la **configuración de ícono personalizado, splash screen y ajustes del archivo AndroidManifest.xml**, además de la **generación del archivo APK funcional** para su instalación en dispositivos Android.

---

## ⚙️ 1. Creación del proyecto Ionic

1. Instalar Ionic CLI:
   ```bash
   npm install -g @ionic/cli
   ```

2. Crear el proyecto base con pestañas (tabs):
   ```bash
   ionic start consulta1 tabs --type=angular --standalone
   ```

3. Ingresar al directorio y ejecutar:
   ```bash
   cd consulta1
   ionic serve
   ```

---

## 🧩 2. Agregar la plataforma Android

1. Instalar Capacitor y la plataforma:
   ```bash
   npm install @capacitor/android
   npx cap add android
   npx cap sync
   ```

2. Verificar que se haya creado la carpeta `android/` en la raíz del proyecto.

---

## 🎨 3. Ícono personalizado y Splash Screen

1. Crear la carpeta `resources` en la raíz del proyecto:
   ```
   consulta1/
   ├─ android/
   ├─ src/
   ├─ resources/
   │   ├─ icon.png
   │   └─ splash.png
   ```

2. Los tamaños recomendados son:
   - **icon.png:** 1024x1024 px  
   - **splash.png:** 2732x2732 px  

3. Instalar dependencias:
   ```bash
   npm install @capacitor/assets @capacitor/splash-screen
   ```

4. Generar íconos y splash automáticamente:
   ```bash
   npx capacitor-assets generate
   ```

5. Los recursos se generan en:
   ```
   android/app/src/main/res/
   ```

---

## 🧾 4. Configuración de AndroidManifest.xml

Ubicación del archivo:
```
android/app/src/main/AndroidManifest.xml
```

Fragmento principal del código:

```xml
<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/AppTheme">

    <activity
        android:name=".MainActivity"
        android:exported="true"
        android:launchMode="singleTask"
        android:theme="@style/AppTheme.NoActionBarLaunch"
        android:configChanges="orientation|keyboardHidden|screenSize|locale|uiMode|navigation">

        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>

    </activity>

    <uses-permission android:name="android.permission.INTERNET" />

</application>
```

---

## 📦 5. Generación del APK funcional

1. Abrir el proyecto en Android Studio:
   ```bash
   npx cap open android
   ```

2. Ir a:  
   **Build > Build Bundle(s) / APK(s) > Build APK(s)**

3. El archivo se genera en:
   ```
   android/app/build/outputs/apk/debug/app-debug.apk
   ```

4. Subir este archivo a la carpeta `/apk` del repositorio.

---

## 📚 6. Estructura final del proyecto

```
consulta1/
├─ android/
│   └─ app/src/main/AndroidManifest.xml
├─ resources/
│   ├─ icon.png
│   └─ splash.png
├─ apk/
│   └─ app-debug.apk
├─ capacitor.config.ts
├─ README.md
└─ package.json
```

---

## 👨‍💻 Autor

**Joel Parra**  
Escuela Politécnica Nacional – Proyecto de implementación de APK con Ionic Angular  
Año: 2025

---

# 📖 Bibliografía

### 📘 Ícono personalizado en Ionic
La personalización del ícono en aplicaciones Ionic es un proceso esencial para definir la identidad visual del producto. Según la documentación oficial de Capacitor, el uso del comando `npx capacitor-assets generate` permite generar íconos en diferentes resoluciones de manera automática, garantizando compatibilidad con múltiples dispositivos Android e iOS. Esta práctica optimiza la apariencia profesional del aplicativo y refuerza su presencia visual en los entornos móviles.

### 📗 Splash Screen en aplicaciones móviles
El splash screen es la primera pantalla que ve el usuario al abrir una aplicación móvil. En Ionic, se gestiona mediante el plugin `@capacitor/splash-screen`, que permite definir parámetros como duración, color de fondo y escalado de la imagen. Implementar un splash screen adecuado mejora la experiencia del usuario al brindar una transición visual fluida entre el inicio de la aplicación y su carga principal, aportando una sensación de calidad y cuidado en el diseño.

### 📙 Archivo AndroidManifest.xml en Capacitor
El archivo `AndroidManifest.xml` cumple una función central en el ecosistema Android, ya que define los permisos, actividades y configuraciones principales de la aplicación. En el contexto de Ionic con Capacitor, este archivo se encuentra en `android/app/src/main/AndroidManifest.xml` y es modificado para ajustar íconos, temas, permisos de red y comportamientos del `MainActivity`. Su correcta configuración asegura que la aplicación pueda compilarse, ejecutarse y distribuirse de forma óptima en dispositivos Android.
