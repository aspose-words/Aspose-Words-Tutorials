---
category: general
date: 2026-05-30
description: Cómo insertar un rectángulo y añadir sombra en Word usando Aspose – una
  guía paso a paso en Python para crear un documento Word con efecto de sombra en
  la forma.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: es
og_description: Cómo insertar un rectángulo y agregar sombra en Word usando Aspose
  – aprende a crear un documento Word con efecto de sombra en la forma usando Python.
og_title: Cómo insertar un rectángulo y agregar sombra en Word usando Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Cómo insertar un rectángulo y añadir sombra en Word usando Aspose
url: /es/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar un rectángulo y agregar sombra en Word usando Aspose

¿Alguna vez te has preguntado **cómo insertar un rectángulo** en un archivo Word sin abrir la interfaz de usuario? No estás solo. Muchos desarrolladores necesitan generar informes, facturas o certificados al instante, y dibujar un simple rectángulo con una sombra agradable puede hacer que el resultado se vea pulido. En este tutorial recorreremos los pasos exactos para crear un documento Word, colocar una forma de rectángulo y aplicar una sombra realista usando Aspose.Words para Python.

Cubrirémos todo, desde la configuración del paquete Aspose hasta el ajuste de la distancia, el desenfoque y la opacidad de la sombra. Al final tendrás un fragmento reutilizable que podrás insertar en cualquier canal de automatización. Sin trucos, solo código claro y algunos consejos prácticos.

## Requisitos previos

Antes de sumergirnos, asegúrate de tener:

- Python 3.8+ instalado (el código funciona en 3.9, 3.10 y versiones posteriores)
- Una licencia activa de Aspose.Words para Python o una clave de evaluación gratuita
- Paquete `aspose-words` instalado mediante `pip install aspose-words`
- Una carpeta con permisos de escritura donde se guardará el **create word document aspose** generado

¡Eso es todo—sin DLLs adicionales, sin interop COM, solo Python puro.

## Paso 1: Inicializar el Documento (Cómo crear documento Word con Aspose)

Lo primero: necesitas un objeto `Document` nuevo. Piensa en él como un lienzo en blanco. El siguiente código crea el documento y un `DocumentBuilder` que nos permitirá insertar formas.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Por qué es importante:* El `DocumentBuilder` te brinda una API de alto nivel para agregar párrafos, tablas y—sí—formas sin tener que manejar árboles de nodos de bajo nivel. Si omites el builder y manipulas los nodos directamente, terminarás con código verboso y más difícil de mantener.

## Paso 2: Insertar el Rectángulo (cómo insertar rectángulo)

Ahora realmente **cómo insertar rectángulo**. Aspose.Words trata un rectángulo como un tipo de forma genérica. Especificas el ancho y la altura en puntos (1 punto ≈ 1/72 pulgada). Siéntete libre de ajustar los números según tu diseño.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Consejo:** Si necesitas que el rectángulo se posicione en una ubicación específica de la página, establece `shape.left` y `shape.top` después de la inserción. Esto te da un control pixel‑perfecto.

## Paso 3: Acceder al Formato de Sombra de la Forma (agregar sombra a forma)

El estilo visual de una forma reside en su `ShadowFormat`. Al obtenerlo, accedemos a cada propiedad que define el aspecto de la sombra.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

En este punto la sombra es invisible—piénsalo como una capa oculta esperando tus instrucciones.

## Paso 4: Configurar la Sombra (cómo agregar sombra a forma, aplicar efecto de sombra en Word)

Aquí es donde ocurre la magia. Activaremos la sombra y ajustaremos su apariencia. Los valores a continuación producen una sombra suave y diagonal que funciona bien para la mayoría de los documentos, pero puedes experimentar.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Qué hace cada propiedad

| Property | Effect | Typical Range |
|----------|--------|---------------|
| `visible` | Activa o desactiva la sombra | `True` / `False` |
| `distance` | Qué tan lejos está la sombra de la forma | 2 – 10 pts |
| `blur` | Suavidad de los bordes de la sombra | 4 – 12 pts |
| `color` | Tono de la sombra; gris oscuro es un valor seguro | Any `aw.Color` |
| `opacity` | Transparencia; 0 = invisible, 1 = sólida | 0.3 – 0.8 for subtle look |
| `angle` | Dirección de la luz | 0 – 360° |

**¿Por qué ajustar esto?** Una sombra bien afinada puede hacer que un rectángulo plano parezca elevado del papel, añadiendo profundidad sin imágenes. Si estableces `opacity` demasiado alta, la sombra se ve dura; demasiado baja y desaparece.

## Paso 5: Guardar el Documento (crear documento Word con Aspose)

Finalmente, escribe el archivo en disco. Puedes usar cualquier extensión compatible con Aspose.Words (`.docx`, `.pdf`, `.html`). Para este tutorial nos quedaremos con `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Abre el archivo resultante en Microsoft Word y verás un rectángulo nítido con una sombra sutil—exactamente lo que esperarías de una plantilla diseñada profesionalmente.

![cómo insertar forma de rectángulo con sombra usando Aspose.Words](/images/rectangle-shadow.png){alt="cómo insertar forma de rectángulo con sombra usando Aspose.Words"}

*La captura de pantalla (arriba) muestra el rectángulo con la sombra aplicada. Observa el suave desenfoque y el ángulo de 45°, que le da un aspecto natural.*

## Variaciones comunes y casos límite

### Agregar múltiples formas

Si necesitas más de un rectángulo, simplemente repite la llamada `insert_shape`. Recuerda mover el cursor del builder (`builder.move_to(shape)`) o ajustar `shape.left`/`shape.top` para evitar superposiciones.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Cambiar el tipo de forma

Aunque esta guía se centra en rectángulos, el mismo patrón funciona para óvalos, estrellas o formas libres personalizadas. Reemplaza `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.CLOUD`, etc., y la configuración de sombra permanece idéntica.

### Guardar en otros formatos

Aspose.Words puede exportar a PDF, PNG o incluso XPS con una sola línea:

```python
doc.save("output/ShapeWithShadow.pdf")
```

El renderizado de la sombra se conserva entre formatos, por lo que tu PDF se verá igual que el archivo Word.

### Manejo de documentos grandes

Al generar informes masivos, considera llamar a `doc.update_page_layout()` después de insertar todas las formas. Esto fuerza una pasada de diseño y puede mejorar el rendimiento cuando luego conviertas a PDF.

## Ejemplo completo (Todos los pasos combinados)

A continuación tienes el script completo que puedes copiar‑pegar en un archivo llamado `rectangle_shadow.py`. Ejecútalo con `python rectangle_shadow.py` y revisa la carpeta `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Ejecutar este script produce exactamente el mismo documento del que hablamos antes. Siéntete libre de ajustar los números; el código es deliberadamente simple para que puedas experimentar sin miedo.

## Preguntas frecuentes

**P: ¿Esto funciona en Linux?**


## ¿Qué deberías aprender a continuación?

- [Crear documento Word Java – Agregar forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear documento Word en blanco con forma de rectángulo sombreada – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial de sombra de forma Aspose.Words – Agregar una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}