---
category: general
date: 2026-11-25
description: Agregar sombra a una forma en un documento de Word con Python. Aprende
  cómo insertar una forma rectangular en Word y aplicar una sombra transparente usando
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: es
lastmod: 2026-11-25
og_description: Agregar sombra a una forma en un documento de Word usando Python.
  Este tutorial muestra cómo insertar una forma rectangular en Word y establecer una
  sombra con un 30 % de transparencia con Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Añadir sombra a una forma en un documento de Word con Python – guía paso
  a paso
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Cómo agregar sombra a una forma en un documento de Word usando Python
url: /es/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar sombra a una forma en un documento Word usando Python

Si necesitas **agregar sombra a una forma** en un documento Word, esta guía te muestra una solución completa y ejecutable. Verás cómo crear un archivo Word, insertar una forma rectangular y aplicar una sombra con un 30 % de transparencia, todo con la biblioteca Aspose.Words para Python.

Trabajar con documentos Word de forma programática te ahorra el formateo manual y te permite generar informes, contratos o folletos de marketing a gran escala. Al final de este tutorial podrás responder “**cómo crear documento Word python**” con un ejemplo de código listo para ejecutar.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Python 3.8 o superior instalado.
* Una licencia activa de Aspose.Words para Python (la prueba gratuita funciona para evaluación).
* Paquete `aspose-words` instalado mediante `pip install aspose-words`.
* Una carpeta donde se pueda escribir el archivo de salida (reemplaza `YOUR_DIRECTORY` en el código).

No se requieren dependencias adicionales.

## Paso 1: Crear un nuevo documento Word

El primer paso es instanciar un objeto `Document`. Este objeto representa todo el archivo .docx en memoria.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` funciona como un cursor virtual. Cuando llamas a sus métodos, la biblioteca inserta los elementos correspondientes en la ubicación actual del cursor.

## Paso 2: Insertar forma rectangular en Word

A continuación **insertas una forma rectangular** usando el método `insert_shape` del builder. El método requiere el tipo de forma y su tamaño en puntos (1 punto = 1/72 de pulgada).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Puedes cambiar las dimensiones para que coincidan con tu diseño. El rectángulo pasa a ser parte de la capa de dibujo del documento, lo que significa que luego podrás modificar su relleno, contorno o sombra.

## Paso 3: Acceder al formato de sombra de la forma

Cada objeto de dibujo expone una propiedad `shadow_format` que controla la apariencia de la sombra. Obténla para poder ajustar la transparencia, desplazamiento, difuminado y color.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

En este punto la forma tiene la sombra predeterminada (sin sombra). El objeto `ShadowFormat` contiene todos los parámetros que necesitas para crear un efecto realista.

## Paso 4: Hacer la sombra 30 % transparente

La transparencia se expresa como un valor entre `0` (totalmente opaco) y `1` (totalmente transparente). Configurarla en `0.3` produce una sombra con un 30 % de transparencia, lo que suele ser suficiente para añadir profundidad sin opacar el texto.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Estas propiedades adicionales no son obligatorias, pero ilustran cómo puedes afinar el efecto. La bandera `visible` es esencial; si la olvidas, la sombra no aparecerá aunque los demás ajustes estén configurados.

## Paso 5: Guardar el documento para ver el resultado

Finalmente, escribe el documento en disco. Abrir el archivo `.docx` resultante en Microsoft Word o cualquier visor compatible muestra el rectángulo con la sombra transparente aplicada.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Al abrir `output.docx`, verás un rectángulo sencillo con una sutil sombra gris desplazada hacia la esquina inferior derecha. La transparencia del 30 % hace que la forma parezca levantada de la página.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Ejemplo de agregar sombra a una forma en un documento Word creado con Python"}

## Script completo y ejecutable

Unir todas las piezas te brinda un script autocontenido que puedes copiar, pegar y ejecutar de inmediato.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Salida esperada:** Al abrir el `output.docx` generado se muestra una sola página con un rectángulo que proyecta una sombra ligera y semitransparente. No se requiere formateo adicional.

## Variaciones comunes y casos límite

| Situación | Cómo adaptar el código |
|-----------|------------------------|
| **Tipo de forma diferente** (p. ej., elipse) | Cambia `aw.drawing.ShapeType.RECTANGLE` por `aw.drawing.ShapeType.ELLIPSE`. |
| **Color de sombra personalizado** | Establece `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` para una sombra rojiza. |
| **Múltiples formas** | Llama a `builder.insert_shape` repetidamente; cada llamada devuelve un objeto `Shape` independiente que puedes estilizar por separado. |
| **Guardar como PDF** | Reemplaza `doc.save(output_path)` por `doc.save(output_path.replace('.docx', '.pdf'))` y usa la extensión `.pdf`. |
| **Ejecutar sin licencia** | La prueba gratuita agrega una marca de agua a la primera página. Obtén una licencia para eliminarla en entornos de producción. |

Estas variaciones demuestran que el mismo patrón —crear un documento, insertar una forma, ajustar `shadow_format`, guardar— cubre la mayoría de los escenarios de automatización.

## Consejos y buenas prácticas

* **Reutiliza el builder**: Mantén una única instancia de `DocumentBuilder` para todo el documento y evita crear objetos innecesarios.
* **Libera recursos**: En servicios de larga duración, llama a `doc.dispose()` después de guardar para liberar memoria nativa.
* **Valida la salida**: Usa `doc.validate(aw.ValidationType.FULL_VALIDATION)` antes de guardar si necesitas garantizar el cumplimiento del estándar Open XML.
* **Compatibilidad de versiones**: El código funciona con Aspose.Words para Python ≥ 22.9. Asegúrate de que tu paquete esté actualizado con `pip install --upgrade aspose-words`.

## Conclusión

Ahora sabes cómo **agregar sombra a una forma** en un documento Word usando Python. Siguiendo los cinco pasos —crear un documento, **insertar forma rectangular en Word**, configurar la sombra y guardar— puedes automatizar la generación de documentos pulidos para informes, facturas o materiales de marketing.

A partir de aquí puedes explorar otras opciones de formato, como rellenos degradados, ajuste de texto o la conversión del documento a PDF. Cada uno de esos temas se basa en los mismos conceptos de `DocumentBuilder` y formato de formas presentados en este tutorial.

¡Feliz codificación y disfruta de la profundidad visual que una simple sombra puede aportar a tus documentos Word automatizados!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}