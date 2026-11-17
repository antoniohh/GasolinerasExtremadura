# Migración al Dominio `gasolinerasextremadura.es` y Páginas Legales (LSSI-CE / RGPD / AEPD)

- **Fecha:** 16 de noviembre de 2026
- **Proyecto:** Gasolineras Extremadura (`combustible-extremadura`)
- **Nuevo dominio oficial:** `https://gasolinerasextremadura.es` (`gasolinerasextremadura.es`)
- **Dominio anterior:** `https://combustible.antoniohorrillo.com`

---

## 1. Resumen de Cambios Realizados

### 1.1. Configuración del Dominio Propio (`gasolinerasextremadura.es`) e Identidad `Gasolineras EXTREMADURA`
Se ha actualizado toda la infraestructura e identidad del proyecto para operar bajo el dominio propio `https://gasolinerasextremadura.es` y el nombre **Gasolineras EXTREMADURA**:

- **`public/CNAME`:** Actualizado a `gasolinerasextremadura.es` para la vinculación personalizada en GitHub Pages.
- **`astro.config.mjs`:** Propiedad `site` configurada en `"https://gasolinerasextremadura.es"`.
- **`src/lib/site.ts`, `Header.astro`, `Footer.astro` y `site.webmanifest`:**
  - `SITE = "https://gasolinerasextremadura.es"`
  - `SITE_DOMAIN = "gasolinerasextremadura.es"`
  - `SITE_NAME = "Gasolineras Extremadura"` (`Gasolineras EXTREMADURA` en cabecera y pie)
  - `AUTHOR_EMAIL = "info@antoniohorrillo.com"`
  - Actualización automática de URLs canónicas (`<link rel="canonical">`), etiquetas Open Graph (`og:url`, `og:image`), Twitter Cards y el grafo estructurado JSON-LD (`WebSite`, `WebPage`, `Dataset`, `ItemList`, `FAQPage`, `BreadcrumbList`) en `src/layouts/BaseLayout.astro`.
- **`public/assets/logo.svg` y `public/assets/og-image.png`:** Actualizado el logotipo horizontal y la tarjeta social Open Graph (`1200×630` px) con el título **Gasolineras Extremadura** y el dominio `gasolinerasextremadura.es` (conservando sin cambios los favicons e iconos PWA).
- **`src/components/NetworkBar.astro` y `src/components/Footer.astro`:** Actualizado el enlace del proyecto `combustible` a `https://gasolinerasextremadura.es/` y el del proyecto hermano `luz` a `https://luzextremadura.es/`.
- **`public/robots.txt`:** Apunta a `Sitemap: https://gasolinerasextremadura.es/sitemap.xml`.
- **`public/sitemap.xml` y `scripts/actualizar_precios_hoy.mjs`:**
  - Actualizado el `User-Agent` de consulta a MITECO: `GasolinerasExtremadura/1.0 (+https://gasolinerasextremadura.es)`.
  - Generación automática del sitemap con las 5 rutas públicas bajo `https://gasolinerasextremadura.es/`:
    1. `https://gasolinerasextremadura.es/`
    2. `https://gasolinerasextremadura.es/aviso-legal/`
    3. `https://gasolinerasextremadura.es/privacidad/`
    4. `https://gasolinerasextremadura.es/cookies/`
    5. `https://gasolinerasextremadura.es/contacto/`
- **`public/sw.js`:** Actualizada la caché del Service Worker a `combustible-ex-v1.4.0` e incorporadas las rutas `/aviso-legal/`, `/privacidad/`, `/cookies/` y `/contacto/` en `STATIC_ASSETS`.
- **`package.json`, `AGENTS.md` y `README.md`:** Documentación y metadatos del repositorio sincronizados con `https://gasolinerasextremadura.es`.

---

### 1.2. Creación y Adecuación de Páginas Legales y Contacto
Se ha completado el bloque legal y de transparencia exigido por la normativa española (**Ley 34/2002 LSSI-CE**, **RGPD UE 2016/679**, **LOPDGDD 3/2018** y **Guía de Cookies de la AEPD**), así como las señales de confianza SEO (**Google E-E-A-T**):

