---
category: general
date: 2026-05-04
description: Aprenda cómo crear una forma rectangular, cómo agregar una forma con
  sombras, cambiar el color de la sombra, establecer la distancia de la sombra y guardar
  el documento como PDF usando Aspose.Words para Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: es
og_description: Crea una forma rectangular con Aspose.Words para Python, aprende cómo
  agregar una forma, cambiar el color de la sombra, establecer la distancia de la
  sombra y guardar el documento como PDF.
og_title: Crear forma de rectángulo – Añadir sombra, cambiar color y guardar como
  PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Crear forma de rectángulo en Python – Guía completa para añadir sombras y guardar
  como PDF
url: /es/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular – Tutorial completo para desarrolladores Python

¿Alguna vez necesitaste **crear forma rectangular** en un documento Word y te preguntaste cómo darle una sombra pulida? Tal vez estés construyendo un generador de informes y el acabado visual sea importante, sobre todo cuando el resultado final es un PDF. ¿La buena noticia? Con Aspose.Words for Python no solo puedes **cómo agregar forma**, sino también ajustar cada propiedad de la sombra, desde el color hasta la distancia, y luego **guardar documento como pdf** en un flujo continuo.

En esta guía recorreremos todo el proceso paso a paso. Verás el código exacto que puedes copiar‑pegar, entenderás *por qué* cada línea es importante y aprenderás algunos trucos para manejar casos límite (como sombras transparentes o DPI no estándar). Al final podrás **crear forma rectangular**, personalizar su sombra y exportar un PDF nítido sin sudar.

## Prerrequisitos

- Python 3.8+ instalado en tu máquina.  
- Aspose.Words for Python vía `pip install aspose-words`.  
- Familiaridad básica con Python orientado a objetos (nada complicado).  

Si ya tienes un entorno virtual configurado, solo ejecuta el comando de instalación y estarás listo.

## Paso 1: Inicializar el Document y el Builder

Antes de poder **cómo agregar forma**, necesitas un documento en blanco con el que trabajar. La clase `Document` representa todo el archivo, y `DocumentBuilder` es tu pincel.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Por qué es importante:* `Document` contiene todas las secciones, páginas y recursos. `DocumentBuilder` te brinda una API fluida para insertar contenido exactamente donde lo necesitas, como un cursor en un procesador de textos.

## Paso 2: Insertar la forma rectangular

Ahora realmente **cómo agregar forma**. El método `insert_shape` necesita el tipo de forma y sus dimensiones (en puntos). Aquí elegimos un rectángulo de 200 × 100 pt y le damos un relleno azul claro.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Consejo profesional:* Si necesitas que la forma se alinee con texto existente, usa `builder.move_to` antes de insertarla, o ajusta las propiedades `left`/`top` después de crearla.

## Paso 3: Activar la sombra

Una forma sin sombra se ve plana. Para **establecer distancia de sombra** y que el efecto sea visible, obtén el formato de sombra y habilítalo.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Por qué este paso:* El formato de sombra es un objeto separado; activar `visible` es lo primero que debes hacer, de lo contrario todas las demás propiedades de sombra se ignoran.

## Paso 4: Estilizar la sombra – Color, Difuminado, Distancia, Dirección

Aquí es donde ocurre la magia. **Cambiaremos el color de la sombra**, ajustaremos el radio de difuminado, definiremos qué tan lejos está la sombra del rectángulo y la rotaremos 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Explicación de cada propiedad:*

| Propiedad | Qué hace | Valores típicos |
|-----------|----------|-----------------|
| `style` | Determina si la sombra es *interna* o *externa*. | `OUTER` (más común) |
| `blur_radius` | Controla la suavidad; mayor = bordes más difusos. | 0–20 px es lo habitual |
| `distance` | Qué tan lejos está la sombra del contorno de la forma. | 0–10 pt para sutil, >10 para dramático |
| `direction` | Ángulo de la fuente de luz, medido en sentido horario desde el eje x. | 0‑360° |
| `color` | Tono de la sombra. | Cualquier `aw.Color` (p. ej., `gray`, `dark_red`) |

*Caso límite:* Si estableces `distance` a `0`, la sombra quedará justo debajo de la forma, ocultando efectivamente el relleno de la forma. Mantén un valor superior a `0` para un desplazamiento visible.

## Paso 5: Guardar el documento como PDF

Finalmente, **guardamos documento como pdf**. Aspose.Words rasteriza automáticamente la sombra, de modo que el PDF se ve exactamente como la vista en Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*¿Por qué PDF?* Los PDFs conservan el diseño en todas las plataformas, lo que los hace perfectos para informes, facturas o cualquier artefacto imprimible.

---

![Crear forma rectangular con sombra](https://example.com/images/rectangle-shadow.png){: .align-center alt="ejemplo de crear forma rectangular con sombra"}

*La imagen anterior muestra el resultado final en PDF: un rectángulo azul claro con una sombra gris externa suave, exactamente como la configuramos.*

## Preguntas frecuentes y variaciones

### ¿Qué pasa si necesito una sombra **transparente**?

Establece el canal alfa en el color de la sombra:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### ¿Puedo aplicar la misma sombra a varias formas?

Sí. Extrae el `ShadowFormat` de una forma y asígnalo a otra:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### ¿Cómo cambio la sombra para un **tipo de forma diferente**?

Todos los tipos de forma comparten las mismas propiedades de `ShadowFormat`, por lo que puedes reutilizar el mismo bloque de configuración—solo reemplaza `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.TRIANGLE`, etc.

### ¿Qué hay de los **PDF de alta resolución** para impresión?

Especifica `PdfSaveOptions` con un DPI mayor:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Resumen

Hemos cubierto todo lo que necesitas para **crear forma rectangular**, **cómo agregar forma**, personalizar su **color de sombra**, **establecer distancia de sombra**, y finalmente **guardar documento como pdf**. El script completo y ejecutable se ve así:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Ejecuta el script, abre el `ShadowedShape.pdf` resultante y verás un rectángulo nítido con una sombra gris sutil—exactamente lo que esperarías de un informe formateado profesionalmente.

## ¿Qué sigue?

- **Explora otros tipos de forma** (`ShapeType.OVAL`, `ShapeType.LINE`) para enriquecer tus documentos.  
- **Combina múltiples sombras** superponiendo formas; incluso puedes crear un efecto de “resplandor” usando una sombra interna con un color brillante.  
- **Automatiza el procesamiento por lotes**: recorre una colección de filas de datos, genera una forma por fila y combina todo en un solo PDF.  
- **Integra con otras bibliotecas Aspose** (p. ej., Aspose.Slides) si necesitas exportar el mismo visual a PowerPoint.

Siéntete libre de experimentar—cambia el `blur_radius`, juega con `direction`, o sustituye `gray` por un tono específico de tu marca. La API es lo suficientemente flexible como para que unos pocos ajustes cambien drásticamente el impacto visual.

¿Tienes preguntas o un escenario complicado? Deja un comentario abajo o visita los foros de la comunidad Aspose. ¡Feliz codificación y disfruta de esos rectángulos bellamente sombreados!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}