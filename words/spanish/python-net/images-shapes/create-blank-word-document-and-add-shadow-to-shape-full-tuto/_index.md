---
category: general
date: 2026-07-20
description: Crea un documento Word en blanco con Aspose.Words y agrega sombra a una
  forma. Aprende cómo cambiar la opacidad y la transparencia de la sombra en solo
  unos pocos pasos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- add shadow effect
- change shadow transparency
- change shadow opacity
language: es
lastmod: 2026-07-20
og_description: Crear un documento Word en blanco usando Aspose.Words y añadir un
  efecto de sombra a una forma. Cambiar la opacidad y la transparencia de la sombra
  con ejemplos de código claros.
og_image_alt: Screenshot showing a Word document with a shape that has a semi‑transparent
  shadow
og_title: Crear documento de Word en blanco y agregar sombra a la forma – Guía paso
  a paso
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  type: TechArticle
- description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  name: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  steps:
  - name: Expected Output
    text: When you open **ShadowedShape.docx**, you should see a rectangle with a
      gray, semi‑transparent shadow that has a gentle blur. The shadow will be offset
      slightly down and to the right, giving the illusion that the shape is lifted
      off the page.
  - name: What if the document already contains multiple shapes?
    text: 'The current script grabs the *first* shape (`index 0`). To target a specific
      shape, change the index or iterate over all shapes:'
  - name: Can I change the shadow color?
    text: 'Absolutely. Shadow color is another property:'
  - name: How do I make the shadow offset differently?
    text: 'Adjust `distance_x` and `distance_y`:'
  - name: Does this work with older Word versions?
    text: Aspose.Words writes the modern OOXML format (`.docx`). Word 2007+ can open
      it without issues. For legacy `.doc` files, call `doc.save("file.doc", aw.SaveFormat.DOC)`—the
      shadow properties will still be preserved.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
- Word Shapes
title: Crear documento de Word en blanco y añadir sombra a la forma – Tutorial completo
url: /es/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-tuto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco y añadir sombra a una forma – Tutorial completo

¿Alguna vez necesitaste **crear un documento Word en blanco** y luego hacer que una forma destaque con una sombra sutil? No eres el único. En muchos informes, folletos o paneles internos, un poco de profundidad puede convertir un rectángulo plano en una pista visual que atrae la mirada.  

En esta guía recorreremos cómo generar un archivo Word nuevo con Aspose.Words para Python, extraer la primera forma y luego **añadir sombra a la forma** mientras ajustamos su opacidad y difuminado. Al final tendrás un documento con un aspecto pulido—sin necesidad de ajustes manuales.

> **Lo que obtendrás** – un script completo y ejecutable, explicaciones de *por qué* cada línea es importante y consejos para manejar documentos que no contengan ya una forma.

## Requisitos previos

- Python 3.8+ instalado (cualquier versión reciente sirve)
- Aspose.Words para Python mediante `pip install aspose-words`
- Familiaridad básica con Python y el concepto de una “forma” en Word (pensa en un cuadro de texto, imagen o auto‑forma)

No se necesitan otras librerías; el código es autónomo.

## Paso 1: Crear un documento Word en blanco con Aspose.Words

Lo primero, necesitamos un lienzo limpio. Aspose.Words lo hace trivial—simplemente instancia un objeto `Document`.

```python
import aspose.words as aw

# Step 1: Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")
```

*Por qué es importante*: La clase `Document` es el punto de entrada para cada operación. Comenzar con un documento nuevo garantiza que no haya sorpresas de formato ocultas más adelante.

## Paso 2: Insertar una forma de ejemplo (para que haya algo a la que aplicar sombra)

Si ejecutas el script en un archivo vacío tendrás un problema al intentar obtener una forma—simplemente no existe. Añadamos un rectángulo sencillo para que los pasos siguientes tengan un objetivo.

```python
# Step 2: Add a rectangle shape to the first page
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")
```

> **Consejo profesional**: Ajusta los valores de ancho/alto (200, 100) según tus necesidades de diseño. Las formas más grandes muestran las sombras con mayor claridad.

## Paso 3: Recuperar la primera forma del documento

Ahora que tenemos una forma, podemos extraerla con seguridad. El método `get_child` recorre el árbol de nodos y devuelve el primer nodo del tipo solicitado.

```python
# Step 3: Retrieve the first shape (index 0) – true = deep search
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")
```

