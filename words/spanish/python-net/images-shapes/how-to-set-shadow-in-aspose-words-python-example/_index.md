---
category: general
date: 2026-08-01
description: Cómo aplicar sombra a una forma de Word usando Aspose.Words para Python.
  Aprende a cambiar la opacidad, ajustar el desenfoque y modificar la distancia de
  la sombra rápidamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: es
lastmod: 2026-08-01
og_description: Cómo aplicar sombra a una forma con Aspose.Words para Python. Sigue
  este tutorial paso a paso para cambiar la opacidad, ajustar el desenfoque y modificar
  la distancia de la sombra.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Cómo establecer sombra en Aspose.Words – Guía rápida de Python
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Cómo establecer sombra en Aspose.Words – Ejemplo en Python
url: /es/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer sombra en Aspose.Words – Ejemplo en Python

¿Alguna vez te has preguntado **cómo establecer una sombra** en una forma de Word sin abrir el documento manualmente? No eres el único: muchos desarrolladores se encuentran con este obstáculo al automatizar informes o crear plantillas con una identidad de marca consistente. ¿La buena noticia? Con Aspose.Words para Python puedes ajustar la sombra, opacidad, desenfoque y distancia de una forma en solo unas pocas líneas de código.

En este tutorial recorreremos un ejemplo completo y ejecutable que muestra **cómo establecer sombra**, **cómo cambiar la opacidad**, **cómo ajustar el desenfoque** y también **cambiar la distancia de la sombra**. Al final tendrás una comprensión sólida de **cómo usar Aspose.Words** para dar estilo a las formas de forma programática.

---

![How to set shadow on a shape using Aspose.Words](image-placeholder.png){alt="Cómo establecer sombra en una forma usando Aspose.Words"}

## Requisitos previos

Antes de comenzar, asegúrate de tener:

| Requisito | Motivo |
|-----------|--------|
| Python 3.8+ | Sintaxis moderna, anotaciones de tipo |
| paquete `aspose-words` (pip install aspose-words) | Biblioteca principal para manipular Word |
| Un archivo de muestra `input.docx` con al menos una forma | La forma a la que le aplicaremos la sombra |
| Permiso de escritura en la carpeta donde guardarás `output.docx` | Para persistir los cambios |

No se requieren DLLs adicionales ni interop COM: Aspose.Words es puro Python, por lo que puedes ejecutarlo en Windows, macOS o Linux.

---

## Cómo establecer sombra en una forma con Aspose.Words

A continuación tienes el script **completo**. Carga un documento, encuentra la primera forma (recursivamente), configura la sombra y guarda el resultado. Cada línea está comentada para que comprendas **por qué** está allí, no solo **qué** hace.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Por qué funciona

* **`doc.get_child(..., True)`** – El indicador `True` indica a Aspose.Words que busque **recursivamente**, de modo que incluso las formas dentro de encabezados, pies de página o objetos agrupados sean encontradas. Eso es crucial cuando no sabes exactamente dónde se encuentra la forma.
* **`shadow_format`** – Esta propiedad agrupa todas las configuraciones relacionadas con la sombra. Al establecer `distance`, `blur` y `opacity` controlas la profundidad visual de la forma. Cambiar cualquiera de estos valores demuestra **cómo cambiar la opacidad**, **cómo ajustar el desenfoque** y **cambiar la distancia de la sombra** en una única llamada coherente.
* **Guardado** – `doc.save` escribe un nuevo `.docx`. El original permanece intacto, lo que es una práctica segura para el procesamiento por lotes.

---

## Cómo cambiar la opacidad de la sombra de una forma

La opacidad determina cuán translúcida aparece la sombra. El rango va de 0.0 (completamente invisible) a 1.0 (totalmente sólida). En el código anterior puedes modificar simplemente el argumento `opacity`:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Consejo profesional:** Al generar PDFs más adelante, una mayor opacidad suele traducirse en una sombra más profunda y más imprimible. Experimenta con valores entre 0.4 y 0.9 para encontrar el punto óptimo según tus directrices de marca.

---

## Cómo ajustar el desenfoque para un aspecto más suave

El desenfoque es el radio del desenfoque gaussiano aplicado a los bordes de la sombra. Un número mayor produce un efecto difuso:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

Si necesitas un aspecto nítido de sombra paralela (tipo “Microsoft PowerPoint”), establece `blur` a un valor bajo como `1.0`.

---

## Cambiar la distancia de la sombra para crear profundidad

La distancia se mide en puntos (1 pt = 1/72 in). Alejar más la sombra hace que la forma parezca flotar más alto:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Combina una `distance` mayor con un `blur` moderado para lograr un efecto dramático y “elevado”.

---

## Poniéndolo todo junto – Un mini‑proyecto

Imagina que estás construyendo un generador de informes automatizado que inserta el logotipo de la empresa dentro de un cuadro de texto. Quieres que cada logotipo tenga una sombra sutil que coincida con el estilo corporativo. Usando la función `apply_shadow` puedes:

1. **Crear el documento** (o cargar una plantilla).
2. **Insertar la forma del logotipo** (mediante `DocumentBuilder.insert_image` o `Shape`).
3. **Llamar a `apply_shadow`** con las especificaciones de sombra de tu marca.
4. **Exportar** a DOCX, PDF o HTML con una sola línea de código.

Como la función acepta parámetros, puedes almacenar tus configuraciones de sombra en un archivo JSON y aplicarlas a docenas de documentos—sin necesidad de ajustes manuales.

---

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si el documento tiene varias formas?** | El ejemplo apunta a la *primera* forma. Para afectar a todas, recorre con `doc.get_child_nodes(aw.NodeType.SHAPE, True)` y aplica la misma configuración de `shadow_format` a cada nodo. |
| **¿Puedo establecer un color de sombra diferente?** | Por supuesto. Usa `shape.shadow_format.color = aw.Color(255, 0, 0)` para una sombra roja, o cualquier `aw.Color` que prefieras. |
| **¿Estas configuraciones sobreviven a una conversión a PDF?** | Sí. Aspose.Words conserva las propiedades de sombra al renderizar a PDF, aunque valores de desenfoque muy altos pueden ser aproximados. |
| **¿Hay impacto en el rendimiento para documentos grandes?** | La API de sombra solo toca los objetos de forma, por lo que incluso un informe de 500 páginas se procesa en milisegundos. El cuello de botella suele ser I/O, no la configuración de la sombra. |
| **¿Puedo eliminar la sombra más tarde?** | Establece `shape.shadow_format.is_visible = False` o simplemente restablece las propiedades a sus valores predeterminados. |

---

## Recapitulación del ejemplo completo

Aquí tienes el script completo nuevamente, sin comentarios para copiar y pegar rápidamente:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Ejecuta el script, abre `output.docx` y verás la forma con una sombra elegante que coincide con los parámetros que definiste.

---

## Conclusión

Hemos cubierto **

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales abordan temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Tutorial de Sombra de Forma de Aspose.Words – Añadir una Sombra a una Forma de Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Cómo Implementar Comentarios y Respuestas en Documentos Word usando Aspose.Words para Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [Cómo Gestionar Variables de Documento con Aspose.Words en Python: Guía Completa](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}