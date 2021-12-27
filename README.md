## Estructura de datos
Las obras están definidas en `_data/obras.csv` y categorizadas en `_data/taxonomias.csv`.
Cada obra está categorizada mediante una taxonomía principal, referenciada con el campo tid.

Cada obra debe tener una entrada en obras.csv y una plantilla (archivo .md).
La ruta del archivo .md para esa obra viene definida en el campo ruta del archivo csv para esa obra.

Esta es la plantilla de contenido de una obra (archivo .md):

```
---
id: 12345
layout: default
---
{% include obra.html %}

```
Donde id, debe coincidir con el id de la obra en el archivo de datos (obras.csv).

A cada obra le corresponde una taxonomía principal, que normalmente es el lugar que reproduce.
Esta taxonomía, que puede ser un pueblo o ciudad, se referencia entre paréntesis cuando la obra aparece en un listado.

Cada taxonomía tiene una plantilla (archivo .md) asociada para mostrar así todas las obras de esta categoría.
El contenido de la plantilla de taxonomía es de esta forma:

```
---
tid: 123
permalink: plumillas/region/xxxxx
layout: default
---
## Plumillas de Xxxxx
{% include taxonomy_content.html %}
```
Donde tid es el id de la taxonomía, permalink es la ruta que tendrá la página, que coincidirá con la ruta de la plantilla (cambiando taxonomias por plumillas) y Xxxxx es el nombre del lugar (taxonomía).

### Características de la imagen
Cada obra tiene dos imágenes, una imagen principal, de 760px máximo de ancho o de alto.
