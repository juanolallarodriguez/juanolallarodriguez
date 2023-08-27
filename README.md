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

El contenido de la página de obra está implementado en `_includes/obras.html`. Los campos se toman del registro de la obra en `_data/obras.csv`. La descripción es autogenerada ya que la inmensa mayoría de las obras son plumillas con la misma estructura. No obstante, hay un campo descripcion en el csv, que de tener algún contenido será este texto el que se muestre en lugar del autogenerado.

#### Características de la imagen
Cada obra tiene dos imágenes, una imagen principal, de 760px máximo de ancho o de alto. Y otra de miniatura para los listados. De momento estamos usando la misma imagen para los dos casos.

### Taxonomías

A cada obra le corresponde una taxonomía principal, que normalmente es el lugar que reproduce.
Esta taxonomía, que puede ser un pueblo o ciudad, se referencia entre paréntesis cuando la obra aparece en un listado.

Cada taxonomía tiene una plantilla (archivo .md) asociada para mostrar así todas las obras de esta categoría. Para saber dónde ubicar este archivo, nos fijamos en el campo ruta de esa taxonomía en `_data/taxonomias.csv`. En lugar de "plumillas", lo ubicaremos en el directorio "taxonomias", y el último fragmento de la ruta será el nombre del archivo al que añadiremos .md. Por ejemplo: para el tid 123 vemos que la ruta en el csv es plumillas/galicia/pontevedra/forcarei, por lo que el archivo quedará ubicado en taxonomias/galicia/pontevedra/forcarei.md En realidad, la ubicación del archivo no importa para su visualización en la web, ya que el sistema toma la ruta del permalink y los enlaces con los campos ruta del csv de taxonomías, pero lo guardamos así siguiendo el mismo orden que la ruta por coherencia y claridad.

El contenido de la plantilla de taxonomía es de esta forma:

```
---
tid: 123
permalink: plumillas/.../...
layout: default
---
## Plumillas de ...
{% include taxonomy_content.html %}
```

Donde tid es el id de la taxonomía, y permalink es la ruta que tendrá esta página, y que copiamos desde el campo ruta de esa taxonomía en `_data/taxonomias.csv`. En "Plumillas de ..." pondremos en nombre del lugar, por ejemplo "Plumillas de Aranda de Duero" o "Plumillas de la provincia de Burgos".
