# UrsusData

Sitio web de UrsusData migrado a [Astro](https://astro.build/) y publicado como sitio
estatico en [https://ursusdata.com](https://ursusdata.com).

## Desarrollo

- Requiere Node.js 22 o posterior.
- `npm ci`: instala las dependencias fijadas en `package-lock.json`.
- `npm run dev`: inicia el servidor local de Astro.
- `npm run build`: comprueba los tipos y genera el sitio estatico en `dist/`.
- `npm run preview`: sirve localmente la compilacion.

Las paginas y componentes viven en `src/`; los archivos estaticos publicos se guardan en
`public/`. Astro genera imagenes AVIF/WebP responsivas durante la compilacion a partir de
los originales de `src/assets/images/`.

El formulario de contacto no usa EmailJS ni otro servicio de envio. Al enviarlo, prepara un
mensaje `mailto:` dirigido a `contact@ursusdata.com` en el programa de correo del visitante.
El visitante debe revisar y enviar el mensaje desde ese programa; el navegador no puede
enviarlo por su cuenta ni confirmar la entrega. No requiere claves ni configuracion de
proveedores externos.

La politica de privacidad y los terminos son textos informativos iniciales, no asesoramiento
legal. Revisa su exactitud y adecuacion a tus servicios, proveedores y jurisdicciones antes
de usarlos como documentos legales definitivos.

## Publicacion con GitHub Pages

El workflow `Deploy to GitHub Pages` publica el sitio cuando se actualiza la rama `main`.
En el repositorio publico `JohnPatneo/UrsusData`, configura **Settings > Pages > Build and
deployment > Source** como **GitHub Actions** y establece `ursusdata.com` como dominio
personalizado. Conserva el archivo `CNAME`.

Antes de vincular el dominio al repositorio nuevo, desvinculalo de GitHub Pages en el
repositorio anterior. Espera a que el despliegue nuevo termine correctamente antes de
desconectar el sitio anterior para reducir el tiempo sin servicio.

## DNS del dominio

En Cloudflare, configura los cuatro registros `A` del dominio raiz a estas IP y selecciona
**DNS only** (sin proxy):

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

Configura `www` como `CNAME` a `johnpatneo.github.io`, tambien con **DNS only**. Conserva sin
cambios los registros MX, SPF y DKIM del correo. Cuando GitHub verifique el dominio y emita
el certificado, activa **Enforce HTTPS** en **Settings > Pages**. GitHub Pages fuerza HTTPS
desde esa configuracion del repositorio; el workflow no puede activar esta opcion.