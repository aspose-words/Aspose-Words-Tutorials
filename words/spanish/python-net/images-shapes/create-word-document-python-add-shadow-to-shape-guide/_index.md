---
category: general
date: 2026-06-05
description: Ejemplo de creación de documento Word en Python que muestra cómo agregar
  sombra a una forma, aplicando el efecto de sombra en Word con Aspose.Words.
draft: false
keywords:
- create word document python
- how to add shadow
- add shadow to shape
- apply shadow effect word
- insert shape with shadow
language: es
og_description: El tutorial de Python para crear documentos Word te guía paso a paso
  para añadir una sombra a una forma y aplicar un efecto de sombra en Word usando
  Aspose.Words.
og_title: Crear documento de Word con Python – Añadir sombra a la forma
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Create Word document Python example shows how to add shadow to a shape,
    applying shadow effect in Word with Aspose.Words.
  headline: Create Word Document Python – Add Shadow to Shape Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Use `builder.insert_image(...)` to place an image, then access
      `image_shape.shadow_format` just like we did with the rectangle.
    question: Can I add a shadow to a picture instead of a shape?
  - answer: Yes. Aspose.Words preserves shape effects during conversion, so the PDF
      will retain the shadow.
    question: Does the shadow survive when I convert the document to PDF?
  - answer: Call `builder.insert_shape` for each shape, then configure each shape’s
      `shadow_format` independently. No shared state.
    question: What if I need multiple shapes with different shadows?
  - answer: 'Minimal for typical documents. If you’re generating thousands of shapes,
      consider batch processing or limiting blur radius to keep rendering fast. ##
      Conclusion We’ve just demonstrated how to **create Word document python** code
      that inserts a rectangle and **adds shadow to shape** using Aspose.Word'
    question: Is there a performance impact when adding many shadows?
  type: FAQPage
tags:
- python
- aspose-words
- document automation
title: Crear documento de Word con Python – Guía para agregar sombra a una forma
url: /es/python/images-shapes/create-word-document-python-add-shadow-to-shape-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word con Python – Guía para agregar sombra a una forma

¿Alguna vez te has preguntado cómo **crear documento Word python** con código que no solo inserte una forma sino que también le dé una sombra elegante? No eres el único. En muchos informes, facturas o folletos de marketing, una sombra sutil puede hacer que un rectángulo parezca elevarse de la página, añadiendo profundidad sin necesidad de gráficos adicionales.

En este tutorial recorreremos un ejemplo completo y ejecutable que muestra exactamente **cómo agregar sombra** a una forma usando Aspose.Words para Python. Al final tendrás un archivo `.docx` con un rectángulo que proyecta una sombra suave de 45 grados, perfecto para que tus documentos luzcan pulidos y profesionales.

## Qué cubre esta guía

Comenzaremos configurando el entorno, luego crearemos un nuevo documento Word, insertaremos un rectángulo, configuraremos sus propiedades de sombra y, finalmente, guardaremos el archivo. En el camino discutiremos por qué cada ajuste es importante, errores comunes y algunos trucos extra que puedes probar. No se requieren referencias externas; todo lo que necesitas está aquí.

**Requisitos previos**

- Python 3.8+ instalado  
- Paquete `aspose-words` (`pip install aspose-words`)  
- Familiaridad básica con la sintaxis de Python (si ya has escrito un “Hello, World!”, estás listo)

¿Listo? Vamos allá.

## Paso 1: Inicializar el documento – Conceptos básicos de **Create Word Document Python**

Lo primero que necesitas es un objeto de documento vacío y un `DocumentBuilder` que te permita añadir contenido. Piensa en el builder como una pluma que escribe dentro del archivo Word.

```python
import aspose.words as aw

# Create a new, empty Word document
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add elements
builder = aw.DocumentBuilder(doc)
```

*Por qué es importante:* `aw.Document()` es el punto de entrada para cualquier operación de Aspose.Words. Sin él no puedes agregar formas, texto ni ningún otro elemento. El builder mantiene una referencia al documento, por lo que no tienes que pasar el documento manualmente.

## Paso 2: Insertar un rectángulo – Lógica de **Insert Shape With Shadow**

Ahora colocaremos un rectángulo en la página. Las dimensiones están en puntos (1 pt ≈ 1/72 pulgada), así que 150 × 100 pts da una caja bien proporcionada.

```python
# Insert a rectangle shape of 150x100 points
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
```

*Consejo profesional:* Si necesitas una forma diferente, simplemente cambia `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`, `ShapeType.CLOUD`, etc. El mismo código de configuración de sombra funciona para cualquier forma que elijas.

## Paso 3: Aplicar el efecto de sombra – **How To Add Shadow** con precisión

Aquí es donde ocurre la magia. El objeto `shadow_format` controla la visibilidad, distancia, desenfoque, ángulo, color y transparencia. Ajusta cada propiedad para obtener el aspecto que deseas.

