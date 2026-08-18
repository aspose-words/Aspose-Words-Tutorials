---
category: general
date: 2026-06-30
description: Añade sombra a una forma usando Aspose.Words para Python. Aprende cómo
  establecer la distancia de la sombra, personalizar el desenfoque y guardar rápidamente
  un PDF con sombra en la forma.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: es
og_description: Agregar sombra a una forma en un documento de Word con Aspose.Words
  para Python. Este tutorial muestra cómo establecer la distancia, el desenfoque y
  el color de la sombra, y luego guardarlo como PDF.
og_title: Agregar sombra a una forma en Python – Guía completa de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Agregar sombra a una forma en Python con Aspose.Words – Guía completa
url: /es/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Añadir sombra a una forma en Python con Aspose.Words – Guía completa

Agregar sombra a una forma en un documento Word usando Aspose.Words para Python es más fácil de lo que piensas. Si alguna vez te has preguntado **cómo establecer la distancia de la sombra** o **cómo añadir sombra a una forma** para un aspecto pulido, esta guía te cubre.

En los próximos minutos recorreremos todo lo que necesitas: desde crear un documento nuevo, insertar un rectángulo, ajustar sus propiedades de sombra, hasta finalmente guardar un PDF que muestre el efecto. Al final podrás aplicar una sombra a cualquier forma—rectángulo, elipse o dibujo personalizado—sin tener que bucear en la documentación de la API.

> **Prerequisitos** – Debes tener Python 3.7+ instalado, una licencia de Aspose.Words para Python (o una evaluación gratuita), y una familiaridad básica con la escritura de scripts en Python. No se requieren otras bibliotecas externas.

---

## Añadir sombra a una forma – Visión general paso a paso

A continuación tienes una hoja de ruta rápida de lo que lograremos:

1. **Crear un documento nuevo** y un `DocumentBuilder` para editarlo.  
2. **Insertar una forma rectangular** del tamaño que necesites.  
3. **Habilitar y personalizar la sombra** – aquí es donde brilla la palabra clave principal.  
4. **Guardar el documento** como PDF que conserve la sombra de la forma.

Cada paso está dividido en su propia sección, para que puedas copiar‑pegar los fragmentos de código directamente en tu IDE.

---

## Paso 1: Inicializar el Documento y el Builder

Primero lo primero—sin un `Document` no tienes nada sobre lo que trabajar. El `DocumentBuilder` es tu pincel.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Por qué es importante*: El objeto `Document` representa todo el archivo, mientras que el `DocumentBuilder` simplifica la inserción de texto, tablas y formas. Piensa en el builder como un cursor que puedes mover por la página.

---

## Paso 2: Insertar una Forma Rectangular

Ahora añadiremos un rectángulo—nuestro lienzo para el efecto de sombra. Puedes reemplazar `RECTANGLE` por `ELLIPSE`, `STAR` o cualquier otro `ShapeType` si necesitas una geometría diferente.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Consejo profesional*: Las dimensiones están en puntos (1 pt ≈ 1/72 pulgada). Ajústalas para que encajen en tu diseño; la sombra se escalará automáticamente.

---

## Cómo establecer la distancia de la sombra

La **distancia** de la sombra determina qué tan lejos aparece de la forma. Una distancia mayor imita una fuente de luz más alejada, mientras que un valor menor brinda un leve levantamiento.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Nota**: La distancia funciona junto con `angle`. Cambiar el ángulo rota la sombra alrededor de la forma, mientras que `distance` la empuja hacia afuera.

---

## Cómo añadir sombra a una forma – Personalizando desenfoque, color y ángulo

Añadir una sombra no es solo activarla; a menudo quieres ajustar el desenfoque, el color y la dirección para un efecto realista.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*¿Por qué estas configuraciones?*  
- **Radio de desenfoque** suaviza el borde, evitando una silueta dura.  
- **Ángulo** simula la fuente de luz; 45° es un valor predeterminado común que se ve equilibrado.  
- **Color** puede ser cualquier objeto `Color`; prueba `Color.gray` para un efecto más suave.

---

## Paso 4: Guardar el documento como PDF

Una vez que la forma y su sombra están listas, persistir el resultado es pan comido. Aspose.Words maneja la conversión a PDF automáticamente, preservando la fidelidad visual.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Salida esperada*: Abre el `ShadowShape.pdf` generado. Verás una sola página con un rectángulo de 200 × 100 pt, cuya sombra se proyecta a 4 pt de distancia con un ángulo de 45°, desenfocada 5 pt. La sombra debería aparecer como un sutil halo gris‑negro abrazando la forma.

---

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito una forma diferente?

Reemplaza `aw.drawing.ShapeType.RECTANGLE` por cualquier otro valor del enum, por ejemplo `aw.drawing.ShapeType.ELLIPSE`. Las mismas propiedades de sombra se aplican—no se necesita código adicional.

### ¿Puedo aplicar una sombra a varias formas a la vez?

Sí. Recorre las formas que crees y configura cada `shadow_format` individualmente. Aquí tienes un fragmento rápido:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### ¿Cómo cambio la opacidad de la sombra?

Utiliza la propiedad `shadow.transparency` (0 = opaco, 1 = totalmente transparente):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Ejemplo completo en funcionamiento

A continuación tienes el script completo—cópialo, ajusta la carpeta de salida y ejecútalo. No falta ninguna pieza.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Ejecuta el script y luego abre el PDF resultante. Deberías ver el rectángulo con una sombra nítida y desplazada—exactamente lo que **add shadow to shape** promete.

---

## Conclusión

Acabamos de demostrar cómo **add shadow to shape** en un documento Word usando Aspose.Words para Python, cubriendo los pasos esenciales para **set shadow distance**, personalizar desenfoque, ángulo y color, y finalmente exportar un PDF que conserve el efecto. Esta técnica funciona con cualquier tipo de forma, y puedes ampliarla con bucles, ajustes de opacidad o incluso sombras degradadas.

¿Listo para el próximo desafío? Prueba combinar múltiples sombras, superponer formas, o generar un informe donde cada gráfico tenga su propia sombra estilizada. Experimentar consolidará los conceptos y revelará nuevas posibilidades para la automatización de documentos.

Si encontraste útil esta guía, siéntete libre de compartirla, darle una estrella al repositorio de Aspose.Words, o dejar un comentario con tus propios consejos para ajustar sombras. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Tutorial de sombra de forma de Aspose.Words – Añadir una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}