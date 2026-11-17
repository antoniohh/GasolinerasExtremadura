# Plan de Actualización: Migración a `gasolinerasextremadura.es` y Bloque Legal Completo (`v1.4.0`)

- **Fecha:** 16 de noviembre de 2026
- **Proyecto:** Combustible Extremadura (`combustible-extremadura`)
- **Versión objetivo:** `1.4.0`
- **Nuevo dominio oficial:** `https://gasolinerasextremadura.es` (`gasolinerasextremadura.es`)
- **Dominio anterior:** `https://combustible.antoniohorrillo.com`

---

## 1. Objetivo

Actualizar **Combustible Extremadura** siguiendo el mismo estándar arquitectónico, legal y documental aplicado en **Luz Extremadura (`v1.3.0`)**, migrando el portal a su nuevo dominio propio oficial **`https://gasolinerasextremadura.es`** e incorporando el bloque completo de páginas legales, de privacidad y de contacto (**LSSI-CE**, **RGPD**, **LOPDGDD**, **Guía de Cookies de la AEPD** y señales de confianza **Google E-E-A-T**), preparando la versión **`v1.4.0`**.

---

## 2. Fases de Ejecución

### Fase 1: Configuración Canónica del Dominio y SEO (`gasolinerasextremadura.es`)
1. **`public/CNAME`:** Actualizar a `gasolinerasextremadura.es`.
2. **`astro.config.mjs`:** Actualizar `site` a `"https://gasolinerasextremadura.es"`.
3. **`src/lib/site.ts`:**
   - `SITE = "https://gasolinerasextremadura.es"`
   - `SITE_DOMAIN = "gasolinerasextremadura.es"`
   - `AUTHOR_EMAIL = "info@antoniohorrillo.com"`
4. **`public/robots.txt`:** Apuntar a `Sitemap: https://gasolinerasextremadura.es/sitemap.xml`.
5. **`public/sitemap.xml` y `scripts/actualizar_precios_hoy.mjs`:**
   - Cabecera `User-Agent: GasolinerasExtremadura/1.0 (+https://gasolinerasextremadura.es)` en la consulta a MITECO.
   - Sitemap automatizado con las 5 rutas públicas bajo `https://gasolinerasextremadura.es/`:
     - `https://gasolinerasextremadura.es/`
     - `https://gasolinerasextremadura.es/aviso-legal/`
     - `https://gasolinerasextremadura.es/privacidad/`
     - `https://gasolinerasextremadura.es/cookies/`
     - `https://gasolinerasextremadura.es/contacto/`
6. **`public/sw.js`:** Actualizar caché a `combustible-ex-v1.4.0` e incluir las 4 rutas legales/contacto en `STATIC_ASSETS`.

### Fase 2: Bloque de Páginas Legales y de Contacto
1. **`src/pages/aviso-legal.astro` (`/aviso-legal/`):** Datos identificativos del titular conforme al art. 10 LSSI-CE (`info@antoniohorrillo.com`, `antoniohorrillo.com`, `gasolinerasextremadura.es`), condiciones de uso, origen público de los datos (MITECO · Orden ITC/2308/2007 · `FiltroCCAA/11`), carácter orientativo de precios y calculadora, independencia institucional y Licencia MIT.
2. **`src/pages/privacidad.astro` (`/privacidad/`):** Cumplimiento RGPD y LOPDGDD bajo el principio de privacidad desde el diseño, detalle de datos técnicos (GitHub Pages), almacenamiento local (`combustible_extremadura_cookie_consent`, `pwa_install_dismissed`) y analítica opcional (GA4 `G-YSZC0MQCHF` con Consent Mode v2), encargados del tratamiento, conservación y ejercicio de derechos ante el titular y la AEPD (`www.aepd.es`).
3. **`src/pages/cookies.astro` (`/cookies/`):** Tabla técnica detallada de cookies y almacenamiento local en `gasolinerasextremadura.es`, explicación de Google Consent Mode v2, botón interactivo `data-open-cookie-preferences` y navegación rápida entre las 4 páginas.
4. **`src/pages/contacto.astro` (`/contacto/`):** Atención directa con el titular (`info@antoniohorrillo.com` y `antoniohorrillo.com`), soporte técnico en GitHub Issues y orientación al consumidor con enlaces al Geoportal de Gasolineras (MITECO), INCOEX (Junta de Extremadura) y CNMC.

### Fase 3: Componentes de Navegación, Red y Privacidad
1. **`src/components/NetworkBar.astro`:** Actualizar las URLs de `combustible` (`https://gasolinerasextremadura.es/`) y `luz` (`https://luzextremadura.es/`).
2. **`src/components/Footer.astro`:** Actualizar enlace de *Luz Extremadura* a `https://luzextremadura.es/` y renovar la Columna 4 («Información Legal y Privacidad») con los enlaces a `/aviso-legal/`, `/privacidad/`, `/cookies/`, `/contacto/` y el botón de preferencias de cookies.
3. **`src/components/CookieBanner.astro`:** Añadir enlace directo a `/privacidad/` junto a `/cookies/` en el banner y en el modal.

### Fase 4: Documentación, Compilación y Paquete de Release `v1.4.0`
1. Actualizar versión a `1.4.0` en `package.json` y `package-lock.json`.
2. Actualizar `AGENTS.md`, `README.md`, `CHANGELOG.md`, `docs/guia-api-miteco.md`, `docs/sesion-desarrollo.md` y crear `docs/migracion-dominio-y-paginas-legales.md`.
3. Ejecutar `npm run check` y `npm run build:fast`.
4. Generar en `release/`:
   - `release/combustible-extremadura-v1.4.0.zip`
   - `release/combustible-extremadura-v1.4.0.zip.sha256`
   - `release/RELEASE_NOTES_v1.4.0.md`
