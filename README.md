# Contra La Tribu — proyecto bookdown

## Estructura

- `index.Rmd` — YAML del libro (título, autor, formato PDF, paquetes LaTeX). No contiene texto de capítulo.
- `00-introduccion.Rmd` — ensayo introductorio (pendiente de redactar).
- `01-adam-smith.Rmd` a `04-popper.Rmd` — cuadernillos ya transcritos, listos para migrar contenido.
- `05-aron.Rmd`, `06-berlin.Rmd`, `07-revel.Rmd` — cuadernillos pendientes de transcripción.
- `_bookdown.yml` — define el orden de los capítulos y el nombre del libro compilado.

## Migración del contenido existente

Tu .Rmd actual tiene todo el texto en un solo archivo, corregido en secuencia.
Para migrar:

1. Abre tu .Rmd actual y ubica dónde empieza y termina cada cuadernillo.
2. Copia el bloque correspondiente a cada pensador y pégalo en su archivo nuevo
   (por ejemplo, todo el bloque de Adam Smith va a `01-adam-smith.Rmd`).
3. Baja un nivel los encabezados internos de cada bloque:
   - `#` pasa a ser `##`
   - `##` pasa a ser `###`
   (El `#` de nivel 1 en cada archivo nuevo ya está reservado para el título del
   capítulo — no lo dupliques.)
4. Revisa que no se haya copiado el YAML original dentro de los archivos de
   capítulo — solo `index.Rmd` debe llevar YAML.

## Cómo compilar

Con el paquete `bookdown` instalado (`install.packages("bookdown")`):

- Libro completo: en la consola de R, `bookdown::render_book("index.Rmd")`,
  o el botón **Build Book** en el panel Build de RStudio (aparece automáticamente
  al abrir esta carpeta como proyecto, gracias a `site: bookdown::bookdown_site`
  en el YAML).
- Vista previa de un solo capítulo (mucho más rápido mientras corriges):
  `bookdown::preview_chapter("05-aron.Rmd")`.

El PDF resultante se genera en la carpeta `_book/`.

## Próximo paso natural

Una vez migrado el contenido de los cuatro cuadernillos cerrados, conviene
correr `render_book()` una vez para confirmar que el PDF se ve exactamente
como con tu flujo anterior antes de seguir transcribiendo Aron, Berlin y Revel
directamente en esta nueva estructura.
