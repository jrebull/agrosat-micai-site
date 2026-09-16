# Cuaderno AgroSatCopilot · MICAI 2027

Sitio estático con el estado del artículo: qué es el proyecto, en qué punto está, el plan
desglosado por épicas e historias de usuario, los hallazgos vigentes y el camino de
continuación.

Vive dentro de [`site/`](./) en el mismo repositorio que el artículo, sus artefactos y sus
controles. Netlify publica únicamente este subdirectorio: los datos y las rutas internas del
monorepo no forman parte del despliegue.

## Qué hay

```
index.html        resumen, estado y hallazgos, con pestañas
plan.html         15 épicas y 89 historias de usuario con criterios de aceptación
assets/style.css  la hoja de estilo, compartida por las dos páginas
../netlify.toml   configuración de despliegue y cabeceras desde la raíz del monorepo
_headers          las mismas cabeceras, por si se despliega sin leer el toml
robots.txt        prohibición de rastreo
```

Sin compilación, sin dependencias, sin `node_modules`. Son dos HTML, una hoja de estilo y
dos fuentes de Google.

## Desplegar en Netlify

**Desde la interfaz**, que es lo más rápido:

1. Sube el monorepo `jrebull/agrosat-copilotv2` a GitHub.
2. En Netlify, *Add new site → Import an existing project* y elige ese repositorio.
3. Deja el comando de compilación **vacío** y el directorio de publicación en `site`
   (el `netlify.toml` de la raíz ya lo declara).
4. *Deploy*.

**Desde la terminal**, si prefieres:

```bash
npm install -g netlify-cli
netlify login
netlify init          # ejecutado desde la raíz del monorepo
netlify deploy --prod --dir site
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
(`support`, `members`, `pending`, `EPICS`). Editar una tabla es editar su array. El historial
diario de `plan.html` se agrupa por la fecha local del commit de evidencia: cada fila identifica
la US afectada, el tipo de avance y un commit del repositorio principal. No se añaden logros sin
ese ancla ni commits del sitio que solo reflejen el mismo cambio. Los gráficos por día y por autor
se derivan en el navegador de esas mismas filas; sus totales no se mantienen por separado. Cada
barra diaria está apilada por autor Git y comparte sus colores con el tablero de autores.

Cuando cambie una cifra del artículo, la fuente de verdad sigue siendo el registro de
custodia del repositorio principal, `paper/ARTIFACTS.md`. Este sitio la refleja; no la
sustituye.

## Licencia

Documento interno de trabajo. Los autores del código del sistema son Isaac Ávila y
Aaron Bocanegra; los del artículo, Arthur Jafed Zizumbo Velasco y Javier A. Rebull-Saucedo.
