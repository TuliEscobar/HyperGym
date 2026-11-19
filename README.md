# 🏀 HyperHoops — Hipertrofia + Básquet Tracker

Aplicación web autocontenida en **un solo archivo `.html`** diseñada para registrar entrenamientos de gimnasio (hipertrofia con sobrecarga progresiva), partidos de básquet, nutrición diaria, evolución de peso corporal y métricas interactivas — con respaldo local offline y sincronización con **Google Drive**.

🔗 **App en vivo (GitHub Pages):** https://tuliescobar.github.io/hyperhoops/

---

## ✨ Características principales

- **Un solo archivo (`index.html`):** funciona 100% offline en el gimnasio gracias a `localStorage` y se puede instalar en el celular como app (PWA).
- **Rutina interactiva con pesos "fantasma":**
  - 4 días de gimnasio + modo Partido de Básquet.
  - Cambio rápido de variantes de ejercicio/máquina.
  - Registro por serie con peso, repeticiones, **RIR** (`RIR 2+`, `RIR 1`, `Fallo`) y sugerencia automática de subida de carga (`+2.5 kg`).
  - Temporizador de descanso flotante con sonido (`Tone.js`) y vibración (150s compuestos / 90s analíticos).
- **Combustible (Nutrición y Peso):**
  - Seguimiento rápido de comidas, batido HSN y ajuste automático de calorías en días de básquet (`3200 kcal` → `3400 kcal`).
  - Registro y gráfico de evolución de peso corporal.
- **Panel de 3 Métricas Interactivas (`Chart.js`):**
  1. **Volumen Total por Sesión (kg):** tonelaje movido por entrenamiento y variación porcentual respecto a la sesión anterior.
  2. **Progresión de Fuerza por Ejercicio:** curva de **1RM estimado (fórmula Epley)** y **peso máximo** filtrable por ejercicio.
  3. **Distribución por Tipo de Día:** balance visual entre días de pesas y partidos de básquet.
- **Sincronización con Google Drive (OAuth 2.0):**
  - Cada usuario conecta su propia cuenta de Google (permiso seguro `drive.file`, solo accede a los archivos creados por la app).
  - Crea automáticamente la carpeta `HyperHoops_Gym` en Google Drive con:
    - `hyperhoops_data.json`: respaldo completo para restaurar en cualquier dispositivo.
    - `hyperhoops_metricas.csv`: tabla lista para abrir en **Google Sheets** y armar gráficas personalizadas.
- **Importar / Exportar JSON y CSV:** permite migrar historiales previos y descargar respaldos locales en 1 toque.

---

## 📱 Cómo instalarla en tu celular

1. Abrí **https://tuliescobar.github.io/hyperhoops/** desde el navegador del celular:
   - **Android (Chrome):** tocá el menú `⋮` → **Instalar aplicación** o **Añadir a pantalla de inicio**.
   - **iPhone (Safari):** tocá el botón **Compartir** (`↑`) → **Añadir a pantalla de inicio**.
2. Se abrirá a pantalla completa como una app nativa y guardará tus datos localmente aunque no tengas señal en el gimnasio.

---

## ☁️ Cómo activar Google Drive (OAuth 2.0)

Para que la app pueda guardar `hyperhoops_data.json` y `hyperhoops_metricas.csv` en Google Drive:

1. Entrá a [Google Cloud Console](https://console.cloud.google.com/) y creá un proyecto (gratis).
2. En **APIs & Services → Library**, buscá y habilitá **Google Drive API**.
3. En **APIs & Services → OAuth consent screen**:
   - Elegí **External** y completá el nombre de la app (`HyperHoops`) y tu correo.
   - En **Test users**, agregá tu correo de Gmail (y los correos de cualquier persona con la que quieras compartirla, o publicá la app).
4. En **APIs & Services → Credentials → Create Credentials → OAuth client ID**:
   - Tipo de aplicación: **Web application**.
   - En **Authorized JavaScript origins**, agregá exactamente:
     ```
     https://tuliescobar.github.io
     ```
   - Copiá el **Client ID** generado (`xxxx.apps.googleusercontent.com`).
5. Pegá ese Client ID dentro de la app tocando el botón **Local** (arriba a la izquierda) → **Google OAuth Client ID** → **Conectar con Google Drive**.
   - *(Opcional)* Si querés que cualquier persona que abra tu enlace pueda conectarse sin pegar el Client ID, pegalo en la constante `DEFAULT_GOOGLE_CLIENT_ID` al inicio del `<script>` en `index.html`.

---

## 🔄 Cómo importar tu historial anterior (desde Gemini Canvas)

1. En el chat original de Gemini donde usabas la app, pedile:
   > *"Agregá un botón 'Exportar JSON' en la pestaña Historial que copie al portapapeles `JSON.stringify(appState)`."*
2. Copiá el JSON generado.
3. En HyperHoops, tocá **Local / Drive** (arriba a la izquierda) → **Pegar JSON** → **Cargar Historial Pegado**.

---

## 🛠️ Tecnologías usadas

- HTML5 + JavaScript Vanilla (single-file)
- [Tailwind CSS](https://tailwindcss.com/) (CDN)
- [Phosphor Icons](https://phosphoricons.com/)
- [Chart.js](https://www.chartjs.org/)
- [Tone.js](https://tonejs.github.io/)
- [Google Identity Services + Google Drive API v3](https://developers.google.com/drive)
