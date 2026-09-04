# Cuaderno AgroSatCopilot · MICAI 2027

Sitio estático con el estado del artículo: qué es el proyecto, en qué punto está, el plan
desglosado por épicas e historias de usuario, los hallazgos vigentes y el camino de
continuación.

Vive aparte del repositorio del sistema
([`jrebull/agrosat-copilotv2`](https://github.com/jrebull/agrosat-copilotv2)) para que
publicarlo no arrastre 68 GB de datos ni exponga rutas internas.

## Qué hay

```
index.html        resumen, estado y hallazgos, con pestañas
plan.html         15 épicas y 89 historias de usuario con criterios de aceptación
assets/style.css  la hoja de estilo, compartida por las dos páginas
netlify.toml      configuración de despliegue y cabeceras
_headers          las mismas cabeceras, por si se despliega sin leer el toml
robots.txt        prohibición de rastreo
```

Sin compilación, sin dependencias, sin `node_modules`. Son dos HTML, una hoja de estilo y
dos fuentes de Google.

## Desplegar en Netlify

**Desde la interfaz**, que es lo más rápido:

1. Sube este repositorio a GitHub.
2. En Netlify, *Add new site → Import an existing project* y elige el repositorio.
3. Deja el comando de compilación **vacío** y el directorio de publicación en `.`
   (el `netlify.toml` ya lo dice, así que basta con no contradecirlo).
4. *Deploy*.

**Desde la terminal**, si prefieres:

```bash
npm install -g netlify-cli
netlify login
netlify init          # crea el sitio y lo enlaza a este repositorio
netlify deploy --prod --dir .
```

Cada `git push` a la rama por defecto vuelve a desplegar.

## Antes de compartir el enlace, dos cosas

**El sitio no debe indexarse.** Nombra a los dos autores y el artículo va a una revisión a
doble ciego. Por eso lleva `X-Robots-Tag: noindex, nofollow` en las cabeceras y un
`robots.txt` que prohíbe el rastreo. Eso disuade a los buscadores; **no es un control de
acceso**. Si el enlace va a circular fuera del equipo, añade protección por contraseña en
Netlify (*Site configuration → Access & security → Password protection*), que sí lo es.

**Y no enlaces este sitio desde el artículo.** Ni en la versión de envío ni en el
repositorio citado mientras dure la revisión: identificaría a los autores.

## Actualizar el contenido

Las cifras están al final de cada HTML, en arrays de JavaScript con nombres explícitos
(`support`, `members`, `pending`, `EPICS`). Editar una tabla es editar su array.

Cuando cambie una cifra del artículo, la fuente de verdad sigue siendo el registro de
custodia del repositorio principal, `paper/ARTIFACTS.md`. Este sitio la refleja; no la
sustituye.

## Licencia

Documento interno de trabajo. Los autores del código del sistema son Isaac Ávila y
Aaron Bocanegra; los del artículo, Arthur Jafed Zizumbo Velasco y Javier A. Rebull-Saucedo.
