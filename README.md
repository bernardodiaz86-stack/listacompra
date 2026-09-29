# Lista de la Compra

Web estática (HTML + JS) con base de datos en tiempo real en Firebase y acceso con contraseña compartida.
Gratis para uso doméstico (plan Spark de Firebase + GitHub Pages).

## Puesta en marcha (una sola vez, ~10 min)

### 1. Crear el proyecto Firebase
1. Entra en https://console.firebase.google.com → **Agregar proyecto** (desactiva Google Analytics, no hace falta).
2. En el proyecto: icono **`</>` (Web)** → registra una app (sin Hosting) → copia el objeto `firebaseConfig`.

### 2. Activar Authentication y Firestore
1. **Build → Authentication → Comenzar → Correo electrónico/contraseña → Habilitar**.
2. Pestaña **Usuarios → Agregar usuario**: correo `compra@lista.app` (el mismo de `authEmail`) y **la contraseña que usaréis los dos** (mín. 6 caracteres).
3. **Build → Firestore Database → Crear base de datos** → modo producción → región `eur3` (Europa).
4. Pestaña **Reglas** → pega el contenido de `firestore.rules` → **Publicar**.

### 3. Pegar la configuración
Edita `firebase-config.js` y rellena `apiKey`, `authDomain`, `projectId` y `appId` con los valores del paso 1.

### 4. Publicar con GitHub Pages
1. Repo → **Settings → Pages** → *Deploy from a branch* → rama `main` (o la que tenga los archivos), carpeta `/ (root)`.
2. En un minuto tendrás la URL `https://<usuario>.github.io/listacompra/`.
3. En Firebase → **Authentication → Configuración → Dominios autorizados**, añade `<usuario>.github.io`.

### 5. Usarla
Abre la URL en el móvil de cada uno, escribe tu nombre y la contraseña. Recuerda la sesión.
En iPhone/Android: menú del navegador → **Añadir a pantalla de inicio**.

## Notas
- La `apiKey` de Firebase es pública por diseño; lo que protege los datos son las reglas de `firestore.rules` (solo usuarios autenticados).
- Si la contraseña se filtra, cámbiala en Firebase → Authentication → Usuarios.
- Pages en repos privados requiere plan de pago de GitHub; con repo público funciona gratis (los datos no están en el repo, solo el código).
