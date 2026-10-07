---
category: general
date: 2026-10-07
description: Aprende cómo guardar un documento como PDF mientras añades una forma
  rectangular y una sombra personalizada usando Aspose.Words para Python. Código paso
  a paso incluido.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: es
lastmod: 2026-10-07
og_description: Guarda el documento como PDF con una forma rectangular personalizada
  usando Aspose.Words para Python. Sigue el ejemplo completo para dibujar, aplicar
  estilo y exportar Word a PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Guardar documento como PDF con una forma rectangular – guía completa de
  Python
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Cómo guardar un documento como PDF con una forma rectangular personalizada
  en Python
url: /es/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo guardar un documento como PDF con una forma de rectángulo personalizada en Python

Si necesitas **guardar un documento como PDF** mientras añades gráficos personalizados, esta guía te muestra cómo hacerlo. Recorreremos la creación de un archivo Word en blanco, **dibujar una forma de rectángulo**, establecer su tamaño, aplicar una sombra visible y, finalmente, **exportar Word a PDF** usando la biblioteca Aspose.Words para Python.

Terminarás con un PDF que contiene un rectángulo perfectamente posicionado, listo para informes, facturas o cualquier escenario de automatización de documentos. No se requieren herramientas externas, solo Python y el paquete Aspose.Words.

## Lo que necesitarás

| Requisito | Por qué es importante |
|-------------|----------------|
| Python 3.8+ | La API de Aspose.Words para Python está dirigida a intérpretes modernos. |
| paquete `aspose-words` (`pip install aspose-words`) | Proporciona el espacio de nombres `aw` usado en los ejemplos de código. |
| Familiaridad básica con Python y programación orientada a objetos | El tutorial manipula objetos como `Document` y `Shape`. |
| Permiso de escritura en una carpeta donde se guardará el PDF | El paso **save document as pdf** escribe un archivo en disco. |

> **Consejo profesional:** Usa un entorno virtual (`python -m venv venv`) para mantener las dependencias aisladas.

## Cómo guardar un documento como PDF con una forma de rectángulo

A continuación tienes un ejemplo completo y ejecutable. Cada paso se explica para que comprendas **por qué** realizamos la acción, no solo **qué** hace el código.

### Paso 1: Inicializar un nuevo documento en blanco

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Crear un objeto `Document` nuevo te brinda una colección de páginas limpia. También podrías cargar un *.docx* existente si quisieras **exportar Word a PDF** más adelante, pero comenzar en blanco mantiene el ejemplo enfocado.

### Paso 2: Añadir una forma de rectángulo al documento

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

El paso **add rectangle shape** utiliza `ShapeType.RECTANGLE`. Al agregar la forma a un párrafo, Aspose.Words sabe dónde renderizarla en el PDF final.

### Paso 3: Establecer las dimensiones del rectángulo

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Definir **rectangle dimensions** explícitas garantiza que la forma se vea consistente en todas las plataformas. También puedes usar los ayudantes `convert_to_inches` si prefieres unidades imperiales.

### Paso 4: (Opcional) Aplicar una sombra personalizada visible

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Una sombra hace que el rectángulo destaque en el PDF. La bandera `shadow.visible` es obligatoria; sin ella, las demás propiedades no tendrán efecto.

### Paso 5: Guardar el documento como PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Llamar a `document.save` con la extensión **.pdf** automáticamente **save document as pdf** usando el renderizador PDF incorporado de Aspose.Words. No se requieren pasos de conversión adicionales, por lo que este método es la forma recomendada de **exportar Word a PDF**.

> **Por qué funciona:** Aspose.Words escribe el diseño del documento, incluido el rectángulo y su sombra, directamente en el flujo PDF. El proceso es sin pérdidas y conserva la calidad vectorial.

## Código fuente completo (script único)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Ejecutar este script genera `shadow_rectangle.pdf` que se ve así:

![Diagram of the generated PDF showing the rectangle shape after save document as pdf](placeholder-image.png)

*El PDF contiene una sola página con un rectángulo con sombra negra centrado en el documento.*

## Preguntas frecuentes y casos especiales

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo colocar el rectángulo en una ubicación específica?** | Sí. Establece `rectangle.left` y `rectangle.top` (en puntos) antes de guardar. |
| **¿Qué pasa si necesito varias formas?** | Crea objetos `Shape` adicionales, configúralos y añádelos al mismo párrafo o a diferentes párrafos. |
| **¿Afecta la sombra al tamaño del PDF?** | Solo marginalmente; la sombra se almacena como metadatos vectoriales, no como una imagen rasterizada. |
| **¿Puedo usar esto para convertir archivos *.docx* existentes?** | Por supuesto. Reemplaza `aw.Document()` por `aw.Document("input.docx")` y el resto de los pasos permanece igual. |
| **¿Hay forma de cambiar el color de relleno del rectángulo?** | Asigna `rectangle.fill_color = aw.drawing.Color.light_blue` (o cualquier `Color` que prefieras). |

## Próximos pasos

Ahora que sabes cómo **save document as PDF** con un rectángulo personalizado, podrías explorar:

* **Exportar Word a PDF** con encabezados, pies de página y números de página.  
* **Añadir otros objetos de dibujo** (`Ellipse`, `Polygon`) usando la misma clase `Shape`.  
* **Procesar por lotes** una carpeta de archivos Word, aplicando la misma superposición de rectángulo a cada uno.  

Estas extensiones siguen el mismo patrón: crear una forma, configurar sus propiedades y **save document as pdf**.

---

**Resumen:** Este tutorial te mostró cómo **save document as PDF** mientras **add rectangle shape**, **set rectangle dimensions** y aplicas una sombra personalizada usando Aspose.Words para Python. El script completo está listo para copiar, ejecutar y adaptar a tus propias canalizaciones de automatización de documentos. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Add rectangle to PDF with Aspose.Words – Step‑by‑Step Guide](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Save Document as PDF with Aspose.Words – Complete C# Guide](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}