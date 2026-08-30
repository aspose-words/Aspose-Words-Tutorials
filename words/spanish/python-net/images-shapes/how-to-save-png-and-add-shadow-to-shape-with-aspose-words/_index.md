---
category: general
date: 2026-08-17
description: Cómo guardar PNG usando Aspose.Words para Python. Aprende a agregar sombra
  a una forma, guardar el documento como PDF y exportar Word a PNG en una sola guía.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: es
lastmod: 2026-08-17
og_description: Cómo guardar PNG con Aspose.Words. Este tutorial muestra cómo agregar
  una sombra a una forma, guardar el documento como PDF y exportar Word a PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Cómo guardar PNG y agregar sombra a una forma con Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Cómo guardar PNG y agregar sombra a una forma con Aspose.Words
url: /es/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo guardar PNG y agregar sombra a una forma con Aspose.Words

Si necesitas **how to save PNG** desde un archivo Word, esta guía te brinda una solución completa y ejecutable. También verás cómo **add shadow to shape**, **save document as PDF**, y **export Word to PNG** sin salir del entorno de Aspose.Words.

El tutorial cubre todo lo necesario para convertir un documento Word en blanco en un PDF y una imagen PNG, mientras se aplica un efecto de sombra simple a una forma rectangular. No se requieren herramientas externas, y el código funciona con Aspose.Words for Python via .NET 7 o posterior.

## Lo que lograrás

* Crear un nuevo documento Word programáticamente.  
* Insertar una forma rectangular y configurar un efecto de sombra.  
* Guardar el mismo documento como archivo PDF.  
* Exportar el documento como una imagen PNG.  

Estos pasos responden a la consulta común **how to save PNG** mientras también manejan **add shadow to shape** y **save document as PDF** en un único flujo de trabajo.

## Requisitos previos

* Python 3.9 o superior.  
* Aspose.Words for Python via .NET instalado (`pip install aspose-words`).  
* Permiso de escritura en el directorio de salida que especifiques.  

Si no has instalado Aspose.Words aún, ejecuta:

```bash
pip install aspose-words
```

## Cómo guardar PNG con Aspose.Words

El primer paso importante es crear un documento y un `DocumentBuilder`. El builder te brinda una API fluida para insertar contenido como formas, tablas o texto.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` representa todo el archivo Word en memoria. `aw.DocumentBuilder` apunta a la ubicación actual de inserción, que inicialmente es el inicio de la primera (y única) sección.

## Agregar sombra a la forma antes de exportar

Una forma puede ser cualquier objeto de dibujo—rectángulo, elipse o polígono personalizado. Aquí creamos un rectángulo de 100 × 100 puntos y aplicamos una sombra suave.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

¿Por qué configurar la sombra antes de guardar? Aspose.Words renderiza la sombra durante las fases de exportación a PDF y PNG, por lo que el efecto visual se conserva en ambos formatos de salida.

### Consejo profesional
Si necesitas una sombra más nítida, reduce `blur`. Para un desplazamiento más pronunciado, aumenta `distance`. La clase `Shadow` también expone `angle` y `transparency` para un control fino.

## Guardar documento como PDF

Guardar un documento Word como PDF es una sola línea una vez que el contenido está listo. La constante `SaveFormat.PDF` indica a Aspose.Words que realice la conversión.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

El PDF resultante contiene el rectángulo con la sombra exacta que definiste. Aspose.Words maneja gráficos vectoriales, por lo que el tamaño del PDF permanece modesto.

## Exportar Word a PNG

Exportar a PNG crea una imagen raster de cada página. Por defecto Aspose.Words usa 96 DPI; puedes aumentar este valor para una salida de mayor resolución proporcionando un objeto `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Cuando **export Word to PNG**, cada página se guarda como un archivo PNG separado. Como nuestro documento de ejemplo tiene solo una página, solo aparece un único archivo PNG.

### Opcional: PNG de mayor resolución

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Un DPI más alto es útil cuando el PNG se usará en impresión o cuando necesites una miniatura nítida.

## Script completo – copia, pega y ejecuta

A continuación se muestra el script completo y autónomo que implementa cada paso descrito arriba. Guárdalo como `generate_assets.py` y ejecútalo desde la línea de comandos.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Salida esperada

Ejecutar el script crea tres archivos:

* `output/output.pdf` – un PDF con un rectángulo que proyecta una sombra negra.  
* `output/output.png` – una representación PNG de 96 DPI de la misma página.  
* `output/high_res_output.png` – un PNG de 300 DPI para mayor calidad.  

Abre cualquiera de los archivos en tu visor favorito para verificar que la sombra aparece exactamente como se definió.

## Preguntas comunes y casos límite

**¿Qué pasa si el directorio de salida no existe?**  
El script llama a `os.makedirs(output_dir, exist_ok=True)`, lo que crea la carpeta automáticamente. Esto evita un `FileNotFoundError` durante las operaciones de guardado.

**¿Puedo agregar múltiples formas con diferentes sombras?**  
Sí. Crea objetos `Shape` adicionales, configura cada propiedad `shadow` de forma independiente e insértalos con `builder.insert_node(shape)` antes de guardar.

**¿Se conservará la sombra al convertir a otros formatos raster (p. ej., JPEG)?**  
Aspose.Words renderiza la sombra para todos los formatos raster soportados por `SaveFormat`. Puedes reemplazar `aw.SaveFormat.PNG` por `aw.SaveFormat.JPEG` y la sombra seguirá apareciendo.

**¿En qué se diferencia esto de “convert word to pdf”?**  
`convert word to pdf` es esencialmente la misma operación que se realiza en el paso 4. La misma llamada `doc.save` con `SaveFormat.PDF` maneja la conversión internamente, preservando el diseño, fuentes y gráficos como sombras.

**¿Existe un límite en el tamaño de la forma?**  
Las formas se miden en puntos (1 pt ≈ 1/72 pulgada). Dimensiones muy grandes pueden aumentar el tamaño del archivo resultante, pero Aspose.Words no impone un límite estricto. Ajusta los argumentos `width` y `height` al crear `aw.Shape` para adaptarlos a tu diseño.

## Conclusión

Ahora sabes **how to save PNG** desde un documento Word mientras también aprendes a **add shadow to shape**, **save document as PDF**, y **export Word to PNG** usando Aspose.Words para Python. El script completo demuestra un patrón limpio y repetible que puedes adaptar para documentos más grandes, múltiples páginas o efectos gráficos más complejos.

Los siguientes pasos podrían incluir:

* Experimentar con otros valores de `ShapeType` (elipse, nube, etc.).  
* Usar `

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}