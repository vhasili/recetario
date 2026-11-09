# Recetario da Casa

App web para guardar las recetas de la familia. Se instala en el móvil como una app normal (Android e iPhone), funciona sin conexión y puede guardar todo en una carpeta de Dropbox.

## 1. Publicarla gratis en GitHub Pages

1. Entra en https://github.com (crea una cuenta si no tienes).
2. **New repository** → nombre: `recetario` → **Public** → **Create repository**.
3. **uploading an existing file** → arrastra **todos los archivos de esta carpeta** → **Commit changes**.
4. **Settings → Pages** → *Branch*: `main` y `/ (root)` → **Save**.
5. En un par de minutos estará en `https://TU-USUARIO.github.io/recetario/`.

## 2. Guardar las recetas en Dropbox (recomendado)

Así las recetas no dependen del navegador, y toda la familia trabaja sobre el mismo archivo. Solo lo hace una persona, una vez:

1. Entra en https://www.dropbox.com/developers/apps → **Create app**.
   - *Choose an API*: **Scoped access**.
   - *Type of access*: **Full Dropbox** (hace falta para poder usar una carpeta compartida).
   - *Name*: un nombre único, por ejemplo `Recetario-TuApellido`.
2. Pestaña **Permissions**: marca `files.metadata.read`, `files.content.read` y `files.content.write` → **Submit**.
3. Pestaña **Settings**:
   - *Redirect URIs*: añade exactamente `https://TU-USUARIO.github.io/recetario/` → **Add**.
   - *Allow public clients (Implicit Grant & PKCE)*: **Allow**.
   - *Development users*: pulsa **Enable additional users** para que la familia pueda conectarse.
   - Copia la **App key**.
4. Pon la App key en la app, de una de estas dos formas:
   - **Para toda la familia (mejor):** en GitHub abre `index.html`, pulsa el lápiz ✏️, busca `window.RECETARIO_DROPBOX_KEY = "";`, pega la clave entre las comillas y guarda (**Commit changes**).
   - **Solo en tu móvil:** pégala en ⚙ Ajustes → Guardar en Dropbox.
5. En la app: ⚙ Ajustes → **Guardar en Dropbox** → carpeta (por ejemplo `/Recetario`) → **Conectar con Dropbox** → acepta los permisos.

La app crea `recetario.json` en esa carpeta (y las fotos en `fotos/`). Lee el archivo al abrirse y lo vuelve a guardar unos segundos después de cada cambio. Sin conexión sigue funcionando y sube los cambios al volver la red.

**Compartir con la familia:** en Dropbox, comparte la carpeta `Recetario` con su correo. Cada uno la acepta, instala la app, entra en Ajustes y conecta su propio Dropbox con la misma carpeta. Si dos personas cambian cosas a la vez, se juntan: gana el cambio más reciente de cada receta y se suman las notas de todos. Lo que se borra en un móvil se borra en los demás.

**iPhone:** haz la conexión desde la app ya instalada en la pantalla de inicio, no desde Safari (en iPhone tienen almacenamientos separados).

## 2 bis. O guardar en una carpeta del móvil (solo Android con Chrome)

Sin Dropbox: en ⚙ Ajustes → **Elegir carpeta**, elige o crea una carpeta (por ejemplo `Documentos/Recetario`). La app guarda ahí `recetario.json` y las fotos en `fotos/`.

- Si esa carpeta la sincroniza otra app (por ejemplo Autosync para Google Drive, FolderSync o la app de OneDrive), las recetas quedan también en la nube y otros móviles pueden usar la misma carpeta.
- Android a veces pide confirmar de nuevo el permiso al abrir la app: en ⚙ Ajustes aparecerá **Dar acceso a la carpeta**.
- En iPhone no es posible: Safari no deja a ninguna web usar carpetas del móvil. En iPhone, usa Dropbox.

## 3. Instalarla en el móvil

- **Android (Chrome):** abre en Chrome la dirección `https://TU-USUARIO.github.io/recetario/` → menú ⋮ → **Añadir a pantalla de inicio** → elige **Instalar** (no «Crear acceso directo»). En algunas versiones aparece directamente **Instalar aplicación**, o un aviso abajo para instalarla. Una vez instalada, desde Instagram, TikTok o Chrome podrás pulsar **Compartir → Recetario**.
- **No aparece la opción de instalar** si abres el `index.html` desde el móvil (archivos, WhatsApp, Drive), desde la página del repositorio en github.com o desde el navegador integrado de otra app. Tiene que ser la dirección `github.io` abierta en Chrome.
- **iPhone (Safari):** botón **Compartir** → **Añadir a pantalla de inicio**.

## 4. La IA (opcional)

Sin IA, «Añadir receta» copia el texto con un prompt preparado: lo pegas en ChatGPT o Gemini y traes el JSON con **Importar JSON**.

Con IA, en ⚙ Ajustes elige **Gemini** (uso gratuito; clave en https://aistudio.google.com/apikey con tu Gmail), **ChatGPT** o **Claude** (de pago, aparte de las suscripciones). La clave se guarda solo en ese móvil.

## Actualizar la app

Sube a GitHub los archivos nuevos encima de los anteriores (y vuelve a poner la App key si la tenías en `index.html`). Las recetas no se tocan.
