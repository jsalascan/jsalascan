<h1><em>$ whoami</em></h1>

```
rol       : desarrollador de software / técnico IT
formación : CFGM SMR + CFGS DAW (completado) → Ing. Informática, UOC (en curso)
método    : aprender construyendo, no leyendo tutoriales
```

## Stack

**Lenguajes**

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white) ![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white) ![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white) ![Lua](https://img.shields.io/badge/Lua-2C2D72?style=flat-square&logo=lua&logoColor=white)

**Frameworks / librerías**

![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white) ![Astro](https://img.shields.io/badge/Astro-BC52EE?style=flat-square&logo=astro&logoColor=white) ![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white) ![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) ![WordPress](https://img.shields.io/badge/WordPress-21759B?style=flat-square&logo=wordpress&logoColor=white)

**Despliegue y bases de datos**

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white) ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white) ![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

**Herramientas**

![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white) ![npm](https://img.shields.io/badge/npm-CB3837?style=flat-square&logo=npm&logoColor=white) ![Jira](https://img.shields.io/badge/Jira-0052CC?style=flat-square&logo=jira&logoColor=white) ![Android](https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=android&logoColor=white) ![Discord](https://img.shields.io/badge/Discord-5865F2?style=flat-square&logo=discord&logoColor=white) ![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=flat-square&logo=telegram&logoColor=white)

## Servicios desplegados

### `miportfolio`
Portfolio personal -> [Web en Producción](https://jsalascan.github.io/miportfolio/)

- **Stack:** Astro + Tailwind CSS 4, estático, GitHub Pages.
- **Decisión:** sin framework con runtime en cliente - el contenido no cambia por interacción, así que renderizar todo en build evita cargar JS que no hace falta.
- **Detalle real:** el formulario de contacto no tiene backend propio; entrega el mensaje a Telegram vía un Cloudflare Worker aislado (workspace pnpm separado del sitio). Se despliega a mano - un push a `main` actualiza la web pero no toca el Worker.

### `vue-rolekit`
Kit de componentes Vue 3 (botón, input, select, tabla, tooltip...) -> [Web en Producción](https://jsalascan.github.io/vue-rolekit/) / [Paquete NPM](https://www.npmjs.com/package/vue-rolekit)

- **Stack:** Vue 3 + TypeScript + Vite, build de librería con tipos incluidos.
- **Decisión:** ningún componente usa un control nativo del navegador por debajo - todos construidos desde cero (dropdown propio, tooltip en CSS puro). Más trabajo, pero es lo que obliga a entender cómo se diseña una API de componente en vez de solo consumir una.

### `novals-web`
Web de una comunidad de GTAV: postulaciones, whitelist y panel de staff -> [Web en Producción](https://novals.es/)

- **Stack:** Next.js 16 + Prisma/SQLite + Auth.js con Discord como único proveedor.
- **Decisión:** auth social con Discord en vez de usuario/contraseña propio - la comunidad ya vive en Discord, y es una cuenta menos que gestionar (sin hashing, sin recuperación de contraseña).
- **Detalle real:** los avisos por privado usan la API REST de Discord directamente, sin cola ni proceso aparte. Si el destinatario tiene los DMs del servidor desactivados, Discord devuelve error 50278 ("no mutual guilds") aunque el bot esté dentro - ese caso cae a un aviso en el canal de staff en vez de fallar en silencio.
