---
category: general
date: 2026-06-21
description: Crea una forma rectangular en Python usando Aspose.Words. Aprende cómo
  agregar sombra a la forma, establecer el color de relleno de la forma y guardar
  el documento como PDF en minutos.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: es
og_description: Crear una forma rectangular en Python con Aspose.Words. Esta guía
  muestra cómo agregar sombra a la forma, establecer el color de relleno de la forma
  y guardar el documento como PDF.
og_title: Crear forma de rectángulo en Python – tutorial de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Crear forma de rectángulo en Python – tutorial de Aspose.Words
url: /es/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Python – Tutorial de Aspose.Words

¿Alguna vez te has preguntado **cómo crear una forma rectangular** en un documento Word mientras programas en Python? No eres el único. Muchos desarrolladores se quedan atascados cuando necesitan un elemento visual rápido—como un cuadro coloreado con una sombra sutil—y luego exportar todo como PDF.  

En esta guía recorreremos un ejemplo completo y ejecutable que **crea una forma rectangular**, **establece el color de relleno de la forma**, **añade sombra a la forma**, y finalmente **guarda el documento como PDF**. Sin referencias vagas, solo código concreto que puedes copiar‑pegar y ejecutar hoy.

## Lo que necesitarás

Antes de comenzar, asegúrate de tener lo siguiente en tu máquina:

- Python 3.8 o superior (la sintaxis que usamos funciona en cualquier versión reciente).
- Una licencia activa de Aspose.Words for Python o una prueba gratuita (la biblioteca es puro‑Python, no requiere interop COM).
- Un editor de texto o IDE con el que te sientas cómodo—VS Code funciona muy bien, pero cualquiera sirve.

Eso es todo. Sin frameworks pesados, sin dependencias adicionales a nivel del SO. Vamos a empezar.

## Paso 1: Instalar Aspose.Words for Python

Lo primero. Si aún no lo has hecho, descarga el paquete desde PyPI:

```bash
pip install aspose-words
```

Por qué este paso es importante: Aspose.Words proporciona las clases `Document` y `DocumentBuilder` de las que dependeremos. Sin la biblioteca, ninguna de las llamadas posteriores—como `insert_shape`—existe, por lo que el script fallaría antes de dibujar una línea.

> **Consejo profesional:** Mantén tu entorno virtual ordenado. Ejecuta `python -m venv .venv && source .venv/bin/activate` antes de instalar, así la biblioteca queda aislada de los paquetes del sistema.

## Paso 2: Crear un nuevo documento y un DocumentBuilder

Ahora realmente **creamos la forma rectangular** – pero primero necesitamos un lienzo en blanco.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

El objeto `Document` representa todo el archivo, mientras que `DocumentBuilder` es un asistente práctico que sabe dónde está el cursor y puede insertar elementos en ese punto. Piensa en el builder como una pluma que escribe en la página.

## Paso 3: Insertar la forma rectangular

Aquí es donde ocurre la acción principal. **Crearemos una forma rectangular** con un ancho y alto fijos, y luego la posicionaremos en la página.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

¿Por qué un rectángulo? Es la forma más simple que aún nos permite mostrar colores de relleno y sombras. Si más adelante necesitas un círculo o una estrella, simplemente reemplaza `ShapeType.RECTANGLE` por otro valor del enum.

## Paso 4: Establecer el color de relleno de la forma

Una caja blanca simple no es muy emocionante, así que **establezcamos el color de relleno de la forma** a algo suave—el azul claro funciona bien para informes.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Puedes usar cualquiera de los miembros predefinidos de `aw.Color` (`red`, `green`, `dark_gray`, etc.) o pasar una tupla RGB (`aw.Color.from_argb(255, 30, 144, 255)`). El color de relleno es lo que el usuario ve antes de que se aplique cualquier sombra o borde.

## Paso 5: Añadir sombra a la forma

Ahora el toque visual: **añadir sombra a la forma**. Las sombras dan profundidad y hacen que el rectángulo destaque en la página.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**¿Cómo añadir sombra?** El código anterior lo hace exactamente, pero desglosaremos por qué cada propiedad es importante:

- `visible` – activa o desactiva el efecto.
- `color` – define el tono; un gris oscuro imita la iluminación natural.
- `blur` – valores más altos producen un borde más suave.
- `offset_x` / `offset_y` – desplazan la sombra respecto a la forma; ajusta estos valores para simular diferentes ángulos de luz.
- `transparency` – 0 es sólido, 1 es invisible; 0.2 brinda una impresión sutil.
- `type` – `OUTER` proyecta la sombra fuera de la forma, mientras que `INNER` la insetaría.

