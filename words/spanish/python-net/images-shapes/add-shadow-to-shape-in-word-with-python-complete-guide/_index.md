---
category: general
date: 2026-07-29
description: Agregar sombra a una forma en Word usando Python y Aspose.Words. Aprende
  cómo aplicar el efecto de sombra en documentos de Word rápidamente con un ejemplo
  de código completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- apply shadow effect word
language: es
lastmod: 2026-07-29
og_description: Añade sombra a una forma en documentos de Word con Python. Esta guía
  muestra cómo aplicar el efecto de sombra a archivos de Word usando Aspose.Words,
  con código y consejos.
og_image_alt: Word document displaying a rectangle shape with a soft gray shadow applied
og_title: Agregar sombra a una forma en Word – Tutorial de Python
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  headline: Add Shadow to Shape in Word with Python – Complete Guide
  type: TechArticle
- description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  name: Add Shadow to Shape in Word with Python – Complete Guide
  steps:
  - name: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
    text: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
  - name: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
    text: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
  - name: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
    text: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Agregar sombra a una forma en Word con Python – Guía completa
url: /es/python/images-shapes/add-shadow-to-shape-in-word-with-python-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Añadir sombra a una forma en Word con Python – Guía completa

¿Alguna vez necesitaste **añadir sombra a una forma** en un documento de Word pero no sabías por dónde empezar? En este tutorial te guiaremos paso a paso para **aplicar efecto de sombra en Word** a archivos usando la biblioteca Aspose.Words para Python.  

Si alguna vez jugaste con la interfaz y pensaste, “Debe haber una forma programática de hacerlo”, estás en el lugar correcto. Al final tendrás un script ejecutable que aplica una sombra de bordes suaves a cualquier forma que elijas.

## Requisitos previos

Antes de sumergirte, asegúrate de tener:

- Python 3.8+ instalado (cualquier versión reciente funciona)
- Una licencia activa de Aspose.Words para Python o una prueba gratuita (la API funciona sin licencia pero agrega una marca de agua)
- Un documento de Word (`.docx`) que ya contenga al menos una forma (un rectángulo, imagen o SmartArt)
- Familiaridad básica con importaciones de Python y manejo de excepciones

> **Consejo profesional:** Si aún no tienes una forma, abre Word, inserta un rectángulo simple y guarda el archivo como `input.docx` en una carpeta que puedas referenciar desde tu script.

## Instalar Aspose.Words para Python

Ejecuta el siguiente comando pip en tu terminal:

```bash
pip install aspose-words
```

Eso descarga la última versión 23.x, que soporta propiedades de sombra en nodos `Shape`.

## Paso 1: Cargar el documento de Word

Lo primero que hacemos es abrir el `.docx` existente. Aquí es donde comienza la operación de **añadir sombra a una forma**.

```python
import aspose.words as aw

# Load the source document
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

> **Por qué es importante:** `aw.Document` analiza todo el archivo de Word en una estructura similar a DOM, lo que nos permite recorrer nodos como formas, párrafos y tablas.

## Paso 2: Ubicar la forma objetivo

Aspose.Words ofrece un método de búsqueda profunda `get_child` que puede obtener la primera forma sin importar el nivel de anidamiento. Si tienes varias formas, puedes ajustar el índice o iterar sobre todas ellas.

```python
# Retrieve the first shape (deep search = True)
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape and try again.")
```

> **Caso límite:** Algunos documentos contienen solo objetos de dibujo (p. ej., imágenes). Estos también se representan como nodos `Shape`, por lo que este código funciona tanto para rectángulos como para imágenes.

## Paso 3: Configurar la apariencia de la sombra

Ahora llega el núcleo de **añadir sombra a una forma**—configurar las propiedades de la sombra. Los siguientes valores dan un aspecto sutil y profesional:

```python
# Softness of the shadow edges
shape.shadow_blur = 5.0

# Horizontal and vertical offsets (in points)
shape.shadow_offset_x = 2.0
shape.shadow_offset_y = 2.0

# Transparency – 0 is invisible, 1 is solid
shape.shadow_opacity = 0.7
```

Puedes experimentar con estos números:

- Aumenta `shadow_blur` para un borde más difuso.
- Usa desplazamientos negativos para mover la sombra a la izquierda o hacia arriba.
- Ajusta `shadow_opacity` para que la sombra sea más pronunciada.

> **¿Por qué estos valores predeterminados?** Un desenfoque de 5 puntos imita la sombra predeterminada de Word, mientras que una opacidad de 0.7 mantiene el efecto visible sin abrumar el color de relleno de la forma.

## Paso 4: Guardar el documento modificado

Finalmente, escribe los cambios en un nuevo archivo. Mantener el original intacto facilita la depuración.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Shadow applied! Saved updated file to {output_path}")
```

