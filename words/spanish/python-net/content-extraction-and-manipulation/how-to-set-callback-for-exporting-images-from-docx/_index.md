---
category: general
date: 2026-06-24
description: Cómo establecer una devolución de llamada para exportar imágenes de DOCX
  al guardar como Markdown. Aprende a extraer imágenes, extraer SVG de Word y guardar
  DOCX como Markdown con manejo personalizado.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: es
og_description: Cómo establecer una devolución de llamada para exportar imágenes de
  DOCX al convertir a Markdown. Esta guía muestra cómo extraer imágenes y SVG de manera
  eficiente.
og_title: Cómo configurar una devolución de llamada para exportar imágenes desde DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Cómo establecer una función de devolución de llamada para exportar imágenes
  de DOCX
url: /es/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer una devolución de llamada para exportar imágenes desde DOCX

¿Alguna vez te has preguntado **cómo establecer una devolución de llamada** para **exportar imágenes desde DOCX** al convertirlo a Markdown? No eres el único. Muchos desarrolladores se topan con el problema de que la conversión predeterminada guarda todas las imágenes en una carpeta genérica o, peor aún, pierde los gráficos SVG por completo.  

En este tutorial recorreremos una solución completa, lista para ejecutar, que responde a la pregunta “cómo establecer una devolución de llamada”, muestra **cómo extraer imágenes** y también cubre **cómo extraer SVG de Word**. Al final podrás **guardar DOCX como Markdown** con un esquema de nombres personalizado para cada recurso de imagen, sin necesidad de ajustes manuales.

## Lo que aprenderás

- Por qué una devolución de llamada es la forma más limpia de controlar los nombres de archivo de las imágenes durante la conversión.  
- Cómo engancharse al `MarkdownSaveOptions.resource_saving_callback` de Aspose.Words.  
- Código paso a paso que extrae **PNG**, **JPG**, **SVG** y cualquier otro recurso incrustado.  
- Consejos para manejar colisiones de nombres, archivos grandes y peculiaridades de rutas multiplataforma.  

> **Consejo profesional:** Si ya utilizas Aspose.Words en una canalización más grande, puedes insertar esta devolución de llamada sin tocar el resto de tu código.

---

