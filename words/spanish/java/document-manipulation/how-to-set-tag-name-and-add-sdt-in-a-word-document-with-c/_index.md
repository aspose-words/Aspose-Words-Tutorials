---
category: general
date: 2026-09-08
description: Establezca el nombre de la etiqueta y cree un control de contenido (SDT)
  en un documento de Word usando C#. Aprenda a añadir un SDT, escribir texto en la
  etiqueta y modificar el documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: es
lastmod: 2026-09-08
og_description: Establece el nombre de la etiqueta y crea un control de contenido
  (SDT) en un documento de Word usando C#. Sigue esta guía paso a paso para agregar
  el SDT, escribir texto en la etiqueta y modificar el documento.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Establecer el nombre de la etiqueta y agregar SDT en un documento Word –
  Guía de C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo establecer el nombre de la etiqueta y agregar SDT en un documento Word
  con C#
url: /es/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer el nombre de etiqueta y agregar SDT en un documento Word con C#

Si necesitas **establecer el nombre de etiqueta** para un StructuredDocumentTag (SDT) mientras trabajas con archivos Word, esta guía te muestra exactamente cómo hacerlo. Verás un ejemplo completo y ejecutable que **crea un control de contenido**, escribe texto en la etiqueta y **modifica el documento Word** de principio a fin.

Los desarrolladores a menudo preguntan: *“¿cómo agregar sdt* a un .docx existente y luego *escribir texto en la etiqueta*?” – la respuesta está en usar la API Aspose.Words para .NET. Al final de este tutorial podrás abrir un archivo Word, insertar un SDT de texto plano, establecer su nombre de etiqueta, rellenarlo con contenido y guardar los cambios sin dejar recursos colgantes.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior instalado.
* Una licencia válida de Aspose.Words para .NET (o puedes trabajar con la versión de evaluación).
* Visual Studio 2022 (o cualquier IDE que soporte C#).
* Un documento Word de entrada (`input.docx`) ubicado en una carpeta a la que puedas referenciar desde el código.

## Paso 1: Configurar el proyecto e importar espacios de nombres

Crea un nuevo proyecto de Aplicación de Consola y agrega el paquete NuGet Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Luego, añade las directivas `using` necesarias al inicio de `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Estos espacios de nombres te dan acceso a `Document`, `DocumentBuilder` y a la clase `StructuredDocumentTag`, que son esenciales para **modificar un documento Word**.

## Paso 2: Cargar el documento Word existente

La primera operación es cargar el archivo que deseas editar. Este paso es necesario para cualquier escenario en el que **modifiques el contenido de un documento Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Por qué cargamos el documento primero** – El objeto `Document` representa todo el paquete .docx en memoria. Sólo después de cargarlo puedes insertar de forma segura nuevos nodos, como un SDT.

## Paso 3: Insertar un StructuredDocumentTag (SDT) y establecer su nombre de etiqueta

Ahora respondemos la pregunta central: **cómo agregar sdt** y **establecer el nombre de etiqueta**. Usamos `DocumentBuilder.InsertStructuredDocumentTag` con `SdtType.PlainText`. El segundo argumento es el nombre de la etiqueta, que luego podrás referenciar programáticamente o mediante la UI de Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Explicación** – `InsertStructuredDocumentTag` devuelve una instancia de `StructuredDocumentTag`. Al pasar `"MyTag"` **establecemos el nombre de etiqueta** directamente en el momento de la creación. Si necesitas cambiarlo después, puedes asignar un nuevo valor a `sdt.Tag`.

## Paso 4: Escribir texto en la etiqueta recién creada

Una vez que el SDT existe, normalmente querrás **escribir texto en la etiqueta** para que los usuarios finales vean contenido de marcador de posición o predeterminado. El método `SetText` hace exactamente eso.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Por qué usar SetText** – Asignar directamente a la propiedad `Text` reemplazaría toda la jerarquía del nodo. `SetText` actualiza de forma segura el texto interno del control de contenido mientras preserva su estructura.

## Paso 5: Guardar el documento modificado

Finalmente, persiste los cambios en un nuevo archivo. Esto completa el flujo de trabajo **modificar documento Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Al abrir `output.docx` en Microsoft Word, verás un control de contenido de texto plano etiquetado **MyTag** que contiene el texto “Sample content”. El control puede editarse manualmente y el nombre de la etiqueta sigue siendo accesible mediante las herramientas de desarrollo de Word.

## Código fuente completo

A continuación tienes el programa completo y autocontenido. Cópialo en `Program.cs` y ejecútalo; no se requieren fragmentos adicionales.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Salida esperada en la consola

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Cómo se ve el archivo Word resultante

![Word document showing a content control named MyTag with the text “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Ejemplo de establecer el nombre de etiqueta en un documento Word"}

*La captura de pantalla ilustra el SDT con el **nombre de etiqueta** establecido en *MyTag* y el texto incrustado visible.*

## Variaciones comunes y casos límite

| Situación | Cómo manejarlo |
|-----------|----------------|
| **Crear un SDT de texto enriquecido** | Usa `SdtType.RichText` en lugar de `PlainText`. |
| **Establecer un nombre de etiqueta diferente después de la inserción** | `sdt.Tag = "NewTag";` – puedes reasignar el nombre de la etiqueta en cualquier momento. |
| **Agregar el SDT dentro de un párrafo específico** | Mueve el cursor del builder (`builder.MoveToParagraph(index)`) antes de llamar a `InsertStructuredDocumentTag`. |
| **Múltiples SDT en el mismo documento** | Repite los pasos 3‑4 para cada control; cada uno puede tener un nombre de etiqueta único. |
| **Trabajar con documentos protegidos** | Asegúrate de que el documento esté sin protección (`doc.Unprotect()`) antes de insertar un SDT. |

## Consejos profesionales para una automatización robusta de Word

* **Licenciar temprano** – Llama `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` al inicio de `Main` para evitar marcas de agua de evaluación.
* **Liberar objetos** – Envuelve `Document` en un bloque `using` si apuntas a .NET Framework para garantizar que se liberen los manejadores de archivo.
* **Validar la existencia de la etiqueta** – Cuando leas un documento más tarde, usa `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` para localizar etiquetas por la propiedad `Tag`.
* **Rendimiento** – Para documentos grandes, carga solo las secciones necesarias usando `LoadOptions` con `LoadFormat.Docx` y `LoadFormat.Auto`.  

## Conclusión

Ahora sabes cómo **establecer el nombre de etiqueta**, **crear un control de contenido**, **escribir texto en la etiqueta** y **modificar un documento Word** usando C#. El ejemplo completo muestra el patrón estándar para **cómo agregar sdt** y persistir los cambios de forma segura.  

A partir de aquí


## ¿Qué deberías aprender a continuación?


Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Agregar contenido usando Document Builder en Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/)
- [Documento Word - Cómo eliminar contenido](/words/english/net/remove-content/)
- [Crear documento Word con Aspose.Words – Guía paso a paso](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}