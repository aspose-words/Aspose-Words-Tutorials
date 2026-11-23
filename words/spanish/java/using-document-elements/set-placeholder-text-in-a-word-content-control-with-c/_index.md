---
category: general
date: 2026-11-22
description: Establecer texto de marcador de posición en un control de contenido de
  Word con C#. Aprende cómo crear una etiqueta personalizada, insertar un control
  de texto sin formato y agregar un marcador de posición a la etiqueta usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: es
lastmod: 2026-11-22
og_description: Establezca texto de marcador de posición en un control de contenido
  de Word con C#. Este tutorial le muestra cómo crear una etiqueta personalizada,
  insertar un control de texto sin formato y agregar un marcador de posición a la
  etiqueta para mejorar la interactividad del documento.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Establecer texto de marcador de posición en un control de contenido de Word
  – Guía de C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Establecer texto de marcador de posición en un control de contenido de Word
  con C#
url: /es/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer texto de marcador de posición en un control de contenido de Word con C#

Si necesitas **establecer texto de marcador de posición** en un documento Word de forma programática, esta guía te muestra exactamente cómo hacerlo. Con Aspose.Words para .NET puedes crear una etiqueta personalizada, insertar un control de texto sin formato y añadir un marcador de posición a la etiqueta para que el documento esté listo para la entrada del usuario.

En este tutorial aprenderás cómo **crear una etiqueta personalizada**, **insertar un control de contenido** y **añadir un marcador de posición a la etiqueta** manteniendo el código conciso y listo para producción. No se requieren herramientas externas, solo un proyecto .NET y la biblioteca Aspose.Words.

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado  
* Una licencia válida de Aspose.Words para .NET (o una clave de evaluación gratuita)  
* Familiaridad básica con C# y Visual Studio (o cualquier IDE que prefieras)  

Las siguientes secciones asumen que has creado un proyecto de consola llamado `WordPlaceholderDemo`.

## Paso 1: Instalar Aspose.Words

Agrega el paquete NuGet a tu proyecto:

```bash
dotnet add package Aspose.Words
```

> **Consejo profesional:** Usa la bandera `--version` para bloquear el paquete a la última versión estable (por ejemplo, `Aspose.Words.NET 24.9`).

## Paso 2: Cargar el documento fuente y crear un `DocumentBuilder`

Lo primero que haces es cargar un archivo `.docx` existente (o crear un nuevo documento vacío) e instanciar un `DocumentBuilder`. El builder te brinda una API fluida para insertar controles y texto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Este código **prepara el escenario** para insertar un control de contenido. El `DocumentBuilder` trabaja directamente sobre el objeto `doc`, por lo que cualquier cambio que realices se refleja automáticamente.

## Paso 3: Crear una etiqueta personalizada (StructuredDocumentTag)

Una *etiqueta personalizada* en Word se llama **StructuredDocumentTag (SDT)**. Puedes considerarla como un control de contenido que lleva un identificador único. Crear una es el núcleo del paso **crear etiqueta personalizada**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

El método `InsertStructuredDocumentTag` recibe dos argumentos:

1. El tipo de control (`PlainText` en este caso).  
2. Una cadena que identifica de forma única la etiqueta (`"MyTag"`).  

Al usar una **etiqueta personalizada**, podrás localizar o manipular el control posteriormente de forma programática.

## Paso 4: Establecer un título para accesibilidad

Un título mejora la accesibilidad y facilita la búsqueda del control en la interfaz de Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

La propiedad `Title` es opcional, pero añadirla es una buena práctica cuando **añades un marcador de posición a la etiqueta** para una mejor experiencia del usuario.

## Paso 5: Añadir texto de marcador de posición a la etiqueta

Ahora llega el objetivo principal: **establecer texto de marcador de posición**. Este texto aparece cuando el control está vacío, guiando al usuario sobre qué escribir.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

La propiedad `PlaceholderText` es exactamente lo que necesitas para **añadir un marcador de posición a la etiqueta**. Se comporta como la pista gris que ves en los campos de formulario modernos.

## Paso 6: Guardar el documento modificado

Después de configurar el control, escribe el documento de nuevo en disco.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Al abrir `output.docx` en Microsoft Word, verás un control de contenido de texto sin formato etiquetado como “CustomerName” con el marcador de posición “Enter name…”. Al hacer clic dentro del control, el marcador desaparece, permitiendo al usuario escribir.

### Resultado esperado

* Un archivo Word (`output.docx`) que contiene un único control de contenido de texto sin formato.  
* El control muestra el marcador de posición “Enter name…” hasta que el usuario escribe algo.  
* El identificador de la etiqueta del control es `MyTag`, que puedes consultar más tarde con `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Paso 7: Cómo insertar un control de contenido en otro lugar (avanzado)

Si necesitas **cómo insertar un control de contenido** en una ubicación específica —por ejemplo, después de un párrafo concreto— usa el método `MoveTo` antes de insertar la etiqueta:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Este fragmento demuestra **insertar control de texto sin formato** varias veces dentro del mismo documento.

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| El marcador de posición no se muestra | El control ya contiene texto (incluso un espacio) | Asegúrate de que `sdt.Text` esté vacío antes de establecer `PlaceholderText`. |
| Colisión de identificadores de etiqueta | Reutilizar el mismo nombre de etiqueta (`MyTag`) en el mismo documento | Usa identificadores únicos para cada `StructuredDocumentTag`. |
| Excepción de licencia | Ejecutar sin una licencia válida de Aspose.Words | Aplica un archivo de licencia (`license.SetLicense("Aspose.Words.lic")`) al inicio de `Main`. |
| El documento no se guarda | Olvidar llamar a `doc.Save` o usar una ruta de solo lectura | Verifica que la ruta de salida sea escribible y llama a `doc.Save`. |

## Ejemplo completo

A continuación tienes el programa completo que puedes copiar y pegar en `Program.cs`. Incluye todos los pasos —**crear etiqueta personalizada**, **cómo insertar control de contenido**, **añadir marcador de posición a la etiqueta** y **insertar control de texto sin formato**— en un flujo cohesivo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Ejecuta el programa con `dotnet run`. Tras la ejecución, abre `output.docx` para verificar que ambos controles muestran sus respectivos marcadores de posición.

## Próximos pasos

* **Personalizar apariencia** – Usa `sdt.Font` para cambiar el tamaño, color o estilo de fuente dentro del control.  
* **Vincular a datos XML** – Explora `sdt.XmlMapping` si necesitas que el control se mapee  

## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}