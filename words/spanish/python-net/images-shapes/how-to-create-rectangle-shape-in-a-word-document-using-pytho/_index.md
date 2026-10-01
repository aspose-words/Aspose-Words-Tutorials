---
category: general
date: 2026-09-30
description: Aprenda a crear una forma rectangular, aplicar sombra a la forma y guardar
  Word con la forma usando Aspose.Words para Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: es
lastmod: 2026-09-30
og_description: Crea una forma rectangular en un documento de Word rápidamente. Este
  tutorial muestra cómo agregar la forma, aplicar sombra a la forma, establecer el
  desenfoque de la sombra y guardar el documento de Word con la forma.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Crear forma rectangular en Word con Python – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Cómo crear una forma rectangular en un documento de Word usando Python
url: /es/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear una forma rectangular en un documento Word usando Python

Si necesitas **crear una forma rectangular** en un archivo Word, esta guía te muestra una solución completa y ejecutable. Verás cómo agregar la forma, aplicar un efecto de sombra, ajustar el desenfoque y, finalmente, **guardar Word con la forma** para que el resultado pueda abrirse en Microsoft Word o cualquier visor compatible.

El ejemplo utiliza **Aspose.Words for Python via .NET**, una biblioteca que permite manipular documentos Word sin necesidad de tener Microsoft Office instalado. No se requiere experiencia previa con la API, solo conocimientos básicos de Python.

## Lo que lograrás

- Insertar un rectángulo en la primera sección de un documento nuevo.  
- Configurar una sombra suave estableciendo su desenfoque, desplazamiento y color.  
- Persistir el documento en disco y verificar el resultado visual.

## Requisitos previos

- Python 3.8 o superior.  
- Paquete `aspose-words` instalado (`pip install aspose-words`).  
- Permiso de escritura en el directorio de salida.

## Crear forma rectangular y configurar su apariencia

El primer paso es instanciar un documento vacío y agregarle una forma rectangular. La forma servirá como lienzo para el efecto de sombra.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Por qué esto es importante:**  
Crear el rectángulo te brinda un objeto concreto (`shape`) que luego puedes estilizar. Establecer dimensiones explícitas garantiza que la forma se vea igual en todas las plataformas.

## Cómo agregar una forma a un documento Word

Aunque el código anterior ya agrega el rectángulo, es posible que necesites agregar formas adicionales (p. ej., círculos, flechas) más adelante. El mismo patrón se aplica: llama a `append_child` en el cuerpo del documento y pasa el `ShapeType` deseado.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Consejo:** Usa la enumeración `ShapeType` para explorar todas las formas admitidas. Esto mantiene tu código legible y evita números mágicos.

## Aplicar sombra a la forma y establecer el desenfoque de la sombra

Una sombra añade profundidad e interés visual. La clase `ShadowEffect` permite controlar el desenfoque, el desplazamiento y el color. A continuación aplicamos una sombra negra suave al rectángulo.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**¿Por qué establecer el desenfoque?**  
`blur` determina cuán difusa aparece la sombra. Un valor bajo (p. ej., 1.0) produce un borde nítido, mientras que un valor más alto (p. ej., 5.0) crea un desvanecimiento suave, lo que suele ser más estéticamente agradable.

**Caso límite:** Si estableces `blur` en 0, la sombra se convierte en una silueta sólida. Algunos visores pueden renderizarla con artefactos de aliasing, por lo que es recomendable elegir un valor mayor que 0 para obtener una salida más suave.

## Guardar Word con la forma

Persistir el documento finaliza todos los cambios. El método `save` escribe un archivo `.docx` que cualquier procesador de Word moderno puede abrir.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Al abrir `output.docx`, verás un rectángulo posicionado a una pulgada de la esquina superior izquierda, con una sombra negra suave desplazada dos puntos a la derecha y hacia abajo. El desenfoque de la sombra hace que parezca que la forma está levantada de la página.

**Consejo profesional:** Si necesitas generar muchos documentos en un bucle, reutiliza la misma instancia de `Document` y limpia su cuerpo entre iteraciones para reducir el consumo de memoria.

## Variaciones comunes y solución de problemas

| Situación | Qué cambiar | Razón |
|-----------|-------------|-------|
| Color de sombra diferente | `shadow.color = aw.Color.red` | Usa colores de la marca o resalta formas importantes. |
| Desplazamiento de sombra mayor | Incrementa `shadow.offset_x`/`offset_y` | Enfatiza la profundidad para maquetas de UI. |
| Sin sombra | Omite la línea `shape.shadow = shadow` | Útil para informes minimalistas. |
| Exportar a PDF en lugar de DOCX | `doc.save("output.pdf")` | PDF es ideal para distribución de solo lectura. |

Si la forma no aparece, verifica que la estés agregando a la sección correcta (`get_first_section()`) y que el documento se guarde después de las modificaciones.

## Ejemplo completo y ejecutable

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Ejecutar el script genera `output.docx` que contiene el rectángulo con una sombra suave. Abre el archivo en Microsoft Word para confirmar que el efecto visual coincide con la descripción.

## Conclusión

Ahora sabes cómo **crear una forma rectangular**, **agregar una forma** a un documento Word, **aplicar sombra a la forma**, **establecer el desenfoque de la sombra**, y finalmente **guardar Word con la forma** usando Aspose.Words for Python. El mismo patrón puede extenderse a otros tipos de forma, colores y efectos, dándote control total sobre los gráficos del documento sin depender de la automatización de Office.

**Próximos pasos**

- Experimenta con `Shape.fill` para agregar fondos de degradado o imágenes.  
- Usa objetos `Paragraph` para colocar texto dentro del rectángulo.  
- Combina múltiples formas para crear diagramas complejos y luego exporta a PDF para distribución.  

¡Siéntete libre de adaptar el código a tus propias necesidades de informes o plantillas, y comparte tus resultados en los comentarios!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Agregar forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear forma rectangular, agregar sombra y guardar PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Tutorial de sombra de forma Aspose.Words – Agregar una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}