---
category: general
date: 2026-11-18
description: El ejemplo de sombra de forma de Aspose.Words muestra cómo agregar una
  sombra a una forma de Word usando Python. Sigue esta guía paso a paso para modificar
  y guardar el documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: es
lastmod: 2026-11-18
og_description: Ejemplo de sombra de forma de Aspose.Words demuestra cómo agregar
  una sombra a una forma de Word con Python. Conoce el código completo, por qué cada
  paso es importante y cómo adaptarlo.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Ejemplo de sombra de forma en Aspose.Words – Guía de Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Ejemplo de sombra de forma en Aspose.Words con Python
url: /es/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ejemplo de sombra de forma Aspose.Words en Python

El ejemplo de sombra de forma Aspose.Words muestra cómo añadir un efecto de sombra a una forma en un documento Word usando Python. En este tutorial obtendrá un script completo y ejecutable que carga un documento, configura la sombra y guarda el resultado.

Aplicar una sombra a una forma es una forma común de mejorar la jerarquía visual en informes, folletos o facturas. El código a continuación funciona con Aspose.Words para Python via .NET y no requiere bibliotecas de terceros adicionales.

## Lo que aprenderás

* Cómo cargar un archivo `.docx` con **Aspose.Words for Python**.  
* Cómo localizar la primera forma (incluyendo formas dentro de tablas o grupos).  
* Cómo configurar el desenfoque, el desplazamiento horizontal y el desplazamiento vertical de la sombra.  
* Cómo guardar el documento modificado preservando todo el contenido restante.  

**Requisitos previos**

* Python 3.8 o superior.  
* Aspose.Words for Python via .NET instalado (`pip install aspose-words`).  
* Un documento Word (`input.docx`) que contenga al menos una forma (por ejemplo, una imagen, AutoShape o cuadro de texto).  

Si necesita instalar la biblioteca, ejecute:

```bash
pip install aspose-words
```

## Ejemplo de sombra de forma Aspose.Words – visión general

El siguiente script es la solución completa. Sigue los cuatro pasos lógicos de un flujo de trabajo típico de **manipulación de documentos Aspose**: cargar, localizar, modificar y guardar.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Resultado esperado

Abra `output.docx` en Microsoft Word. La primera forma que añadió ahora debería mostrar una sombra suave desplazada 2 pt horizontal y verticalmente, con un radio de desenfoque de 5 pt. Todo el demás contenido permanece sin cambios.

## Paso 1: Cargar el documento Word

Cargar un documento es la primera operación en cualquier flujo de trabajo de **Aspose.Words for Python**. La clase `Document` analiza el archivo y construye un modelo de objetos en memoria. Como la biblioteca funciona sobre la plataforma .NET, puede manejar archivos grandes de manera eficiente.

*Por qué es importante:* Cargar el documento una sola vez y mantener una referencia (`doc`) evita I/O repetido, lo que mejora el rendimiento cuando necesita aplicar múltiples modificaciones.

## Paso 2: Acceder a la forma

Las formas pueden ser hijos directos del cuerpo del documento, o pueden estar anidadas dentro de tablas, grupos o lienzos de dibujo. Usar `get_child(NodeType.SHAPE, 0, True)` busca recursivamente y devuelve la primera forma que coincide.

*Por qué es importante:* El indicador `True` garantiza que no se pierdan formas ocultas dentro de otros nodos. Si lo omite, solo se considerarían las formas de nivel superior, y muchos documentos del mundo real devolverían `None`.

### Alternativa: Encontrar una forma por nombre

Si su documento contiene varias formas, podría preferir localizar una específica:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Este fragmento muestra una variación **python shape shadow** que filtra por la propiedad `name` de la forma.

## Paso 3: Configurar la sombra de la forma

La propiedad `shadow` de un objeto `Shape` le brinda control granular sobre el efecto visual. Los tres atributos más comúnmente ajustados son:

| Propiedad | Rango típico | Impacto visual |
|-----------|--------------|----------------|
| `blur`    | 0 – 15       | Valores más altos crean un borde más suave. |
| `offset_x`| –10 – 10     | Valores positivos desplazan la sombra a la derecha. |
| `offset_y`| –10 – 10     | Valores positivos desplazan la sombra hacia abajo. |

También puede modificar `color`, `transparency`, `visible` y `style`. El ejemplo establece un desenfoque moderado y un ligero desplazamiento para mantener la sombra sutil.

**Consejo profesional:** Cuando una forma ya tiene una sombra, las propiedades anteriores sobrescriben la configuración existente. Si necesita preservar el estilo original, lea los valores actuales antes de cambiarlos.

## Paso 4: Guardar el documento modificado

Llamar a `doc.save()` escribe la representación en memoria de vuelta a un archivo `.docx`. Aspose.Words actualiza automáticamente todas las relaciones internas, por lo que el archivo de salida sigue siendo totalmente compatible con Microsoft Word.

*Por qué es importante:* Guardar solo una vez al final del proceso reduce el riesgo de corrupción del archivo y mejora la velocidad general, especialmente al procesar muchos documentos en un trabajo por lotes.

## Variaciones comunes y casos límite

### Trabajar con múltiples formas

Si necesita aplicar la misma sombra a cada forma, itere sobre la colección de nodos:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Aplicar una sombra a un tipo de forma específico

Puede filtrar por `ShapeType` (por ejemplo, `aw.ShapeType.IMAGE`). Esto es útil cuando solo desea afectar a imágenes, no a AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Manejar documentos sin formas

El script ya lanza un `ValueError` claro si no se encuentra ninguna forma. En código de producción podría registrar el problema y continuar procesando otros archivos.

### Notas de compatibilidad

* El código funciona con **Aspose.Words for Python via .NET** versión 23.10 y posteriores.  
* El efecto de sombra es compatible con Word 2007+ (`.docx`). Los formatos antiguos (`.doc`) perderán el efecto después de la conversión.

## Conclusión

Este **aspose.words shape shadow example** le guía paso a paso para cargar un archivo Word, localizar una forma, configurar su sombra y guardar el resultado con **Aspose.Words for Python**. Ahora dispone de un patrón reutilizable para cualquier escenario de **manipulación de documentos Aspose** que implique mejoras visuales.

A continuación, podrías explorar:

* Añadir rellenos degradados o estilos de línea a las formas (`modify shape shadow` y otras propiedades visuales).  
* Combinar la configuración de sombra con el formato de texto para crear plantillas totalmente estilizadas.  
* Automatizar el proceso para un lote de documentos usando `os.listdir` y el patrón mostrado arriba.

¡Siéntase libre de experimentar con diferentes niveles de desenfoque, desplazamientos y colores para que coincidan con las directrices de su marca! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [How to set shadow on a shape in Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [How to save PNG and add shadow to shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}