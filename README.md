# 🏋️ HyperGym — Tracker Universal de Gimnasio, Nutrición y Métricas

Aplicación web autocontenida en **un solo archivo `.html`** pensada para cualquier persona que quiera registrar sus entrenamientos de gimnasio, nutrición, peso corporal y métricas de progreso — con funcionamiento 100% offline y sincronización con **Google Drive**.

🔗 **App en vivo (GitHub Pages):** https://tuliescobar.github.io/hyperhoops/

---

## ✨ Características principales

- **Un solo archivo (`index.html`):** instalable como app en Android e iPhone (PWA) y 100% funcional offline con `localStorage`.
- **4 Programas de Entrenamiento listos para usar** *(cambiables en cualquier momento sin perder tu historial ni pesos fantasma)*:
  1. **Hipertrofia + Deporte (4 días + Cardio/Deporte):** 4 días de hipertrofia + sesiones deportivas (básquet, fútbol, etc.) con opción de 1 o 2 partidos por semana.
  2. **Reducción de Peso / Quema Grasa:** 3 días Full Body metabólico + Cardio Zona 2 / HIIT con metas en déficit calórico.
  3. **Push / Pull / Legs (PPL Estándar):** clásico de 3 a 6 días (Empuje, Tirón, Pierna + Cardio opcional).
  4. **Torso / Pierna Estándar (4 días):** frecuencia 2 equilibrada (Torso A/B + Pierna A/B).
- **Rutina 100% editable:**
  - **Editar cualquier ejercicio** (nombre, rango de repeticiones, tiempo de descanso o eliminarlo del día) con el botón ✏️.
  - Cambio rápido entre variantes de máquinas/ejercicios y opción de agregar ejercicios personalizados.
  - Registro por serie con peso, repeticiones, **RIR** (`RIR 2+`, `RIR 1`, `Fallo`), pesos "fantasma" de tu sesión anterior y sugerencia automática de sobrecarga (`+2.5 kg`).
  - Temporizador flotante de descanso con sonido (`Tone.js`) y vibración.
- **Perfil y Nutrición personalizables:**
  - Editá tu estatura, peso meta, objetivo (Hipertrofia, Reducción de Peso o Recomposición), calorías diarias, proteína y bonus de cardio.
  - Ideas rápidas de comidas y snacks adaptadas automáticamente a tu objetivo.
- **Panel de 3 Métricas Interactivas (`Chart.js`):**
  1. **Volumen Total por Sesión (kg):** tonelaje movido y variación % vs sesión anterior.
  2. **Progresión de Fuerza por Ejercicio:** curva de **1RM estimado (fórmula Epley)** y **peso máximo**.
  3. **Distribución por Tipo de Sesión:** balance visual entre días de pesas y cardio/deporte.
- **Sincronización con Google Drive (OAuth 2.0):**
  - Cada usuario conecta su propia cuenta de Google (permiso seguro `drive.file`).
  - Guarda automáticamente en `Google Drive / HyperGym_Data`:
    - `hypergym_data.json`: respaldo completo para restaurar en cualquier celular.
    - `hypergym_metricas.csv`: tabla lista para abrir en **Google Sheets** y crear tus propias métricas.

---

## 📱 Cómo instalarla en tu celular

1. Abrí **https://tuliescobar.github.io/hyperhoops/** desde el navegador del celular:
   - **Android (Chrome):** menú `⋮` → **Instalar aplicación** / **Añadir a pantalla de inicio**.
   - **iPhone (Safari):** botón **Compartir** (`↑`) → **Añadir a pantalla de inicio**.

---

## ☁️ Cómo activar Google Drive (OAuth 2.0)

1. Entrá a [Google Cloud Console](https://console.cloud.google.com/) y creá un proyecto (gratis).
2. En **APIs & Services → Library**, habilitá **Google Drive API**.
3. En **APIs & Services → OAuth consent screen**:
   - Elegí **External**, completá el nombre (`HyperGym`) y tu correo.
   - En **Test users**, agregá tu correo de Gmail (y los correos de quienes quieras que la prueben, o publicá la app).
4. En **APIs & Services → Credentials → Create Credentials → OAuth client ID → Web application**:
   - En **Authorized JavaScript origins**, agregá exactamente:
     ```
     https://tuliescobar.github.io
     ```
   - Copiá el **Client ID** (`xxxx.apps.googleusercontent.com`).
5. Pegá el Client ID dentro de la app tocando **Local** (arriba a la izquierda) → **Google OAuth Client ID** → **Conectar con Google Drive** *(o dejalo fijo en `DEFAULT_GOOGLE_CLIENT_ID` en `index.html`)*.

---

## 🔄 Importar historial previo

Tocá el botón **Local / Drive** (arriba a la izquierda) → **Importar JSON** o **Pegar JSON** para cargar cualquier respaldo anterior (compatible con versiones previas de HyperHoops / Gemini Canvas).
