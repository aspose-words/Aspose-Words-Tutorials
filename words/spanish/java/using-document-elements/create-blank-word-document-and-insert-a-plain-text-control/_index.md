---
category: general
date: 2026-09-18
description: Crear un documento Word en blanco usando C# y establecer texto de marcador
  de posición, luego guardar el documento como docx. Aprender a insertar un control
  de texto sin formato y añadir el nombre del marcador de posición.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: es
lastmod: 2026-09-18
og_description: Crear un documento Word en blanco usando C#. Establecer texto de marcador
  de posición, insertar un control de texto sin formato, agregar el nombre del marcador
  de posición y guardar el documento como docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Crear documento Word en blanco con texto de marcador de posición – Guía
  de C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crear documento de Word en blanco e insertar un control de texto sin formato
url: /es/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco e insertar un control de texto sin formato

Si necesitas **crear documento Word en blanco** de forma programática, esta guía te muestra cómo hacerlo con C#. Aprenderás a **insertar control de texto sin formato**, **establecer texto de marcador de posición**, **agregar nombre de marcador de posición**, y finalmente **guardar el documento como docx**. Los pasos son completamente autónomos, por lo que puedes copiar el código en cualquier proyecto .NET y ejecutarlo de inmediato.

Trabajar con archivos Word a menudo requiere un punto de partida limpio: un documento vacío que ya contiene los controles que tus usuarios completarán. Al final de este tutorial tendrás un archivo `.docx` que contiene un control de contenido de texto sin formato con un marcador de posición útil, seguido de contenido normal.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
- Una referencia a la biblioteca **Aspose.Words for .NET** (disponible vía NuGet `Install-Package Aspose.Words`)
- Familiaridad básica con aplicaciones de consola C#
- Permiso de escritura en la carpeta de salida que especifiques en `doc.save(...)`

## Qué construir

El documento final (`SDT.docx`) contiene:

1. Un archivo Word vacío (el **documento Word en blanco** que creaste)
2. Un control de contenido de texto sin formato (el paso **insertar control de texto sin formato**)
3. Texto de marcador de posición que aparece dentro del control hasta que el usuario escribe algo (el paso **establecer texto de marcador de posición**)
4. Un nombre de marcador de posición que puede usarse para acceso programático más adelante (el paso **agregar nombre de marcador de posición**)
5. Una línea de texto normal después del control, demostrando que el contenido normal puede seguir

## Paso 1: Crear un documento Word en blanco

La primera operación es instanciar un objeto `Document` vacío. Este objeto representa un **documento Word en blanco** completamente nuevo en memoria.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Por qué es importante:* Un `Document` vacío te brinda control total sobre cada elemento que añades, asegurando que no haya estilos o secciones ocultas que interfieran con el control de contenido que insertarás más adelante.

## Paso 2: Inicializar un DocumentBuilder

`DocumentBuilder` es la clase auxiliar que te permite escribir en el `Document`. Rastrea la posición actual del cursor y proporciona métodos para insertar todo tipo de objetos Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué es importante:* Usar un `DocumentBuilder` simplifica el proceso de agregar un **control de texto sin formato** porque el constructor conoce el punto exacto de inserción.

## Paso 3: Insertar control de texto sin formato

Ahora añadimos un **control de contenido de texto sin formato** (también conocido como Structured Document Tag, o SDT). El tipo de control `StructuredDocumentTagType.PLAIN_TEXT` indica a Word que trate el contenido como texto plano, no como formato enriquecido.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Por qué es importante:* El método `InsertStructuredDocumentTag` crea el control y devuelve una referencia (`sdt`) que puedes configurar más, como agregar texto de marcador de posición o un nombre personalizado.

## Paso 4: Establecer texto de marcador de posición y agregar nombre de marcador de posición

El texto de marcador de posición brinda a los usuarios una pista visual sobre qué escribir. El paso **agregar nombre de marcador de posición** asigna un identificador programático que puedes consultar más tarde con `doc.GetChildNodes` o APIs similares.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Por qué es importante:* `SetPlaceholderName` controla el texto de sugerencia gris que se muestra dentro del control de contenido. Configurar `Tag` (la acción **agregar nombre de marcador de posición**) te permite localizar el control en el árbol del documento sin escanear todo el archivo.

## Paso 5: Agregar contenido regular después del control

Para demostrar que el documento continúa normalmente después del control, escribimos una línea simple de texto.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Paso 6: Guardar documento como docx

Finalmente, persistimos el documento en memoria al disco. Esta es la operación **guardar documento como docx** que produce el archivo que puedes abrir en Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Por qué es importante:* Usar el formato `.docx` garantiza la máxima compatibilidad con versiones modernas de Word, Google Docs y otras herramientas compatibles con Office.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar en un proyecto de consola. Reemplaza `YOUR_DIRECTORY` con una ruta de carpeta real en tu máquina.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Resultado esperado

- Al abrir `SDT.docx` en Word se muestra una caja gris vacía con el texto **Enter text…** dentro.
- La caja es un control de contenido de texto sin formato; puedes escribir directamente en ella.
- Debajo de la caja, la línea **After the tag.** aparece como texto de párrafo normal.

Si el marcador de posición no aparece, verifica que estés usando una versión reciente de Aspose.Words (v23.1 o posterior) y que el documento se abra en una versión de Word que soporte controles de contenido (Word 2007+).

## Variaciones comunes y casos límite

| Escenario | Cómo adaptar el código |
|----------|-----------------------|
| **Múltiples marcadores de posición** | Llama a `InsertStructuredDocumentTag` nuevamente con un ID de etiqueta diferente y un nombre de marcador de posición. |
| **Control de texto enriquecido** | Usa `StructuredDocumentTagType.RichText` en lugar de `PlainText`. |
| **Establecer texto predeterminado** | Después de la inserción, asigna `sdt.Text = "Default value";` – este texto reemplaza el marcador de posición cuando se carga el documento. |
| **Guardar en un flujo** | Reemplaza `doc.Save(outputPath);` con `doc.Save(stream, SaveFormat.Docx);` para enviar el archivo por HTTP. |
| **Cambiar color del marcador de posición** | Usa `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (requiere `using System.Drawing`). |

## Consejos profesionales

- **Reutilizar el ID de etiqueta**: Mantener la etiqueta (`MyTag`) consistente en todos los documentos te permite automatizar la población de datos más adelante con `doc.Range.Replace` o la `StructuredDocumentTagCollection`.
- **Evitar rutas codificadas**: Usa `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` para una ubicación de salida portátil.
- **Rendimiento**: Si necesitas generar miles de documentos, crea una única plantilla `Document` con el SDT ya presente, luego clónala con `doc.Clone()` para cada iteración.

## Conclusión

Ahora sabes cómo **crear documento Word en blanco**, **insertar control de texto sin formato**, **establecer texto de marcador de posición**, **agregar nombre de marcador de posición**, y **guardar el documento como docx** usando Aspose.Words for .NET. Este patrón constituye la base para crear plantillas Word con formularios completados, informes automatizados, o cualquier solución que requiera marcadores de posición editables por el usuario.

Siéntete libre de experimentar con otros tipos de controles, combinar múltiples marcadores de posición, o integrar este código en una API web que devuelva el archivo `.docx` generado directamente a los solicitantes. Para el siguiente paso, explora **poblar un control de contenido con datos programáticamente** o **convertir el archivo Word generado a PDF** usando las funciones de conversión integradas de Aspose.Words. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar campo de formulario de entrada de texto en documento Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Crear un documento Word con tabla usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Crear documento Word con encabezado y pie de página usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}