![Diagrama de cómo establecer devolución de llamada](https://example.com/images/how-to-set-callback.png "cómo establecer devolución de llamada")

## Requisitos previos

- Python 3.8+ (el ejemplo usa f‑strings, así que 3.6+ es suficiente).  
- Paquete `aspose-words` instalado (`pip install aspose-words`).  
- Un archivo DOCX que contenga imágenes raster **y** gráficos vectoriales (SVG).  
- Familiaridad básica con funciones de Python y E/S de archivos.

Si tienes todo eso, vamos a sumergirnos.

---

## Cómo establecer una devolución de llamada para exportar imágenes desde DOCX

El núcleo de la solución vive en una **devolución de llamada de guardado de recursos**. Aspose.Words llama a este delegado por cada imagen o SVG que desea escribir cuando invocas `document.save`. Al devolver una tupla `(new_name, data)` dictas tanto el nombre de archivo como la carga de bytes.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### ¿Por qué una devolución de llamada?

Sin una devolución de llamada, Aspose.Words crea archivos con nombres como `image1.png`, `image2.svg`, etc., y los coloca en una carpeta junto al archivo Markdown. Esto está bien para demostraciones rápidas, pero en producción a menudo necesitas:

1. **Nombres determinísticos** – útiles para control de versiones o publicación en CDN.  
2. **Evitar colisiones** – dos imágenes con el mismo nombre original no se sobrescribirán.  
3. **Estructuras de carpetas personalizadas** – quizá quieras todos los activos bajo `/assets/docs/`.

La devolución de llamada te brinda control total sobre esas tres preocupaciones.

---

## Exportar imágenes desde DOCX usando una devolución de llamada de recursos

A continuación se muestra la implementación de la devolución de llamada. Calcula un hash del dato binario para producir un sufijo único, conserva la extensión original del archivo y devuelve el nuevo nombre de archivo junto con los bytes crudos.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Manejo de casos límite

- **Archivos grandes:** SHA‑256 funciona bien para cualquier tamaño; el hash se calcula en memoria, así que ten en cuenta las limitaciones de memoria si procesas PDFs enormes.  
- **Extensiones faltantes:** Algunos archivos Word antiguos pueden almacenar imágenes sin una extensión explícita. En ese caso `extension` quedará vacío; puedes usar `.bin` por defecto o inspeccionar los primeros bytes para adivinar el formato.  
- **Recursos no‑imagen:** La devolución de llamada se invoca para cada recurso externo (p. ej., objetos OLE). Si solo te interesan imágenes/SVG, filtra por `resource.type` antes de continuar.

---

## Cómo extraer imágenes y SVG de Word

Ahora conectamos la devolución de llamada al flujo de guardado de Markdown. El objeto `MarkdownSaveOptions` expone la propiedad `resource_saving_callback` precisamente para este propósito.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Configurar `resource_folder` es opcional pero a menudo práctico. Si lo omites, las imágenes terminan al lado del archivo Markdown, lo que puede desordenar la raíz de tu proyecto.

### Guardar el documento

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

Al ejecutar el script, verás una serie de archivos como:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

Y el `output.md` generado contendrá enlaces de imagen que apuntan a esos nombres de archivo exactos:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Eso es la **parte de cómo extraer imágenes** en acción: cada foto, raster o vector, ahora es un activo separado y con nombre único.

---

## Guardar DOCX como Markdown con manejo personalizado de imágenes

Juntándolo todo, aquí tienes el script completo que puedes copiar‑pegar en un archivo llamado `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Por qué funciona:**  
- La `resource_callback` garantiza que cada imagen obtenga un nombre único y reproducible.  
- `resource_folder` mantiene el Markdown ordenado separando los activos.  
- Las llamadas a `os.makedirs` te protegen de errores de “carpeta no encontrada” cuando el script se ejecuta en una máquina nueva.

---

## Extraer SVG de Word – ¿Qué pasa con los gráficos vectoriales?

Los SVG se tratan igual que los PNG en la devolución de llamada porque son simplemente otro `resource`. La única diferencia es que algunas versiones antiguas de Word incrustan SVG como objetos *OfficeArt*, que Aspose.Words convierte automáticamente a PNG raster a menos que habilites explícitamente la bandera **preserve SVG**:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Añade esa línea antes de guardar, y la devolución de llamada recibirá recursos con extensión `.svg`, preservando los datos vectoriales nítidos—perfecto para documentación web responsiva.

---

## Preguntas frecuentes y trucos

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si dos imágenes son idénticas?** | El hash SHA‑256 será idéntico, por lo que los nombres de archivo colisionarán. Si necesitas ambas copias, incluye `resource.name` en el cálculo del hash (p. ej., `hash(resource.name + resource.data)`). |
| **¿Puedo cambiar la carpeta por tipo de archivo?** | Sí. Dentro de `resource_callback` puedes inspeccionar `extension` y devolver una ruta como `f"png/{new_name}"` para imágenes raster y `f"svg/{new_name}"` para vectores. |
| **¿Funciona en Linux/macOS?** | Absolutamente. El código usa `os.path`, que abstrae los separadores de ruta. Solo asegúrate de que el archivo de licencia de Aspose.Words (`aspose.words.lic`) sea accesible si usas una versión de pago. |
| **¿Qué pasa con el uso de memoria en documentos enormes?** | La devolución de llamada recibe el **array de bytes completo** de cada recurso, lo que significa que la imagen completa vive en memoria temporalmente. Para archivos de varios gigabytes podrías querer transmitir los datos a disco dentro de la devolución de llamada en lugar de devolverlos. |

---

## Conclusión

Ahora sabes **cómo establecer una devolución de llamada** para controlar la extracción de imágenes cuando **guardas DOCX como Markdown**. El enfoque te permite **exportar imágenes desde DOCX**, **extraer SVG de Word** y mantener tu Markdown limpio y determinista.  

En un único script autocontenido cubrimos la carga del documento, la definición de una devolución de llamada de guardado de recursos, la configuración de `MarkdownSaveOptions` y el manejo de casos límite como colisiones de nombres y gráficos vectoriales. El resultado es un conjunto de activos con nombres únicos junto a un archivo Markdown perfectamente enlazado—listo para generadores de sitios estáticos, pipelines de documentación o cualquier flujo de trabajo que requiera recursos limpios y reutilizables.

**¿Próximos pasos?**  
- Prueba encadenar esto con un generador de sitios estáticos como MkDocs para publicar automáticamente documentos basados en Word.  
- Experimenta con `markdown_options.export_images_as_base64 = True` si prefieres imágenes en línea en lugar de archivos externos.  
- Profundiza en otras devoluciones de llamada de Aspose.Words (p. ej., `document_saving_callback`) para controlar la salida de Markdown en sí.

¿Tienes más preguntas sobre **cómo extraer imágenes** de otros formatos de Office, o necesitas ayuda para ajustar la devolución de llamada a una convención de nombres específica? Deja un comentario abajo, ¡y feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}