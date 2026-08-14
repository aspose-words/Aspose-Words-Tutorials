---
category: general
date: 2026-08-14
description: Cómo agregar SDT rápidamente con Aspose.Words. Aprende a crear un marcador
  de posición de Word e insertar un control de texto plano en un archivo .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: es
lastmod: 2026-08-14
og_description: Cómo agregar SDT en C# usando Aspose.Words. Sigue este tutorial para
  crear un marcador de posición de Word e insertar un control de texto sin formato
  para documentos dinámicos.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Cómo agregar SDT en C# – guía paso a paso de marcadores de posición en Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Cómo agregar SDT en C# – guía completa para marcadores de posición de Word
url: /es/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar SDT en C# – guía completa para marcadores de posición en Word

Si necesitas **how to add sdt** en un archivo Word, este tutorial te muestra los pasos exactos usando Aspose.Words para .NET. Al final de la guía podrás **create word placeholder** etiquetas que permiten a los usuarios finales escribir directamente en un documento, y comprenderás cómo **insert plain text control** de manera fiable.

Trabajar con Structured Document Tags (SDTs) elimina la necesidad de campos de formulario manuales y te brinda una forma limpia y programática de crear contratos, informes o cartas dinámicas. El ejemplo a continuación cubre todo, desde la configuración del proyecto hasta guardar el archivo .docx final, para que puedas copiar y pegar el código en tu propia solución sin perder ninguna dependencia.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
- Visual Studio 2022 o cualquier IDE de C# que prefieras
- Una licencia de Aspose.Words para .NET (una licencia temporal gratuita funciona para pruebas)
- Familiaridad básica con la sintaxis de C# y el concepto de SDTs

> **Consejo profesional:** Si planeas distribuir los documentos generados, incrusta un archivo de licencia para evitar la marca de agua de evaluación.

## Paso 1: Configurar el proyecto e importar Aspose.Words

Crea una nueva aplicación de consola y agrega el paquete NuGet de Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Estas directivas `using` te dan acceso a las clases `Document`, `DocumentBuilder` y `StructuredDocumentTag` que son necesarias para las operaciones de **insert plain text control**.

## Paso 2: Inicializar el documento y el builder

El primer bloque de código crea un documento Word vacío y un `DocumentBuilder` que te permite escribir contenido en él.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funciona como un cursor; cada llamada posterior agrega contenido en la posición actual. Inicializar el documento es la base para cualquier escenario de **how to add sdt** porque el SDT debe pertenecer a una instancia `Document` activa.

## Paso 3: Insertar un Structured Document Tag (SDT) de texto plano

Ahora **insert plain text control** que actúa como un marcador de posición donde un usuario puede escribir un nombre, una fecha o cualquier valor personalizado.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` indica a Aspose.Words que cree un campo de texto simple.
- `SdtAppearanceTags.Default` otorga a la etiqueta el estilo visual estándar de Word (un cuadro sombreado cuando el documento se abre en Word).

## Paso 4: Configurar el SDT con un título y texto de marcador de posición

Un SDT bien nombrado hace que el documento sea autoexplicativo para los usuarios finales. Aquí **create word placeholder** metadatos y establecemos la pista que aparece dentro del campo.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` es el identificador interno que puedes usar más adelante al extraer o actualizar el valor programáticamente.
- `PlaceholderName` es la pista en gris que se muestra en Word, indicando al usuario qué escribir.

## Paso 5: Agregar contenido circundante

Un documento rara vez consiste en un solo SDT. Normalmente necesitas párrafos regulares antes y después del marcador de posición. Usa el método `WriteLine` del builder para agregar texto estático.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

La llamada a `InsertNode` coloca el SDT creado previamente exactamente donde lo necesitas, preservando el flujo de texto circundante.

## Paso 6: Guardar el documento en un archivo .docx

Finalmente, persiste el documento en disco. La ruta puede ser absoluta o relativa a la carpeta del proyecto.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Abrir `SDT.docx` en Microsoft Word muestra un marcador de posición gris que dice **Enter name here**. Los usuarios pueden hacer clic en el campo, escribir un valor, y el documento mantendrá ese valor al guardarlo nuevamente.

## Ejemplo completo y ejecutable

Unir todas las piezas te brinda un programa autónomo que puedes ejecutar al instante:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Salida esperada** al ejecutar el programa:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Al abrir el `SDT.docx` generado se muestra:

```
Dear [Enter name here],
After the SDT
```

El texto entre corchetes es el marcador de posición **insert plain text control** que los usuarios pueden reemplazar.

## Variaciones comunes y casos límite

| Situación | Cómo adaptar el código |
|-----------|-----------------------|
| **Multiple placeholders** | Llama a `InsertStructuredDocumentTag` repetidamente y asigna a cada etiqueta un `Title` único. |
| **Rich‑text SDT** | Usa `StructuredDocumentTagType.RichText` en lugar de `PlainText`. |
| **Lock the placeholder** | Establece `plainTextTag.LockContentControl = true;` para evitar que los usuarios eliminen el campo. |
| **Pre‑populate with a value** | Asigna `plainTextTag.Text = "John Doe";` antes de guardar. |
| **Conditional appearance** | Usa `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` para un control de casilla de verificación. |

Estas variaciones te permiten **create word placeholder** estructuras que se ajustan a casi cualquier escenario tipo formulario.

## Consejos de solución de problemas

- **Placeholder not visible** – Asegúrate de abrir el archivo en Microsoft Word (o un visor compatible). Algunos editores ligeros ocultan los SDT.
- **License warning** – Si ves una marca de agua de evaluación, verifica que tu archivo de licencia se haya cargado correctamente (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Después de insertar un SDT, el cursor del builder permanece *después* de la etiqueta. Si necesitas agregar texto *dentro* de la etiqueta, usa `builder.MoveTo(plainTextTag);` antes de escribir.

## Conclusión

Ahora sabes **how to add sdt** a un documento Word usando Aspose.Words para .NET, cómo **create word placeholder** etiquetas, y cómo **insert plain text control** que los usuarios pueden editar directamente en Word. El ejemplo completo muestra la inicialización, inserción de etiquetas, configuración, contenido circundante y guardado, todo en un solo programa ejecutable.

A continuación, explora temas relacionados como **insert rich text control**, **populate SDTs from a database**, o **convert the final document to PDF**. Todos estos se basan en los mismos fundamentos cubiertos aquí, por lo que puedes ampliar tu canal de automatización con confianza.

¡Feliz codificación, y siéntete libre de experimentar con diferentes tipos de SDT para adaptarlos a tus necesidades de automatización de documentos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cómo crear rangos editables en documentos de solo lectura usando Aspose.Words para Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Agregar marcadores en Word con Aspose.Words para Java – Insertar, actualizar, eliminar](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}