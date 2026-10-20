---
category: general
date: 2026-08-07
description: Dibujar un rectángulo en PDF usando Aspose.Words para Python y aprender
  cómo agregar sombra a la forma, configurar la sombra de la forma y guardar el documento
  como PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: es
lastmod: 2026-08-07
og_description: Dibujar un rectángulo en PDF con Aspose.Words para Python. Este tutorial
  muestra cómo agregar sombra a una forma, configurar la sombra de la forma y guardar
  el documento como PDF para la generación profesional de documentos.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Dibujar rectángulo en PDF con Aspose.Words para Python – guía
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Dibujar rectángulo en PDF con Aspose.Words para Python
url: /es/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dibujar rectángulo en PDF con Aspose.Words for Python

Si necesitas **draw rectangle in PDF** mientras trabajas en Python, esta guía te brinda una solución completa y lista para ejecutar. Verás exactamente cómo **add shadow to shape**, configurar esa sombra y, finalmente, **save document as PDF** para distribución o archivado.

Crear un rectángulo sombreado es un requisito común para informes, facturas o anotaciones visuales. Al final de este tutorial tendrás un único script que genera un PDF que contiene un rectángulo con una sombra realista, y comprenderás cómo ajustar el tamaño, el color y el desplazamiento para adaptarlo a cualquier diseño.

## Requisitos previos

* Python 3.8+ instalado.
* El paquete Aspose.Words for Python via .NET (`aspose-words`) – instalar con:

```bash
pip install aspose-words
```

* Permiso de escritura en la carpeta donde deseas guardar el PDF.

No se requieren bibliotecas adicionales; Aspose.Words maneja la creación de formas, la configuración de sombras y la exportación a PDF internamente.

## Paso 1: Crear un nuevo documento en blanco (draw rectangle in PDF – initialize)

El primer paso es instanciar un objeto `Document`. Este objeto representa todo el archivo PDF y proporciona un contenedor para secciones, párrafos y formas.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Por qué es importante:** Aspose.Words trata la generación de PDF como una conversión desde un modelo de documento Word, por lo que comenzamos con un `Document` aunque la salida final sea un PDF.

## Paso 2: Insertar una forma de rectángulo en el cuerpo del documento

Un rectángulo es un `ShapeType` específico. Lo añadimos al cuerpo de la primera sección, lo que crea automáticamente una nueva página al guardarse como PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Explicación:** Las propiedades `width` y `height` controlan el tamaño visual de la forma en el PDF. Añadir texto facilita la verificación del rectángulo durante las pruebas.

## Paso 3: Añadir sombra a la forma – habilitar y personalizar

Ahora activamos el efecto de sombra y afinamos su apariencia. Aquí es donde entra en juego la palabra clave **add shadow to shape**.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**¿Por qué configurar la sombra de la forma?** Ajustar `blur`, `distance` y `angle` permite simular una iluminación realista, lo que mejora la legibilidad y la jerarquía visual en los PDFs generados.

## Paso 4: Guardar el documento como PDF – salida final

Con el rectángulo y su sombra definidos, el último paso es exportar el documento Word a PDF. Esto cumple con el requisito **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Al abrir `shadow_rectangle.pdf`, verás una sola página que contiene un rectángulo con borde gris titulado “Shadow demo” y una sombra diagonal nítida.

### Resultado esperado

* Un archivo PDF llamado `shadow_rectangle.pdf`.
* Una página con un rectángulo de 200 pt × 100 pt.
* Una sombra visible desplazada 5 pt a un ángulo de 45°, difuminada en 8 pt.

## Paso 5: Explorar variaciones y casos límite (opcional)

A continuación se presentan ajustes comunes que podrías necesitar en proyectos del mundo real:

| Variación | Fragmento de código | Cuándo usar |
|-----------|---------------------|-------------|
| **Tipo de forma diferente** (p.ej., elipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Para gráficos redondeados o insignias |
| **Color de sombra personalizado** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Cuando se requiere una sombra gris o específica de la marca |
| **Múltiples formas** | Repeat the shape‑creation block and adjust `left`/`top` properties | Para crear diagramas complejos |
| **Sin texto dentro de la forma** | Omit `rectangle.text = "..."` | Cuando la forma es puramente decorativa |
| **Salida con mayor DPI** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Para PDFs listos para impresión |

**Consejo profesional:** Siempre establece `shadow.visible = True` antes de ajustar otras propiedades; de lo contrario, los cambios se ignoran silenciosamente.

## Script completo – copiar, pegar y ejecutar

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Ejecuta el script desde tu terminal o IDE. Reemplaza `YOUR_DIRECTORY` con una ruta de carpeta real, como `"/tmp"` o `"C:\\Users\\Me\\Documents"`.

## Conclusión

Ahora sabes cómo **draw rectangle in PDF** usando Aspose.Words for Python, **add shadow to shape**, **configure shape shadow** y **save document as PDF**. El ejemplo completo muestra cada paso, desde la creación del documento hasta la exportación final, y las variaciones opcionales demuestran cómo adaptar el código a escenarios más complejos.

A continuación, podrías explorar:

* Agregar otros tipos de forma (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Aplicar rellenos degradados o bordes para mejorar el atractivo visual.
* Usar `PdfSaveOptions` para incrustar fuentes o controlar la compresión de imágenes.

Siéntete libre de experimentar con los parámetros para que coincidan con tu marca o directrices de diseño. ¡Feliz scripting de PDFs!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Optimizar marcadores PDF usando Aspose.Words para Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimizar carga de PDF en Python con Aspose Words omitiendo imágenes](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Manipulación de PDF con Aspose Words Python](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}