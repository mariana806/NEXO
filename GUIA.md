# Guía completa — App de Contabilidad

## Antes de empezar
Necesitas 3 cuentas gratis: **Supabase** (base de datos), **GitHub** (para subir la app a internet). Ambas son gratis y solo piden correo.

Archivos que ya tienes: `index.html`, `manifest.json`, `sw.js`, `icon.png`, `supabase.sql`.

---

## Paso 1 — Arreglar/crear la base de datos en Supabase

1. Entra a **supabase.com** → "Start your project" → crea cuenta.
2. "New project" → nombre (ej. `mi-contabilidad`) → crea una contraseña **solo con letras y números** (guárdala) → elige la región más cercana → "Create new project". Espera 1-2 min.
3. Menú izquierdo → ícono **`</>` SQL Editor** → "New query".
4. Si ya te salió el error `relation "finanzas" already exists`, pega y corre esto primero (borra la tabla vieja):
   ```sql
   drop table if exists finanzas cascade;
   ```
5. Borra ese texto, abre `supabase.sql`, copia **todo** el contenido, pégalo, dale **Run**. Debe decir "Success. No rows returned".

## Paso 2 — Conseguir tus llaves de conexión

6. Menú izquierdo → engranaje **"Project Settings"** → **"API"**.
7. Copia el **"Project URL"**.
8. Copia la llave **"anon public"** (es larga).

## Paso 3 — Personalizar el diseño antes de subir (opcional pero recomendado)

Abre `index.html` con el Bloc de notas y busca estas partes si quieres cambiarlas:

- **Nombre de la app**: busca `<title>Contabilidad</title>` y `<h1>Contabilidad</h1>` — cambia "Contabilidad" por el nombre que quieras (ej. "Finanzas de Papá").
- **Colores**: cerca del inicio del `<style>` hay líneas como `--ink:#1B2A4A;` y `--gold:#C08A2E;` — son códigos de color (hex), puedes buscar otro color en google "color picker" y reemplazar el código.
- **Nombre del ícono/PWA**: abre `manifest.json`, cambia `"name"` y `"short_name"` por el mismo nombre que pusiste arriba.
- **Ícono**: si quieres un ícono distinto al que te di, reemplaza el archivo `icon.png` por otra imagen cuadrada (idealmente 512x512 px) con el mismo nombre `icon.png`.

## Paso 4 — Conectar la app a tu base de datos

9. En `index.html`, busca `PEGA_AQUI_TU_PROJECT_URL`, bórralo y pega tu Project URL (entre las comillas que ya están).
10. Busca `PEGA_AQUI_TU_ANON_KEY`, bórralo y pega tu anon key (entre comillas).
11. Guarda el archivo (Ctrl+S).

## Paso 5 — Subir la app a internet (GitHub Pages)

12. Entra a **github.com** → crea cuenta.
13. "+" arriba a la derecha → **"New repository"** → nombre (ej. `contabilidad`) → márcalo **Public** → "Create repository".
14. Click en **"uploading an existing file"**.
15. Arrastra `index.html`, `manifest.json`, `sw.js`, `icon.png` (el `.sql` no se sube).
16. "Commit changes".
17. Pestaña **"Settings"** del repositorio → menú izquierdo **"Pages"**.
18. En "Branch" elige **"main"** y **"/ (root)"** → "Save".
19. Espera 1-2 min y recarga esa página de Settings → arriba te muestra tu URL, algo como:
    `https://tu-usuario.github.io/contabilidad/`

## Paso 6 — Descargar / instalar en el celular

20. Abre esa URL desde **Chrome** (Android) o **Safari** (iPhone).
21. La primera vez te pide crear un **PIN** — créalo y no lo olvides.
22. Toca el menú del navegador (3 puntitos, o el ícono de compartir en iPhone) → **"Agregar a pantalla de inicio"** / **"Instalar app"**.
23. Queda como un ícono más en el teléfono, se abre a pantalla completa como cualquier app.

## Paso 7 — Cómo seguir editando la app después

Tienes dos formas, según qué tan grande sea el cambio:

**A) Cambios chiquitos (texto, colores, un número)** — directo desde GitHub, sin descargar nada:
1. Entra a tu repositorio en github.com.
2. Click en el archivo que quieres cambiar (ej. `index.html`).
3. Click en el ícono del lápiz (Edit) arriba a la derecha.
4. Haz el cambio, baja y dale **"Commit changes"**.
5. Espera 1-2 minutos y recarga la app en el navegador — el cambio ya está.

**B) Cambios grandes (agregar funciones nuevas)** — pídemelo aquí en el chat, te doy el código actualizado, y luego repites el Paso 5 (subir los archivos nuevos), reemplazando los que ya estaban en el repositorio (GitHub te va a preguntar si quieres reemplazarlos, dile que sí).

**Importante:** los datos (gastos, ingresos, etc.) viven en Supabase, no en estos archivos — así que puedes cambiar el diseño o subir una versión nueva sin perder nada de lo que ya se registró.
