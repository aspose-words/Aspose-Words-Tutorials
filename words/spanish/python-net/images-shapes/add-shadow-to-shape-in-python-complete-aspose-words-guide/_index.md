---
category: general
date: 2026-08-11
description: Agregar sombra a una forma usando Aspose.Words para Python. Aprende cómo
  añadir sombra a la forma, aplicar desenfoque a la forma y personalizar el desplazamiento
  y el color.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: es
lastmod: 2026-08-11
og_description: Agrega sombra a una forma con Aspose.Words para Python. Esta guía
  te muestra cómo aplicar desenfoque a la forma, establecer desplazamientos y elegir
  colores de sombra en solo unas pocas líneas de código.
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Agregar sombra a una forma en Python – tutorial paso a paso de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Agregar sombra a una forma en Python – guía completa de Aspose.Words
url: /es/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Añadir sombra a una forma en Python – guía completa de Aspose.Words

Si necesitas **añadir sombra a una forma** en un documento Word, este tutorial te muestra exactamente cómo hacerlo con Aspose.Words para Python. Ya sea que estés construyendo un generador de informes o un servicio de plantillas de documentos, aprenderás a añadir sombra a la forma, aplicar desenfoque a la forma y afinar la apariencia de la sombra en solo unas pocas líneas de código.

La guía cubre todo lo que necesitas: importaciones requeridas, localización de la forma objetivo (incluidos nodos anidados), configuración de las propiedades de la sombra, manejo de casos límite comunes y guardado del documento modificado. Al final tendrás un fragmento reutilizable que podrás insertar en cualquier proyecto Python que trabaje con archivos .docx.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- **Python 3.8+** instalado.  
- **Aspose.Words for Python via .NET** (instálalo con `pip install aspose-words`).  
- Un documento Word (`input.docx`) que contenga al menos una forma (por ejemplo, un rectángulo, una imagen o SmartArt).  
- Familiaridad básica con Python y el modelo de objetos de Aspose.Words.

## Paso 1: Importar Aspose.Words y abrir el documento

El primer paso es importar el paquete `aspose.words` (comúnmente con alias `aw`) y cargar el documento fuente.

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*Por qué es importante*: Abrir el documento te da acceso al árbol de nodos donde viven las formas. La clase `aw.Document` es el punto de entrada para todas las manipulaciones posteriores.

## Paso 2: Localizar la primera forma (incluidos nodos anidados)

Las formas pueden ser hijos directos de un `Paragraph` o estar anidadas dentro de otros contenedores (como tablas). Usar `get_child` con la bandera `is_deep` establecida en `True` garantiza que recuperes la primera forma sin importar el nivel de anidación.

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*Por qué es importante*: La operación de **add shape shadow** requiere un objeto `Shape`. La búsqueda profunda evita que pases por alto formas ocultas dentro de tablas o contenedores de grupo.

## Paso 3: Habilitar la sombra y establecer propiedades básicas

Aspose.Words representa una sombra con varias propiedades. Primero, activa la sombra estableciendo `shadow_visible` a `True`.

```python
# Enable the shadow effect
shape.shadow_visible = True
```

Ahora puedes configurar el radio de desenfoque, los desplazamientos y el color.

## Paso 4: Aplicar desenfoque a la forma y definir valores de desplazamiento

El radio de desenfoque controla cuán suave aparece la sombra. Un valor de `5.0` produce un desenfoque perceptible pero no abrumador. Los desplazamientos mueven la sombra horizontal y verticalmente.

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*Por qué es importante*: Ajustar `shadow_blur` y los valores de desplazamiento te permite crear efectos de profundidad realistas que coincidan con el estilo visual de tu documento.

## Paso 5: Elegir el color de la sombra (add shape shadow con color personalizado)

Puedes usar cualquier `aw.Color`. Aquí seleccionamos negro, pero puedes reemplazarlo con `aw.Color.red`, `aw.Color.from_argb(255, 0, 120, 215)`, etc.

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*Por qué es importante*: El color determina cómo la sombra interactúa con el contenido circundante. Las sombras más oscuras son más visibles sobre fondos claros, mientras que tonos más claros funcionan mejor en páginas oscuras.

## Paso 6: Guardar el documento actualizado

Finalmente, escribe los cambios en disco. Puedes sobrescribir el archivo original o crear uno nuevo.

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

Al abrir `output_with_shadow.docx` en Microsoft Word, la primera forma mostrará una sombra negra suave con el desenfoque y desplazamiento especificados.

## Ejemplo completo y ejecutable

Juntando todo, aquí tienes un script autocontenido que puedes ejecutar de inmediato:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**Salida esperada**: Al abrir `output_with_shadow.docx` se muestra la primera forma con una sutil sombra negra que está desenfocada y desplazada 2 pt horizontal y verticalmente, según los parámetros que pasaste.

## Manejo de múltiples formas y casos límite

### Añadir sombra a una forma específica por nombre

Si tu documento contiene varias formas, puede que quieras dirigirte a una mediante su propiedad `name`:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### Omitir nodos no visuales

A veces un nodo de forma puede ser un marcador de posición (por ejemplo, un lienzo de dibujo sin contenido visual). Protege tu código verificando `shape.is_image` o `shape.is_picture_frame` antes de aplicar la sombra.

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### Trabajar con formas agrupadas

Cuando las formas están agrupadas, el propio grupo es un nodo `Shape`. Para aplicar una sombra a cada miembro, itera a través de `shape.get_child_nodes(aw.NodeType.SHAPE, True)`.

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

Estas variaciones garantizan que tu código funcione de manera robusta en diferentes diseños de documento.

## Consejos profesionales para sombras perfectas

- **Consistencia**: Usa el mismo radio de desenfoque y desplazamiento para todas las formas de un informe para mantener un lenguaje visual coherente.  
- **Rendimiento**: Aplicar sombras a decenas de imágenes de alta resolución puede aumentar el tamaño del archivo. Prueba el tamaño de salida si planeas generar PDFs más adelante.  
- **Contraste de color**: En fondos de página oscuros, considera una sombra más clara (`aw.Color.gray`) para mantener la visibilidad.  
- **Vista previa**: La interfaz de “Shadow” de Word refleja las propiedades de Aspose.Words, por lo que puedes experimentar manualmente y luego copiar los valores resultantes en tu script.

## Conclusión

Ahora sabes cómo **añadir sombra a una forma** en un documento Word usando Aspose.Words para Python. La guía cubrió la localización de una forma, la activación de la sombra, **add shape shadow** con desenfoque, desplazamientos y color personalizados, y el guardado del resultado. Con la función reutilizable anterior, puedes integrar este efecto en cualquier canal de generación de documentos.

### ¿Qué sigue?

- Explora **apply blur to shape** para otros efectos como resplandor o bordes suaves.  
- Combina sombras con **shape borders** o **reflection** para crear gráficos más ricos.  
- Convierte el documento editado a PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`) para su distribución.

¡Siéntete libre de experimentar con diferentes colores, niveles de desenfoque y valores de desplazamiento para que coincidan con las directrices de tu marca! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}