---
category: general
date: 2026-10-16
description: Crear un documento de Word en blanco, insertar una forma en Word, añadir
  sombra externa y guardar como PDF usando Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: es
lastmod: 2026-10-16
og_description: Crea un documento de Word en blanco con una forma de sombra exterior
  usando Aspose.Words para Python. Esta guía muestra cómo insertar la forma, aplicar
  la sombra y guardar el archivo como PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Crear documento Word en blanco con sombra de forma – Guía de Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Crear documento Word en blanco con forma sombreada en Python
url: /es/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco con forma sombreada en Python

Si necesitas **crear un documento Word en blanco** y añadir un gráfico personalizado, esta guía te cubre. Te guiaremos paso a paso sobre cómo **insertar una forma en Word**, aplicar una **forma con sombra externa**, y finalmente **guardar como PDF usando Python**.

Aprenderás cómo configurar Aspose.Words para Python, crear un rectángulo, estilizar su sombra y generar un PDF que preserve el efecto visual. No se requiere experiencia previa con la API de Aspose, pero deberías tener conocimientos básicos de Python y una instalación funcional de Python 3.10 o posterior.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Python 3.10 o superior instalado.
* Una licencia activa de Aspose.Words para Python (una prueba gratuita funciona para evaluación).
* Acceso a `pip` para instalar el paquete `aspose-words`.
* Permiso de escritura en el directorio donde se guardará el PDF.

Puedes instalar la biblioteca con un solo comando:

```bash
pip install aspose-words
```

## Crear documento Word en blanco – configuración del entorno

El primer paso es crear un archivo Word vacío que servirá como lienzo para la forma.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` representa un archivo Word completamente en blanco. Al usar `DocumentBuilder` obtienes acceso a métodos como `insert_shape`, que utilizaremos en el siguiente paso.

## Insertar forma en Word y establecer dimensiones

Ahora añadimos un rectángulo que más adelante recibirá una sombra externa. El tamaño se expresa en puntos (1 pt ≈ 1/72 pulgada).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

La llamada `insert_shape` devuelve un objeto `Shape` que puedes personalizar aún más. En este punto el documento ya contiene un rectángulo visible al abrirlo en Microsoft Word.

## Añadir sombra externa a la forma – personalizando el efecto

Aspose.Words proporciona una clase `ShadowEffect` para definir propiedades de la sombra como estilo, desenfoque, distancia y color.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Establecer `style` a `OUTER` garantiza que la sombra aparezca fuera del borde del rectángulo, proporcionando un sutil aspecto 3‑D. Puedes experimentar con `blur` y `distance` para lograr una sombra más ajustada o más difusa.

## Guardar como PDF con Python – finalizando el documento

Después de estilizar la forma, el documento puede guardarse directamente como PDF. Aspose.Words maneja la conversión internamente, preservando el efecto de sombra.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Cuando abras `shape_with_shadow.pdf` en cualquier visor de PDF, verás el rectángulo con la sombra externa exactamente como apareció en Word.

## Ejemplo completo en funcionamiento

A continuación se muestra el script completo que combina todos los pasos. Cópialo en un archivo llamado `create_word_with_shadow.py` y ejecútalo.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Salida esperada**

Ejecutar el script imprime una línea de confirmación, por ejemplo:

```
PDF generated at: output/shape_with_shadow.pdf
```

Abrir el PDF resultante muestra una sola página que contiene un rectángulo de 200 pt × 100 pt con una suave sombra externa negra.

## Variaciones comunes y casos límite

* **Cambiar el color de la sombra** – Reemplaza `aw.Color.black` por cualquier otro valor de `aw.Color`, como `aw.Color.red` o `aw.Color.from_argb(255, 0, 120, 215)`.
* **Usar una forma diferente** – Cambia `aw.drawing.ShapeType.RECTANGLE` a `OVAL`, `DIAMOND` o cualquier otro valor de enumeración soportado.
* **Guardar como DOCX en lugar de PDF** – Llama a `doc.save("output/shape.docx")` para mantener el formato Word.
* **Múltiples formas** – Crea formas adicionales llamando de nuevo a `builder.insert_shape`; cada forma puede tener su propio `ShadowEffect`.

**Consejo profesional:** Si necesitas colocar la forma en una ubicación específica, establece `rectangle.left` y `rectangle.top` después de la inserción. Esto te brinda un control pixel‑perfecto sobre la posición.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **insertar una forma en Word**, **añadir una sombra externa a la forma**, y **guardar como PDF usando Python**. El ejemplo de código completo demuestra el flujo de trabajo de extremo a extremo, y las explicaciones aclaran por qué cada llamada a la API es necesaria.

Desde aquí puedes explorar opciones de estilo más avanzadas, añadir texto dentro de la forma, o combinar múltiples formas para crear diagramas complejos. Experimenta con diferentes parámetros de sombra para que coincidan con el lenguaje visual de tu marca, e integra este enfoque en pipelines de generación de documentos más amplios.

¡Feliz programación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma rectangular, añadir sombra y guardar PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Crear PDF desde Word – Guía completa de Python con Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Añadir sombra a una forma en Word con Aspose.Words – Paso a paso](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}