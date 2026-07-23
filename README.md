# Vireon — MVP (Fase 0)

App de seguimiento de hábitos, alimentación, hidratación, peso, sueño y ánimo.
Funciona 100% en el navegador — los datos se guardan en el dispositivo (localStorage), sin backend.

Pensada para que la uses vos como primera usuaria y compartas tu evolución con tu nutricionista mediante el reporte semanal en PDF (no requiere que tu nutricionista tenga la app instalada).

## Publicarla en GitHub Pages (5 minutos)

1. Andá a https://github.com/new y creá un repositorio (por ejemplo `vireon-app`). Puede ser público.
2. En tu repo, subí estos 5 elementos manteniendo la misma estructura de carpetas:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icons/icon-192.png`
   - `icons/icon-512.png`
   - `icons/icon-maskable-512.png`

   (Botón "Add file" → "Upload files" en GitHub, arrastrás todo incluida la carpeta `icons`.)

3. Andá a **Settings → Pages** del repositorio.
4. En "Source" elegí **Deploy from a branch**, rama `main`, carpeta `/ (root)`. Guardá.
5. Esperá 1-2 minutos. Tu app va a estar en:
   `https://TU-USUARIO.github.io/vireon-app/`

## Instalarla como app

- **Android (Chrome):** abrí el link → menú (⋮) → "Instalar app" o "Agregar a pantalla de inicio".
- **iPhone (Safari):** abrí el link → botón compartir (□↑) → "Agregar a pantalla de inicio".
- **PC (Chrome/Edge):** abrí el link → ícono de instalar en la barra de direcciones.

## Qué incluye esta versión

- Onboarding: elegir Modo Bienestar o Modo Deportivo, nombre, peso objetivo
- Home con racha de constancia, Score de Bienestar, widgets del día
- Registro de comidas (texto libre + foto opcional, sin pedir calorías en Modo Bienestar)
- Hidratación con recipientes personalizables (vaso, botella, termo, etc.)
- Peso corporal con % grasa/músculo, foto y gráfico de evolución
- Sueño, estado de ánimo, entrenamientos
- Cambio entre Modo Bienestar / Modo Deportivo sin perder datos
- Fotos corporales por ángulo (frente/perfil/espalda) con comparación lado a lado y diferencia de peso entre dos fechas
- Reporte semanal en PDF (peso, hábitos, ánimo, Score de Bienestar, fotos comparativas) — botón "Compartir con tu nutricionista" en Ajustes. En celular, abre directamente el menú para enviarlo por WhatsApp o email; en PC, lo descarga.
- Exportar / importar copia de seguridad en JSON
- Instalable y funciona sin conexión (service worker). Nota: el generador de PDF necesita conexión a internet la primera vez que lo usás en cada sesión (carga una librería externa liviana).

## Qué falta (según lo que diseñamos en la arquitectura completa)

Esto es intencionalmente de **un solo usuario, sin nube** — para que la puedas usar hoy mismo.
Lo que sigue, cuando quieras dar el salto:

- Backend real (Supabase/PostgreSQL/Prisma) para que el nutricionista vea tus datos desde otro dispositivo
- Login (Google/Apple/Email) y panel del nutricionista
- IA para reconocer alimentos en la foto y estimar macros automáticamente
- Módulo InBody con lectura automática de PDF/imagen
- Feature flags dinámicos y planes comerciales (Free/Plus/Pro)

El modelo de datos que armamos (`Meal`, `HydrationLog`, `WeightLog`, etc.) ya está pensado para que migrar esta versión a esa base no implique perder ni rediseñar nada — solo conectar cada pantalla a Supabase en vez de a `localStorage`.
