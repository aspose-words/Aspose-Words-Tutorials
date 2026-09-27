---
category: general
date: 2026-09-27
description: Aprenda cómo aplicar sombra a una forma con Aspose.Words para Python.
  Esta guía cubre agregar sombra a una forma, aplicar el efecto de sombra y establecer
  el color de la sombra.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: es
lastmod: 2026-09-27
og_description: Cómo aplicar sombra a una forma usando Aspose.Words para Python. Sigue
  la guía paso a paso para agregar sombra a la forma, aplicar el efecto de sombra
  y establecer el color de la sombra.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Cómo establecer sombra en una forma en Aspose.Words para Python
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Cómo establecer sombra en una forma en Aspose.Words para Python
url: /es/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo aplicar sombra a una forma en Aspose.Words para Python

Si necesita **cómo establecer sombra** para un objeto de dibujo, esta guía muestra el proceso completo. Verá cómo agregar sombra a una forma, configurar el desenfoque, desplazamiento y color de la sombra, y guardar el documento actualizado sin salir del código.

El tutorial asume que ya tiene un entorno básico de Aspose.Words para Python. Al final del artículo podrá aplicar un efecto de sombra de aspecto profesional a cualquier forma en un archivo DOCX.

## Requisitos previos

Antes de comenzar, asegúrese de tener:

* Python 3.8+ instalado.
* Aspose.Words for Python via .NET (`pip install aspose-words`) instalado.
* Un documento Word (`input.docx`) que contenga al menos una forma (p. ej., un rectángulo o una imagen).  
  Si el documento está vacío, el código creará una nueva forma para la demostración.

Estos elementos garantizan que los pasos posteriores se ejecuten sin errores de importación.

## Paso 1: Cargar o crear el documento Word

La primera operación es obtener un objeto `Document`. Puede cargar un archivo existente o crear uno nuevo.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Por qué este paso es importante*: El objeto `Document` es el punto de entrada para todas las operaciones de procesamiento de Word. Sin él no puede acceder a las formas ni aplicar efectos visuales.

## Paso 2: Recuperar la forma objetivo

Para manipular la apariencia de una forma necesita una referencia al nodo de forma. El ejemplo a continuación obtiene la primera forma encontrada en la jerarquía del documento.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Por qué este paso es importante*: `add shadow to shape` requiere un objeto de forma concreto. El código maneja de forma segura el caso límite en que el documento no contiene formas, asegurando que el tutorial funcione para todos los lectores.

## Paso 3: Configurar la apariencia de la sombra

Ahora puede **aplicar efecto de sombra** ajustando la propiedad `shadow` de la forma. Los siguientes ajustes proporcionan una sombra sutil y oscura.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Por qué cada propiedad es importante*:

| Propiedad | Efecto |
|----------|--------|
| `blur`   | Controla cuán difusa se ve la sombra. |
| `offset_x` / `offset_y` | Determina la dirección y distancia respecto a la forma. |
| `color`  | Define el tono de la sombra; puede usar cualquier `aw.Color`. |
| `visible`| Asegura que la sombra se renderice en el archivo de salida. |

Puede reemplazar `aw.Color.black` por `aw.Color.from_argb(255, 0, 0, 0)` para un valor RGBA personalizado, o cualquier otro color predefinido.

## Paso 4: Guardar el documento modificado

Después de configurar la sombra, persista los cambios en un nuevo archivo.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

Cuando abra `output.docx` en Microsoft Word, la forma seleccionada mostrará una sombra negra suave desplazada 2 pt a la derecha y 2 pt hacia abajo.

## Ejemplo completo funcional

Unir todos los pasos brinda un script autónomo que puede copiar y pegar en su IDE.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

Ejecutar el script produce `output.docx` donde la primera forma lleva la sombra configurada.

## Problemas comunes y cómo evitarlos

| Problema | Razón | Solución |
|----------|-------|----------|
| `shape` es `None` incluso después de cargar un documento | El documento no contiene objetos de dibujo. | Use el bloque de creación de forma de respaldo mostrado en el Paso 2. |
| La sombra no aparece en Word | `shape.shadow.visible` quedó como `False` o el documento se guardó en un formato antiguo (p. ej., `.doc`). | Asegúrese de que `visible = True` y guarde como `.docx`. |
| El color se ve diferente de lo esperado | El tema del documento sobrescribe los colores explícitos. | Establezca `shape.shadow.color` después de desactivar las sobrescrituras del tema, o use `aw.Color.from_argb`. |

Abordar estos casos límite hace que la solución sea robusta para código de producción.

## Extender el efecto (próximos pasos)

Ahora que sabe **cómo agregar sombra**, puede explorar mejoras relacionadas:

* **apply shadow effect** con degradado o múltiples sombras ajustando las sub‑propiedades de `shape.shadow`.
* Use **set shadow color** de forma dinámica basándose en la entrada del usuario o colores del tema.
* Combine **add shadow to shape** con otras acciones de formato como rotación, estilo de línea o efectos 3‑D.
* Automatice la adición de sombras para cada forma en un documento iterando a través de `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

Estas extensiones le permiten crear pipelines de generación de documentos sofisticados que producen resultados pulidos y visualmente consistentes.

## Conclusión

Ahora tiene una solución completa y ejecutable para **cómo establecer sombra** en una forma usando Aspose.Words para Python. La guía cubrió cargar un documento, recuperar o crear una forma, configurar desenfoque, desplazamiento y **set shadow color**, y finalmente guardar el archivo. Aplique el patrón a cualquier forma en sus proyectos de automatización y experimente con ajustes visuales adicionales para cumplir con sus requisitos de diseño.

--- 

*Siéntase libre de adaptar el código para otros tipos de forma, colores o valores de desplazamiento. Si encuentra algún problema, revisar la tabla de “Problemas comunes” es un buen primer paso.*

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Add shadow to shape in C# – Complete Guide to Apply Shadow Effect](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}