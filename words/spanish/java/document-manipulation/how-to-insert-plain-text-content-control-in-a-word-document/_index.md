---
category: general
date: 2026-10-26
description: Aprende a insertar un control de contenido de texto sin formato usando
  Aspose.Words en C#. Guía paso a paso que cubre StructuredDocumentTag, títulos e
  IDs de etiqueta.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: es
lastmod: 2026-10-26
og_description: Inserte un control de contenido de texto sin formato usando Aspose.Words
  en C#. Siga esta guía para agregar títulos, IDs de etiqueta y personalizar la apariencia.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Insertar control de contenido de texto sin formato en Word con C# – guía
  completa
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo insertar un control de contenido de texto sin formato en un documento
  de Word con C#
url: /es/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar control de contenido de texto plano en un documento Word con C#

Si necesita **insertar control de contenido de texto plano** en un archivo Word, este tutorial le muestra exactamente cómo hacerlo usando Aspose.Words para .NET. Ya sea que esté creando un servicio de generación de documentos o automatizando la creación de formularios, los pasos a continuación le permiten agregar una región reutilizable y editable que los usuarios finales pueden completar.

Aprenderá cómo crear un `Document`, usar `DocumentBuilder` para colocar una Structured Document Tag (SDT) de texto plano, establecer un título descriptivo y asignar un identificador de etiqueta único. La guía también explica variaciones comunes —como cambiar la apariencia o anidar controles— para que pueda adaptar la solución a cualquier proyecto.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
- Una licencia válida de Aspose.Words para .NET (o una clave de evaluación gratuita)
- Visual Studio 2022 o cualquier IDE compatible con C#
- Familiaridad básica con la sintaxis de C#

> **Consejo profesional:** Si está usando la evaluación gratuita, recuerde que el documento de salida contendrá una marca de agua. Una versión con licencia la elimina automáticamente.

## Cómo insertar un control de contenido de texto plano usando Aspose.Words

El núcleo de la solución es un proceso de tres pasos:

1. **Crear un `Document` y un `DocumentBuilder`.**  
2. **Insertar una Structured Document Tag (SDT) de texto plano con apariencia predeterminada.**  
3. **Asignar un título y un identificador de etiqueta al SDT.**  

Cada paso se explica a continuación, con código completo y ejecutable.

### Paso 1: Inicializar el documento y el constructor

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo el archivo Word, mientras que `DocumentBuilder` proporciona métodos como `InsertParagraph`, `InsertImage` y, crucialmente para este tutorial, `InsertStructuredDocumentTag`. Inicializarlos primero le brinda un lienzo sobre el cual colocar el **control de contenido de texto plano**.

### Paso 2: Insertar el control de contenido de texto plano (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` indica a Aspose.Words que cree un **control de contenido de texto plano**, que se comporta como un cuadro de texto simple que los usuarios pueden editar. `SdtAppearance.Default` muestra el control con un fondo sutil, haciendo evidente en el documento que la región es editable.

> **¿Por qué usar `SdtAppearance.Default`?**  
> La apariencia predeterminada es el estilo más universalmente compatible en todas las versiones de Word. Si necesita una apariencia sin bordes, puede cambiar a `SdtAppearance.Hidden` más adelante.

### Paso 3: Establecer un título y un identificador de etiqueta

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Título** (`sdt.Title`) aparece en el panel de *Content Controls* de Word, ayudando a los usuarios finales a comprender el propósito del campo.  
- **Etiqueta** (`sdt.Tag`) es un identificador orientado al desarrollador que puede consultar más tarde mediante `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** proporciona texto de guía en gris, mejorando la experiencia del usuario.

El fragmento de código completo anterior forma un programa autónomo que puede compilar y ejecutar. Después de la ejecución, `output.docx` contendrá un único control de contenido de texto plano con el título *MyTag* y la etiqueta *TagId*.

![Diagrama que muestra la inserción de un control de contenido de texto plano en un documento Word](image.png){alt="insertar control de contenido de texto plano"}

## Comprender StructuredDocumentTag (SDT) y sus propiedades

Una **Structured Document Tag** (SDT) es el modelo de objeto subyacente para los controles de contenido de Word. Las propiedades más relevantes para insertar un control de texto plano son:

| Propiedad | Propósito | Valores típicos |
|----------|-----------|-----------------|
| `SdtType` | Determina el tipo de control (texto plano, texto enriquecido, imagen, etc.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Estilo visual del control | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Nombre legible por humanos que se muestra en el panel *Content Controls* | Any short string |
| `Tag` | Identificador legible por máquina usado en el código | Alphanumeric string |
| `PlaceholderName` | Texto que se muestra cuando el control está vacío | Custom hint text |

Cuando establece `SdtType.PlainText`, Word restringe el contenido a caracteres simples, evitando el formato enriquecido. Esto hace que el control sea ideal para campos de formulario simples como *Nombre*, *Correo electrónico* o *Número de teléfono*.

### Variaciones que podría necesitar

| Escenario | Cambio de código |
|----------|------------------|
| **Sin sombreado visual** (sin bordes) | Use `SdtAppearance.Hidden` instead of `Default`. |
| **Campo de solo lectura** | After insertion, set `sdt.LockContentControl = true`. |
| **Pre‑poblar con datos** | Set `sdt.Text = "John Doe";` after creating the tag. |
| **Múltiples controles en una tabla** | Insert the SDT inside a table cell using `builder.InsertCell();` before the `InsertStructuredDocumentTag` call. |

## Errores comunes y cómo evitarlos

1. **Olvidar establecer un título** – Word aún creará el control, pero los usuarios no verán una descripción significativa en el panel *Content Controls*. Siempre asigne `sdt.Title`.  
2. **Usar el `SdtType` incorrecto** – Si necesita texto plano pero elige accidentalmente `RichText`, el control permitirá formato, lo que puede romper el procesamiento posterior. Verifique el valor del enum.  
3. **Guardar en una carpeta de solo lectura** – La llamada `doc.Save` lanzará una `UnauthorizedAccessException`. Asegúrese de que el directorio de destino sea escribible o use `Path.GetTempPath()` para pruebas.  
4. **Licencia no aplicada** – Sin una licencia válida, el documento de salida contiene una marca de agua de evaluación. Aplique la licencia al inicio de su programa:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo, listo para copiar y pegar en un nuevo proyecto de consola.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Salida esperada:** Al abrir `output.docx` en Microsoft Word se muestra una línea de texto *“Please fill in the following field:”* seguida de una región enmarcada en gris claro etiquetada *MyTag*. El marcador de posición *Enter your text here* aparece en gris claro hasta que el usuario escribe.

## Conclusión

Ahora sabe cómo **insertar control de contenido de texto plano** en un documento Word usando Aspose.Words para .NET. El tutorial cubrió la inicialización de un `Document`, la inserción de un `StructuredDocumentTag` de tipo `PlainText` y la personalización de su título, etiqueta y marcador de posición. Al comprender las opciones de `SdtAppearance` y los errores comunes, puede crear con confianza formularios, plantillas e informes automatizados que dependen de controles de contenido editables.

### ¿Qué sigue?

- Explore otros tipos de SDT como `RichText` o `ComboBox` para listas desplegables.  
- Combine varios controles de contenido dentro de tablas o repítalos usando `RepeatingSection`.  
- Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` para leer o modificar los valores de los controles programáticamente.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Cómo crear un control de contenido en C# con Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Crear un nuevo documento Word e insertar control de contenido en C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Agregar contenido usando Document Builder en Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}