1. **Aviso Legal y Condiciones de Uso (`src/pages/aviso-legal.astro` → `/aviso-legal/`):**
   - Identificación del titular conforme al art. 10 LSSI-CE (Antonio Horrillo, `info@antoniohorrillo.com`, `gasolinerasextremadura.es`, `antoniohorrillo.com` y repositorio oficial).
   - Objeto del portal, condiciones de acceso y uso gratuito.
   - Origen público de los datos (Sede Electrónica del MITECO · Geoportal de Gasolineras, Orden ITC/2308/2007, `FiltroCCAA/11`), carácter orientativo de los precios, rankings y calculadora de ahorro, e independencia institucional respecto a estaciones de servicio u operadoras petrolíferas.
   - Propiedad intelectual (código bajo Licencia MIT y reutilización de datos abiertos) y legislación aplicable.
2. **Política de Privacidad (`src/pages/privacidad.astro` → `/privacidad/`):**
   - Información completa de protección de datos (RGPD y LOPDGDD).
   - Principio de privacidad desde el diseño: sin registro de usuarios, sin formularios de captación ni perfiles comerciales.
   - Detalle de datos técnicos de conexión (GitHub Pages), almacenamiento local en el navegador (`localStorage` / `sessionStorage`) y analítica estadística opcional (Google Analytics 4 con IP anonimizada y Consent Mode v2).
   - Base jurídica, encargados del tratamiento, plazos de conservación y ejercicio de derechos con botón interactivo de gestión de consentimiento y referencia a la AEPD (`www.aepd.es`).
3. **Política de Cookies (`src/pages/cookies.astro` → `/cookies/`):**
   - Tabla técnica detallada de cookies y claves de almacenamiento local (`combustible_extremadura_cookie_consent`, `pwa_install_dismissed`, `_ga` y `_ga_YSZC0MQCHF`).
   - Explicación del funcionamiento de **Google Consent Mode v2** (señales `denied` por defecto en el EEE).
   - Botón interactivo para configurar o revocar el consentimiento en cualquier momento.
4. **Contacto y Soporte (`src/pages/contacto.astro` → `/contacto/`):**
   - Tarjetas de contacto directo con el titular (`info@antoniohorrillo.com` y `antoniohorrillo.com`) y canal de soporte técnico / mejoras vía GitHub Issues.
   - Aviso destacado de orientación al consumidor aclarando que `gasolinerasextremadura.es` no es una estación de servicio ni operadora petrolífera y facilitando los enlaces oficiales del **Geoportal de Gasolineras (MITECO)**, **INCOEX (Junta de Extremadura)** y **CNMC** para reclamaciones o consultas oficiales.
   - Garantía de privacidad en las comunicaciones sin almacenamiento en bases de datos intermedias.
5. **Interconexión en Interfaz (`src/components/Footer.astro` y `src/components/CookieBanner.astro`):**
   - Enlaces directos en el pie de página a las 4 páginas (`/aviso-legal/`, `/privacidad/`, `/cookies/`, `/contacto/`) y al configurador de cookies.
   - Barra de navegación rápida en la cabecera de las 4 páginas legales para alternar entre ellas cómodamente.

---

## 2. Estado de Publicación (Release `v1.4.0`)

1. **Correo electrónico de contacto integrado:** `info@antoniohorrillo.com` incorporado en `src/lib/site.ts`, `/contacto/`, `/aviso-legal/` y `/privacidad/`.
2. **Versión `1.4.0` compilada y empaquetada:** Actualizados `package.json`, `CHANGELOG.md`, `README.md`, `docs/sesion-desarrollo.md` y generados los artefactos en `release/` (`combustible-extremadura-v1.4.0.zip`, `.sha256` y `RELEASE_NOTES_v1.4.0.md`).
3. **Configuración DNS y GitHub Pages del dominio `gasolinerasextremadura.es`:**
   - Configurar los registros DNS `A` / `AAAA` del dominio raíz `gasolinerasextremadura.es` apuntando a los servidores de GitHub Pages (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`) y el registro `CNAME` de `www` apuntando a `antoniohh.github.io`.
   - Verificar la activación de HTTPS (`Enforce HTTPS`) en **Settings → Pages** de GitHub.