Si alguna vez necesitas una sombra dramática, aumenta `blur` a 10‑15 y eleva `offset_x`/`offset_y` a 6‑8.

## Paso 6: Guardar el documento como PDF

Todo ese trabajo no sirve de nada si no podemos **guardar el documento como PDF** y compartirlo. Aspose.Words lo hace con una sola línea:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

¿Por qué PDF? Los PDFs conservan el diseño en todas las plataformas, lo que los hace ideales para informes, facturas o cualquier material imprimible. El método `save` detecta automáticamente la extensión del archivo y elige el formato correcto—solo asegúrate de que la ruta termine con `.pdf`.

### Resultado esperado

Abre el `ShapeWithShadow.pdf` resultante y deberías ver un rectángulo azul claro centrado cerca de la parte superior de la primera página, con una sombra gris oscuro suave desplazada ligeramente a la derecha y hacia abajo. Los bordes de la forma son nítidos, la sombra es sutil, y el tamaño del archivo suele estar por debajo de 100 KB.

## Bonus: Ajustar sombras – Respuestas a “cómo añadir sombra”

Quizás te preguntes, *“¿Puedo cambiar la dirección de la sombra sin mover la forma?”* Absolutamente. La posición de la sombra es independiente de las coordenadas de la forma; solo ajusta `offset_x` y `offset_y`. Valores positivos mueven la sombra a la derecha/abajo, valores negativos la mueven a la izquierda/arriba. Para una fuente de luz en la esquina superior izquierda, usa `offset_x = -3` y `offset_y = -3`.

Otra pregunta frecuente: *“¿Qué pasa si necesito varias sombras en la misma forma?”* Aspose.Words solo admite una sombra por forma. Si necesitas efectos en capas, crea una forma duplicada, despliázala ligeramente y aplica una sombra diferente a cada una. Es un pequeño truco, pero funciona.

## Script completo – Listo para ejecutar

A continuación tienes el script completo y autocontenido. Cópialo en un archivo llamado `create_rectangle_with_shadow.py` y ejecútalo con `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Nota:** Reemplaza `YOUR_DIRECTORY` con una ruta absoluta o relativa que exista en tu máquina. Si la carpeta no existe, Python lanzará un `FileNotFoundError`.

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| La sombra no aparece | `shadow.visible` quedó con el valor predeterminado `False` | Asegúrate de que `shadow.visible = True` |
| La forma es invisible | El color de relleno se estableció a `aw.Color.transparent` o `None` | Usa un color sólido como `aw.Color.light_blue` |
| El PDF está vacío | Olvidaste llamar a `doc.save` o guardaste con la extensión incorrecta | Llama `doc.save("output.pdf")` y verifica la ruta |
| Error de tiempo de ejecución `ImportError` | Aspose.Words no está instalado o estás en el entorno Python equivocado | Ejecuta `pip install aspose-words` dentro del venv activo |

## Próximos pasos – Explora más formas y formato

Ahora que dominas **crear forma rectangular**, puedes:

- Reemplazar `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE` o `ShapeType.PENTAGON` para experimentar con otras geometrías.
- Añadir texto dentro de la forma usando `builder.move_to(rectangle.absolute_position)` y luego `builder.writeln("Hello World")`.
- Combinar varias formas en un grupo con `group = aw.drawing.GroupShape(doc)` para diagramas complejos.
- Exportar a otros formatos como DOCX (`doc.save("output.docx")`) o HTML (`doc.save("output.html")`) para ver cómo se traduce la sombra.

Todas estas extensiones se basan en los mismos conceptos centrales: **añadir sombra a la forma**, **establecer el color de relleno de la forma**, y **guardar el documento como PDF** (u otro formato).

---

### Vista previa de la imagen *(opcional)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*La captura muestra la salida final en PDF con un rectángulo azul claro y una sombra exterior sutil.*

---

## Conclusión

Hemos recorrido cada paso necesario para **crear forma rectangular** en Python, aplicar un relleno personalizado, **añadir sombra a la forma**, y finalmente **guardar el documento como PDF**. El código es totalmente ejecutable, las explicaciones cubren el *por qué* detrás de cada propiedad, y hemos abordado casos límite comunes y próximos pasos.

---

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}