```python
# Grab the shadow formatting object
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set how far the shadow sits from the shape (in points)
shadow.distance = 5.0

# Blur radius controls softness; higher = fuzzier edges
shadow.blur = 3.0

# Angle determines the light source direction (degrees clockwise from the x‑axis)
shadow.angle = 45

# Choose a color – black works for most professional documents
shadow.color = aw.drawing.Color.black

# Transparency is a float from 0 (opaque) to 1 (fully transparent)
shadow.transparency = 0.4   # 40 % transparent gives a subtle effect
```

**Por qué cada ajuste es importante**

| Propiedad | Uso típico | Impacto visual |
|-----------|------------|----------------|
| `visible` | Activa o desactiva el efecto | No hay sombra si es `False` |
| `distance` | Controla el desplazamiento respecto a la forma | Valores mayores alejan más la sombra |
| `blur` | Suaviza los bordes | Un mayor desenfoque = sombra más difusa |
| `angle` | Simula la dirección de la luz | 0° = sombra a la derecha, 90° = abajo |
| `color` | Coincide con la marca o tema | Las sombras blancas rara vez tienen sentido |
| `transparency` | Ajusta la opacidad | 0.0 = sólido, 0.8 = apenas perceptible |

*Error común:* Olvidar establecer `shadow.visible = True` produce una forma perfectamente válida pero sin sombra, algo fácil de pasar por alto cuando te concentras en el color o el tamaño.

## Paso 4: Guardar el documento – Paso final de **Create Word Document Python**

Después de configurar la forma, simplemente escribe el documento en disco. Puedes elegir cualquier formato compatible (`.docx`, `.pdf`, `.html`, etc.). Para esta guía nos quedaremos con el clásico `.docx`.

```python
# Save the document to the desired location
output_path = "shadowed_shape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Al abrir `shadowed_shape.docx` en Microsoft Word (o cualquier visor compatible), verás un rectángulo con una sombra nítida de 45 grados, exactamente como describe el código anterior.

### Resultado esperado

- Un archivo Word de una sola página.  
- Un rectángulo centrado donde estaba posicionado el builder.  
- Una sombra negra semi‑transparente desplazada 5 pts, desenfocada 3 pts, proyectada a 45°.

Si no ves la sombra, verifica que `shadow.visible` sea `True` y que estés usando un visor que respete los efectos de forma (la mayoría de versiones modernas de Word lo hacen).

## Bonus: Ajustar la sombra para diferentes estilos

Quizás quieras un aspecto más suave para un informe corporativo, o una sombra audaz y coloreada para un folleto de marketing. Aquí tienes algunas variaciones rápidas:

```python
# Soft gray shadow for subtle emphasis
shadow.color = aw.drawing.Color.gray
shadow.transparency = 0.6
shadow.blur = 5.0
shadow.distance = 3.0

# Red, dramatic shadow for a creative brochure
shadow.color = aw.drawing.Color.red
shadow.transparency = 0.2
shadow.blur = 2.0
shadow.angle = 120
```

Experimentar con estos valores es la mejor manera de entender cómo **add shadow to shape** funciona en la práctica.

## Vista previa visual (texto alternativo incluido)

![Shadowed rectangle shape in a Word document – create word document python example](/images/shadowed_rectangle.png)

*Texto alternativo:* *Forma de rectángulo con sombra en un documento Word – ejemplo de crear documento Word con Python.*

## Preguntas frecuentes

**P: ¿Puedo agregar una sombra a una imagen en lugar de a una forma?**  
R: Absolutamente. Usa `builder.insert_image(...)` para colocar una imagen, luego accede a `image_shape.shadow_format` igual que hicimos con el rectángulo.

**P: ¿La sombra se mantiene al convertir el documento a PDF?**  
R: Sí. Aspose.Words conserva los efectos de forma durante la conversión, por lo que el PDF retendrá la sombra.

**P: ¿Qué pasa si necesito varias formas con sombras diferentes?**  
R: Llama a `builder.insert_shape` para cada forma y configura cada `shadow_format` de manera independiente. No hay estado compartido.

**P: ¿Existe un impacto de rendimiento al agregar muchas sombras?**  
R: Mínimo para documentos típicos. Si generas miles de formas, considera el procesamiento por lotes o limitar el radio de desenfoque para mantener la renderización rápida.

## Conclusión

Acabamos de demostrar cómo **create Word document python** con código que inserta un rectángulo y **adds shadow to shape** usando Aspose.Words. Al configurar `shadow_format`, puedes **apply shadow effect word** en documentos con control granular sobre distancia, desenfoque, ángulo, color y transparencia. El mismo patrón funciona para cualquier forma, imagen o incluso cuadro de texto, dándote una caja de herramientas versátil para documentos de aspecto profesional.

¿Qué sigue? Prueba combinar múltiples formas, superponer texto encima o exportar a PDF para ver que la sombra sobrevive a la conversión. También puedes explorar otros efectos visuales como brillo o reflexión—simplemente reemplaza `shadow_format` por `glow_format` o `reflection_format`.

¡Feliz codificación, y que tus documentos siempre tengan esa profundidad extra!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos de implementación en tus propios proyectos.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}