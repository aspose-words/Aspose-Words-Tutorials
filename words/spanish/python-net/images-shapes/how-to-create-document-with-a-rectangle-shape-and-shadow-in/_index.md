---
category: general
date: 2026-10-04
description: Cómo crear un documento en Python y agregar sombra a una forma usando
  Aspose.Words. Aprende a establecer el color de la sombra, insertar una forma rectangular
  y personalizar la sombra externa.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: es
lastmod: 2026-10-04
og_description: Cómo crear un documento en Python y agregar sombra a una forma. Esta
  guía le muestra cómo establecer el color de la sombra, insertar una forma rectangular
  y aplicar una sombra externa usando Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Cómo crear un documento con una forma rectangular y sombra en Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Cómo crear un documento con una forma rectangular y sombra en Python
url: /es/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento con una forma rectangular y sombra en Python

Si necesitas **cómo crear un documento** que contenga un rectángulo con estilo, esta guía ofrece una solución completa. Verás cómo **agregar sombra a la forma**, establecer el color de la sombra y controlar su desplazamiento y difuminado, todo con Aspose.Words for Python. Al final del tutorial podrás generar un archivo `.docx` que se ve pulido y listo para distribuir.

Los pasos a continuación cubren todo, desde la instalación de la biblioteca hasta la personalización de la apariencia de la sombra. No se requiere documentación externa; el código está listo para copiar, ejecutar y adaptar a tus propios proyectos. También aprenderás a **insertar forma rectangular**, elegir un **estilo de sombra externa** y manejar problemas comunes como sombras invisibles o configuraciones de ajuste incorrectas.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Python 3.8 o superior instalado.
* Una licencia activa de Aspose.Words for Python (o una clave de evaluación gratuita).
* Familiaridad básica con la escritura de scripts en Python.
* Acceso a una ubicación del sistema de archivos donde se guardará el documento generado.

Puedes instalar el SDK con pip:

```bash
pip install aspose-words
```

## Paso 1: Importar la biblioteca y crear un nuevo documento en blanco

Crear un nuevo documento es la primera acción en cualquier escenario de automatización de Word. El constructor `aw.Document()` te proporciona un archivo vacío que puedes rellenar con texto, imágenes o formas.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

El objeto `DocumentBuilder` simplifica la inserción de contenido. Mantiene el seguimiento de la posición actual del cursor, de modo que puedes añadir elementos secuencialmente sin gestionar manualmente las secciones.

## Paso 2: Insertar una forma rectangular del tamaño deseado

Una forma rectangular actúa como contenedor para elementos visuales. Puedes definir su ancho y alto en puntos (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

En este punto la forma no tiene estilo visual, por lo que aparece como un contorno simple. Los siguientes pasos le darán profundidad y color.

## Paso 3: Configurar la forma para que fluya en línea con el texto circundante

Cuando una forma está **en línea**, se comporta como un carácter dentro de un párrafo. Esto asegura que el rectángulo permanezca donde esperas en el diseño del documento.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Si prefieres que la forma flote sobre el texto, podrías usar `WrapType.SQUARE` o `WrapType.TOP_BOTTOM`, pero para la mayoría de los informes una forma en línea mantiene el diseño predecible.

## Paso 4: Hacer visible la sombra y elegir su color

Una sombra que no es visible no aporta ningún beneficio visual. La bandera `visible` activa el efecto, y la propiedad `color` determina su tono. Usar negro brinda una profundidad clásica y sutil.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Puedes reemplazar `aw.drawing.Color.black` por cualquier otro color, como `aw.drawing.Color.gray` o un valor RGB personalizado (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Paso 5: Definir el desplazamiento y difuminado de la sombra para darle profundidad

El desplazamiento controla qué tan lejos se desplaza la sombra de la forma, mientras que el radio de difuminado suaviza los bordes. Valores pequeños crean una sombra nítida; valores mayores producen un aspecto más suave.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Experimenta con estos números para que coincidan con tus guías de diseño. Para una sombra de caída pronunciada podrías aumentar tanto el desplazamiento como el difuminado.

## Paso 6: Elegir un estilo de sombra externa

Aspose.Words ofrece varios estilos de sombra, como `INNER`, `OUTER` y `PERSPECTIVE`. El estilo **externo** coloca la sombra fuera del borde de la forma, lo que es ideal para una apariencia limpia y profesional.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Si necesitas un efecto más dramático, prueba `ShadowStyle.PERSPECTIVE`; añade una inclinación tridimensional.

## Paso 7: Guardar el documento con la sombra aplicada a la forma

Guardar finaliza el archivo y escribe todo el formato en disco. Elige un directorio donde tengas permisos de escritura y asigna al archivo un nombre descriptivo.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Ejecutar el script genera un archivo Word que contiene un rectángulo con una sombra visible y coloreada. Abre el archivo en Microsoft Word o LibreOffice para verificar el resultado.

## Ejemplo completo ejecutable

A continuación tienes el script completo que incorpora cada paso descrito. Copia el código en un archivo llamado `create_shadowed_shape.py` y ejecútalo con `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Salida esperada**

Al abrir `ShapeWithShadow.docx`, verás un único rectángulo centrado en la página. El rectángulo está acompañado por una sutil sombra negra desplazada hacia la esquina inferior derecha, ligeramente difuminada para crear profundidad. La sombra respeta el estilo externo, por lo que no intersecta el interior del rectángulo.

## Preguntas comunes y casos límite

### ¿Por qué a veces la sombra aparece invisible?

La sombra solo se renderiza si `shadow.visible` está establecido en `True` **y** el `wrap_type` de la forma permite que se muestre. Una forma en línea funciona de manera fiable; las formas flotantes pueden requerir ajustes adicionales de diseño.

### ¿Cómo puedo cambiar el color de la sombra para que coincida con la paleta de la marca?

Reemplaza `aw.drawing.Color.black` por un valor RGB personalizado:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### ¿Qué pasa si necesito que la forma aparezca detrás del texto?

Establece el tipo de ajuste a `WrapType.BEHIND` y ajusta `z_order_position` si es necesario. Ten en cuenta que algunos visores pueden renderizar las formas detrás del texto de manera diferente.

### ¿Puedo aplicar la misma configuración de sombra a varias formas?

Sí. Crea una función auxiliar que configure la sombra y llámala para cada forma que insertes. Esto favorece la reutilización de código y garantiza un estilo consistente.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Conclusión

Ahora sabes **cómo crear un documento** que contenga una forma rectangular con una sombra personalizada usando Aspose.Words for Python. El tutorial cubrió la inserción de un rectángulo, la configuración de la forma en línea, la activación de la sombra, la definición de su color, desplazamiento, difuminado y estilo, y finalmente la guardado del archivo.

A partir de aquí puedes explorar temas relacionados como **agregar sombra a la forma** para otros tipos de formas, **establecer el color de la sombra** dinámicamente según los datos, o **cómo agregar sombra** a imágenes y cuadros de texto. Experimenta con diferentes dimensiones, colores y estilos de sombra para que coincidan con las directrices de tu marca o sistema de diseño.

¿Listo para automatizar más documentos Word? Prueba a añadir tablas, encabezados o contenido dinámico a continuación; cada paso se basa en los mismos principios demostrados aquí. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma rectangular, agregar sombra y guardar como PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Crear documento Word en blanco con forma rectangular sombreada – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Cómo administrar variables de documento con Aspose.Words en Python&#58; Guía completa](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}