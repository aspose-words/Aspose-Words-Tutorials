---
category: general
date: 2026-06-24
description: Crear una forma rectangular en Python con Aspose.Words, aprender a añadir
  sombra a la forma, establecer el ángulo de la sombra y guardar el documento como
  PDF en minutos.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: es
og_description: Crea una forma rectangular en Python, agrega sombra a la forma, establece
  el ángulo de la sombra y guarda el documento como PDF con Aspose.Words. Sigue esta
  guía paso a paso.
og_title: Crear forma de rectángulo en Python – Tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Crear forma de rectángulo en Python – Guía completa de Aspose.Words
url: /es/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma de rectángulo en Python – Guía completa de Aspose.Words

¿Alguna vez te has preguntado cómo **create rectangle shape** en un documento Word usando Python? Tal vez necesites un recuadro llamativo, una pista visual para un diagrama, o simplemente un rectángulo elegante para un informe. Sea cual sea el caso, has llegado al lugar correcto. En este tutorial recorreremos todo el proceso—from inserting the rectangle, to adding a subtle shadow, tweaking the shadow angle, and finally **save document as PDF** so you can share it with anyone.

Usaremos **Aspose.Words for Python via .NET**, una biblioteca poderosa que te permite manipular archivos Word sin necesidad de abrir Word. Al final de esta guía podrás responder la pregunta *“how to add shape shadow”* con confianza, y tendrás un script listo‑para‑ejecutar que puedes incorporar en cualquier proyecto.

---

## Lo que necesitarás

- **Python 3.8+** instalado en tu máquina.  
- **Aspose.Words for Python via .NET** (`aspose-words` package). Instálalo con:

  ```bash
  pip install aspose-words
  ```

- Una carpeta con permisos de escritura donde se guardará el PDF generado.  
- (Opcional) Un IDE o editor de texto—VS Code funciona muy bien.

Eso es todo. No hay DLLs extra, ni instalación de Office, solo un único paquete pip.

## Paso 1: Configurar el documento y el builder

Lo primero que debes hacer es crear objetos compatibles con **create rectangle shape**: un `Document` y un `DocumentBuilder`. Piensa en el builder como tu lápiz; dibuja todo por ti.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Por qué es importante:** El objeto `Document` representa todo el archivo .docx, mientras que el `DocumentBuilder` proporciona métodos como `insert_shape` que facilitan el dibujo de formas.

## Paso 2: Insertar la forma de rectángulo

Ahora que tenemos un builder, finalmente podemos **create rectangle shape**. El método `insert_shape` necesita tres argumentos: el tipo de forma, el ancho y la altura. Usaremos un ancho de 200 pt y una altura de 100 pt para una buena proporción.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

En este punto has **create rectangle shape** con éxito en tu documento. Si abres el DOCX generado (lo haremos más adelante), verás un rectángulo simple ubicado donde estaba el cursor.

## Paso 3: Acceder al objeto de formato de sombra

Para **add shadow to shape**, primero necesitamos obtener el formato de sombra de la forma. Cada forma en Aspose.Words tiene una propiedad `shadow_format` que expone todas las configuraciones relacionadas con la sombra.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Tener la referencia `shadow` nos permite alternar la visibilidad, desenfoque, distancia, ángulo, color y transparencia—todo en unas pocas líneas de código.

## Paso 4: Habilitar la sombra y configurar su apariencia

Aquí es donde ocurre la magia. **add shadow to shape**, lo haremos ligeramente difuso, lo desplazaremos un poco, estableceremos la dirección (la parte de **set shadow angle**), y le daremos un tono negro semi‑transparente.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Consejo profesional:** Si alguna vez necesitas un efecto más dramático, aumenta `blur_radius` o disminuye `transparency`. Por el contrario, una sombra nítida y totalmente opaca se puede lograr con `blur_radius = 0` y `transparency = 0`.

## Paso 5: Guardar el documento como PDF

Hemos **create rectangle shape**, hemos **add shadow to shape**, y ahora **save document as PDF** para que el resultado se vea idéntico en cualquier dispositivo. Aspose.Words lo hace con una sola línea.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Ejecutar el script generará `shadowed_rectangle.pdf` en la carpeta `output`. Ábrelo con cualquier visor de PDF y verás un rectángulo limpio con una sombra suave de 45 grados—exactamente lo que configuramos.

## Ejemplo completo y funcional

A continuación tienes el script completo, listo‑para‑ejecutar, que combina todos los pasos anteriores. Copia‑y‑pega en un archivo llamado `create_rectangle_with_shadow.py` y ejecuta `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Salida esperada:** Un archivo PDF que muestra un solo rectángulo con una sombra suave y diagonal. Sin páginas extra, sin artefactos ocultos—solo la forma que creamos.

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito una forma diferente?

Aspose.Words admite muchos valores de `ShapeType` (elipse, estrella, recuadro, etc.). Simplemente reemplaza `aw.drawing.ShapeType.RECTANGLE` por el enum deseado, como `aw.drawing.ShapeType.ELLIPSE`.

### ¿Puedo agregar múltiples sombras?

La API expone solo un `ShadowFormat` por forma, pero puedes simular múltiples sombras duplicando la forma, desplazando cada copia y ajustando la transparencia.

### ¿Cómo cambio el color de la sombra para que coincida con mi marca?

Simplemente asigna `shadow.color` a cualquier `aw.drawing.Color`. Para un azul de marca, usa `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### ¿Qué pasa al guardar como DOCX en lugar de PDF?

Reemplaza `document.save(pdf_path)` por `document.save("output/shadowed_rectangle.docx")`. La representación de la sombra se conserva en ambos formatos.

### ¿Funciona la sombra en visores de PDF antiguos?

Aspose.Words renderiza la sombra como un efecto vectorial, que es ampliamente compatible. Sin embargo, visores muy antiguos podrían aplanar el efecto; probar en los dispositivos de tu audiencia objetivo siempre es una buena práctica.

## Consejos para pulir tu PDF

- **Agregar un borde:** `rectangle.line_format.width = 1.5` y establece un color para un contorno nítido.  
- **Centrar el rectángulo:** Usa `builder.move_to_document_start()` antes de insertar, luego `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combinar con texto:** Inserta un `TextFragment` después del rectángulo para etiquetarlo, por ejemplo, `"Important Section"`.

Estos pequeños ajustes pueden convertir un rectángulo simple en un recuadro pulido que luce profesional en informes, propuestas o libros electrónicos.

## Conclusión

Ahora tienes una receta sólida, de principio a fin, para **create rectangle shape** en Python, **add shadow to shape**, **set shadow angle**, y **save document as PDF** usando Aspose.Words. Los pasos son sencillos, el código está completamente autocontenido, y has visto por qué cada línea es importante—from initializing the document to polishing the final PDF.

A continuación, podrías explorar **how to add shape shadow** en dibujos más complejos, experimentar con rellenos degradados, o generar tablas dentro de tus formas. La biblioteca también soporta enlazar formas a marcadores, lo cual puede ser útil para PDFs interactivos.

¿Tienes una variante que probaste? Compártela en los comentarios, o dispara cualquier pregunta pendiente. ¡Feliz codificación y disfruta añadiendo esa profundidad extra a tus documentos! 

![Forma de rectángulo con sombra – ejemplo de create rectangle shape en Python](/images/rectangle-shadow.png)


## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Añadir forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial de sombra de forma Aspose.Words – Añadir una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crear forma de rectángulo en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}