En este punto has **añadido sombra a una forma** con éxito y puedes abrir `output.docx` para ver el efecto.

## Ejemplo completo y funcional

Juntándolo todo, aquí tienes un script autónomo que puedes copiar y pegar y ejecutar de inmediato:

```python
import aspose.words as aw
import os

def add_shadow_to_first_shape(input_file: str, output_file: str) -> None:
    """
    Loads a Word document, adds a soft shadow to the first shape,
    and saves the result to a new file.

    Parameters
    ----------
    input_file : str
        Path to the source .docx file.
    output_file : str
        Destination path for the modified document.
    """
    # Verify the input exists
    if not os.path.isfile(input_file):
        raise FileNotFoundError(f"Input file not found: {input_file}")

    # Load the document
    doc = aw.Document(input_file)

    # Find the first shape (deep search)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape and retry.")

    # Apply shadow settings
    shape.shadow_blur = 5.0
    shape.shadow_offset_x = 2.0
    shape.shadow_offset_y = 2.0
    shape.shadow_opacity = 0.7

    # Save the updated document
    doc.save(output_file)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
    print("✅ Shadow added successfully.")
```

### Resultado esperado

Abre `output.docx` y deberías ver la forma original ahora con una suave sombra gris, desplazada ligeramente a la derecha y hacia abajo. El efecto refleja lo que obtienes al aplicar manualmente **aplicar efecto de sombra en Word** a través de la interfaz.

![Shadowed shape example](https://example.com/shadowed_shape.png "Forma de Word con una sombra suave"){: .center-image width="600" alt="Captura de pantalla que muestra una forma con sombra en un documento de Word"}

## Aplicar efecto de sombra en Word – Opciones avanzadas

Si necesitas más control, Aspose.Words te permite ajustar propiedades adicionales:

| Property | Descripción | Rango típico |
|----------|-------------|---------------|
| `shadow_color` | El color de la sombra (el predeterminado es negro) | Cualquier `aw.Color` |
| `shadow_type` | Determina si la sombra es **outer**, **inner**, o **perspective** | Enum `aw.ShadowType` |
| `shadow_transform` | Aplica una matriz de transformación personalizada para sombras sesgadas | Avanzado – usar con moderación |

Ejemplo de configuración de una sombra azul:

```python
shape.shadow_color = aw.Color.from_argb(255, 0, 0, 255)  # Opaque blue
shape.shadow_type = aw.ShadowType.OUTER
```

Estas configuraciones te permiten **aplicar efecto de sombra en Word** a documentos de forma creativa, como agregar una sombra de caída coloreada a un logotipo.

## Errores comunes y cómo evitarlos

1. **No se encontró forma** – Si tu documento solo contiene texto, el script lanzará un `ValueError`. Añade una forma primero o extiende el script para iterar sobre todos los nodos `Shape`.
2. **Marca de agua de licencia** – Ejecutar el código sin una licencia adecuada inserta una marca de agua “Aspose.Words Evaluation” en cada página. Obtén una licencia de prueba del portal de Aspose para mantener la salida limpia.
3. **Rutas de archivo incorrectas** – Usar rutas relativas puede causar `FileNotFoundError` cuando el directorio de trabajo del script difiere. Prefiere `os.path.abspath` o pasa rutas absolutas.

## Próximos pasos

Ahora que dominas **añadir sombra a una forma**, quizás quieras explorar temas relacionados:

- **Aplicar efecto de sombra en Word** a múltiples formas en un bucle
- Convertir el documento con sombra a PDF (`doc.save("output.pdf")`)
- Cambiar el color de la sombra según el relleno de la forma (estilizado dinámico)
- Usar Aspose.Words para insertar programáticamente nuevas formas antes de aplicar sombras

Cada una de estas extensiones se basa en los mismos conceptos de la API, por lo que encontrarás la curva de aprendizaje suave.

## Conclusión

Hemos cubierto todo lo que necesitas para **añadir sombra a una forma** en un archivo de Word usando Python: cargar el documento, localizar la forma, configurar los parámetros de sombra y guardar el resultado. El script completo anterior está listo para integrarse en cualquier canal de automatización, y los consejos adicionales te ayudan a **aplicar efecto de sombra en Word** a documentos en escenarios más sofisticados.

Pruébalo, ajusta los valores de desenfoque y opacidad, y observa cómo una pequeña sombra puede marcar una gran diferencia visual. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Tutorial de sombra de forma Aspose.Words – Añadir una sombra a una forma de Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Crear documento Word Java – Añadir forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}