*Por qué verificamos `None`*: En escenarios reales el documento podría generarse en otro lugar, y una forma ausente provocaría un críptico `AttributeError`. Lanzar una excepción clara ahorra tiempo de depuración.

## Paso 4: Añadir efecto de sombra – Cambiar la opacidad de la sombra

Una sombra no es solo un adorno visual; puede transmitir jerarquía. Hagámosla semitransparente estableciendo la opacidad al 75 %.

```python
# Step 4: Set shadow opacity (0.0 = fully transparent, 1.0 = fully opaque)
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")
```

**Entendiendo la opacidad**: El valor es un número flotante entre 0 y 1. Los números bajos hacen que la sombra se desvanezca en el fondo, los números altos la hacen más visible. Para la mayoría de documentos con estilo UI, 0.5–0.8 se ve natural.

## Paso 5: Definir el difuminado de la sombra – Cambiar la transparencia de la sombra

El radio de difuminado controla cuán suave es el borde de la sombra. Un radio mayor produce una transición más delicada, imitando la difusión de la luz natural.

```python
# Step 5: Define blur radius (in points) for a softer edge
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")
```

*Por qué el difuminado importa*: Una sombra de borde duro puede parecer barata, mientras que un difuminado sutil añade profundidad sin abrumar el contenido.

## Paso 6: Guardar el documento y verificar el resultado

Finalmente, escribimos el documento en disco. Abre el `.docx` resultante en Word para ver el rectángulo con su nueva sombra.

```python
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

### Resultado esperado

Al abrir **ShadowedShape.docx**, deberías ver un rectángulo con una sombra gris, semitransparente y con un difuminado suave. La sombra estará ligeramente desplazada hacia abajo y a la derecha, dando la ilusión de que la forma está levantada de la página.

## Casos límite y preguntas frecuentes

### ¿Qué pasa si el documento ya contiene varias formas?

El script actual toma la *primera* forma (`índice 0`). Para apuntar a una forma específica, cambia el índice o itera sobre todas las formas:

```python
for i in range(doc.get_child_nodes(aw.NodeType.SHAPE, True).count):
    shp = doc.get_child(aw.NodeType.SHAPE, i, True)
    # Apply shadow settings to each shape
    shp.shadow.opacity = 0.6
    shp.shadow.blur_radius = 5.0
```

### ¿Puedo cambiar el color de la sombra?

Claro. El color de la sombra es otra propiedad:

```python
shape.shadow.color = aw.drawing.Color.black
```

### ¿Cómo hago que el desplazamiento de la sombra sea diferente?

Ajusta `distance_x` y `distance_y`:

```python
shape.shadow.distance_x = 5   # shift right
shape.shadow.distance_y = 5   # shift down
```

### ¿Funciona esto con versiones antiguas de Word?

Aspose.Words escribe el formato OOXML moderno (`.docx`). Word 2007+ lo abre sin problemas. Para archivos legados `.doc`, llama a `doc.save("file.doc", aw.SaveFormat.DOC)`—las propiedades de sombra seguirán preservadas.

## Recapitulación del script completo

Juntando todo, aquí tienes el ejemplo completo, listo para ejecutar:

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")

# Insert a rectangle shape (so we have something to shadow)
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")

# Retrieve the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")

# Add shadow effect – change opacity
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")

# Change shadow transparency – define blur radius
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")

# Optional: tweak color and offset
shape.shadow.color = aw.drawing.Color.gray
shape.shadow.distance_x = 4
shape.shadow.distance_y = 4

# Save the document
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

Ejecuta este script, abre el archivo generado y verás la forma bañada en una sombra elegante—exactamente lo que necesita un informe pulido.

## Conclusión

Ahora sabes **cómo crear un documento Word en blanco** con Aspose.Words, insertar una forma y **añadir sombra a la forma** mientras dominas *cambiar la opacidad de la sombra* y *cambiar la transparencia de la sombra*. Los pasos son sencillos, pero el impacto visual es considerable.  

A continuación, podrías explorar **añadir efecto de sombra** a imágenes, experimentar con diferentes valores de `blur_radius`, o combinar varias formas en un solo gráfico compuesto. Para profundizar, consulta la documentación de Aspose sobre [Shape Formatting](https://docs.aspose.com/words/python-net/shape/) y la guía más amplia de [Document Automation](https://docs.aspose.com/words/python-net/).

¿Probaste alguna variante? Deja un comentario abajo—compartir ajustes del mundo real fortalece a la comunidad. ¡Feliz codificación!


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye código completo y funcional con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}