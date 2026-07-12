---
category: general
date: 2026-06-27
description: Aprende cómo insertar una forma rectangular en Python usando Aspose.Words,
  cambiar el color de la sombra, agregar una sombra externa y aplicar un efecto de
  sombra a la forma, todo en un solo tutorial.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: es
og_description: Domina cómo insertar una forma rectangular en Python, cambiar su color
  de sombra, agregar una sombra externa y aplicar un efecto de sombra a la forma con
  Aspose.Words.
og_title: Cómo insertar una forma rectangular en Python – Tutorial de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Cómo insertar una forma rectangular en Python – Guía completa de Aspose.Words
url: /es/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar una forma de rectángulo en Python – Guía completa de Aspose.Words

¿Alguna vez te has preguntado **how to insert rectangle shape** en un documento Word usando Python? No eres el único; muchos desarrolladores se topan con este obstáculo al automatizar informes o crear plantillas. La buena noticia es que Aspose.Words lo hace muy sencillo, y en este tutorial recorreremos todo el proceso, desde dibujar el rectángulo hasta darle una sombra externa elegante.

También cubriremos **how to change shadow color**, **how to add outer shadow**, y el paso final de **apply shadow effect to shape**. Al final, tendrás un rectángulo totalmente estilizado que podrás insertar en cualquier archivo .docx de forma programática.

## Prerrequisitos

- Python 3.8+ instalado en tu máquina  
- Aspose.Words para Python mediante `pip install aspose-words`  
- Familiaridad básica con scripting en Python (no se requiere un conocimiento profundo de la API de Word)  

Si ya cuentas con esto, perfecto—¡vamos al grano! Si no, primero obtén la biblioteca; el resto de la guía asume que la importación funciona sin problemas.

## Cómo insertar una forma de rectángulo con Aspose.Words para Python

El primer paso es exactamente lo que promete la palabra clave principal: **how to insert rectangle shape**. Crearemos un nuevo documento, inicializaremos un `DocumentBuilder` y colocaremos un rectángulo en la página.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Por qué es importante:** La llamada `insert_shape` es el núcleo de *how to insert rectangle shape*. Devuelve un objeto `Shape` que luego puedes manipular—tamaño, posición, relleno, bordes, lo que necesites. Observa que también establecemos un `fill_color`; sin él, la sombra podría mezclarse con una página blanca, dificultando su visualización.

### Consejo profesional
Si necesitas que el rectángulo esté posicionado en una ubicación específica, usa `builder.move_to` antes de insertarlo, o ajusta `rectangle.left` y `rectangle.top` después de la creación.

## Cambiar el color de la sombra de una forma

Ahora que el rectángulo está en el documento, respondamos **how to change shadow color**. Aspose.Words expone un objeto `ShadowEffect` donde puedes establecer la propiedad `color` a cualquier valor RGB.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Por qué querrías esto:** Una sombra negra oscura puede resultar demasiado dura, sobre todo en documentos de colores claros. Ajustar el color te permite coincidir con la identidad corporativa o simplemente lograr un efecto visual más suave.

### Caso límite
Si olvidas establecer `shadow.opacity`, el valor predeterminado es totalmente opaco, lo que puede hacer que la sombra parezca una forma sólida. Siempre combina el cambio de color con un nivel de opacidad adecuado.

## Añadir un efecto de sombra externa

La siguiente pregunta que muchos hacen es **how to add outer shadow**. La bandera `ShadowStyle.OUTER` indica a Aspose.Words que renderice la sombra fuera del contorno de la forma en lugar de dentro.

El fragmento de código anterior ya usa `ShadowStyle.OUTER`, pero aíslemos esta configuración para mayor claridad:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Si cambias a `ShadowStyle.INNER`, la sombra aparecerá *dentro* del rectángulo, lo cual es útil para efectos de relieve. Para la mayoría de los escenarios de diseño de documentos, el estilo externo brinda un aspecto natural de sombra proyectada.

## Aplicar el efecto de sombra a tu forma

Ya hemos **apply shadow effect to shape** asignando `rectangle.shadow = shadow`. Ahora unamos todo y guardemos el documento, confirmando que el efecto persista.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Al abrir `RectangleWithShadow.docx` en Microsoft Word, deberías ver un rectángulo azul claro con una sutil sombra gris externa proyectada en un ángulo de 45°. La sombra estará ligeramente difuminada y desplazada, tal como la configuramos.

### Errores comunes
- **Directorio inexistente:** `doc.save` generará un error si la carpeta no existe. Créala primero o usa `os.makedirs`.
- **Incompatibilidad de versiones:** La API de sombra requiere Aspose.Words 22.9+; versiones anteriores ignoran silenciosamente la configuración de sombra.

## Ejemplo completo funcional

A continuación tienes el script completo, listo para ejecutar, que combina todos los pasos. Copia‑pega el contenido en un archivo llamado `rectangle_shadow.py` y ejecútalo con `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Salida esperada:** Un documento Word (`RectangleWithShadow.docx`) que contiene un único rectángulo con una sombra gris externa. Ábrelo en Word para verificar el efecto visual.

## Preguntas frecuentes

| Pregunta | Respuesta |
|----------|-----------|
| *¿Puedo usar otro tipo de forma?* | Por supuesto—reemplaza `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.TRIANGLE`, etc., y la misma lógica de sombra se aplicará. |
| *¿Qué pasa si necesito un borde más grueso?* | Establece `rectangle.line_width = 2.0` (puntos) antes de aplicar la sombra. |
| *¿Es posible animar la sombra?* | No directamente con Aspose.Words; tendrías que exportar a HTML/CSS para animaciones. |
| *¿Funciona en macOS?* | Sí—Aspose.Words es independiente de la plataforma siempre que Python se ejecute. |

## Conclusión

Hemos recorrido **how to insert rectangle shape**, demostrado **how to change shadow color**, explicado **how to add outer shadow**, y finalmente mostrado cómo **apply shadow effect to shape** usando Aspose.Words para Python. El script completo está listo para integrarse en cualquier pipeline de automatización, brindándote un rectángulo de aspecto profesional con una sombra pulida en segundos.

¿Listo para el siguiente paso? Prueba cambiar el color de relleno, experimentar con diferentes ángulos de `direction`, o añadir múltiples formas en la misma página. También puedes explorar la rica API de formato de texto de Aspose.Words para combinar sombras con texto estilizado—perfecto para informes llamativos.

Si este tutorial te resultó útil, dale un pulgar arriba, compártelo con tus compañeros o deja un comentario con tus propias variaciones. ¡Feliz codificación!

![Diagrama que muestra cómo insertar una forma de rectángulo con una sombra externa aplicada en un documento Word](/images/rectangle-shadow.png)


## ¿Qué deberías aprender a continuación?


Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos de implementación en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}