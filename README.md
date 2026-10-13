# UrsusData

Sitio web estatico de UrsusData, publicado en [https://ursusdata.com](https://ursusdata.com).

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
el certificado, activa **Enforce HTTPS** en **Settings > Pages**.