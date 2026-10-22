---
category: general
date: 2026-07-19
description: Establezca texto de marcador de posición en un StructuredDocumentTag
  con Aspose.Words. Aprenda cómo agregar control, desplazarse al control y establecer
  el atributo de etiqueta en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- move to control
- how to add control
- how to create sdt
- set tag attribute
language: es
lastmod: 2026-07-19
og_description: Establezca texto de marcador de posición en un StructuredDocumentTag
  usando Aspose.Words. Siga esta guía paso a paso para agregar control, mover al control
  y establecer el atributo de etiqueta.
og_image_alt: Screenshot showing a Word document with placeholder text inside a content
  control created by Aspose.Words
og_title: Establecer texto de marcador de posición en Aspose.Words – Tutorial rápido
  de C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  headline: Set Placeholder Text in Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  name: Set Placeholder Text in Aspose.Words – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6+ (or .NET Framework 4.7.2) – the code works on any recent runtime.
      - Aspose.Words for .NET (NuGet package `Aspose.Words` version 23.12 or later).
      - A basic understanding of C# and Visual Studio (or your favorite IDE).'
  - name: Expected Result
    text: 'Open `SDTExample.docx` in Microsoft Word:'
  - name: What if I need a **dropdown** instead of plain text?
    text: Replace `SdtType.PlainText` with `SdtType.DropDownList` and populate the
      `ListItems` collection. The rest of the workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—remains
      the same.
  - name: Can I **set the tag attribute** after insertion?
    text: 'Absolutely. The `Tag` property can be modified at any time:'
  - name: How do I **find a control later** in a large document?
    text: Use the `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` method
      and filter by `Tag` or `Title`. This is handy when you need to replace placeholder
      text in bulk.
  - name: What if I want the placeholder to appear in **all languages**?
    text: Aspose.Words supports localized placeholder text via the `PlaceholderName`
      property. Set it to a resource string that varies per culture.
  type: HowTo
tags:
- Aspose.Words
- C#
- ContentControl
title: Establecer texto de marcador de posición en Aspose.Words – Guía completa de
  C#
url: /es/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer texto de marcador de posición en Aspose.Words – Guía completa en C#

¿Alguna vez te has preguntado cómo **establecer texto de marcador de posición** dentro de un control de contenido de Word usando Aspose.Words? No eres el único. Ya sea que estés construyendo un motor de generación de documentos o simplemente necesites una plantilla reutilizable, saber cómo agregar un control, moverse al control y establecer el atributo de etiqueta es esencial.

En este tutorial recorreremos un ejemplo del mundo real que muestra exactamente cómo crear un SDT (StructuredDocumentTag), asignarle una etiqueta, establecer texto de marcador de posición y escribir contenido predeterminado, todo en C# puro. Al final tendrás un fragmento listo para ejecutar que puedes insertar en cualquier proyecto .NET.

## Lo que aprenderás

- Cómo **crear SDT** (StructuredDocumentTag) programáticamente.
- La forma correcta de **establecer texto de marcador de posición** para que los usuarios vean indicaciones útiles.
- Usar **move to control** para posicionar el cursor dentro del control recién añadido.
- Asignar un **atributo de etiqueta** para identificación posterior.
- Guardar el documento y verificar el resultado.

### Requisitos previos

- .NET 6+ (o .NET Framework 4.7.2) – el código funciona en cualquier runtime reciente.
- Aspose.Words para .NET (paquete NuGet `Aspose.Words` versión 23.12 o posterior).
- Un conocimiento básico de C# y Visual Studio (o tu IDE favorito).

No se requieren otras bibliotecas externas.

## Paso 1: Inicializar el Documento y el Builder

Primero lo primero: crea un `Document` vacío y un `DocumentBuilder`. El builder es tu pincel; el documento es el lienzo.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Create a brand‑new blank document.
Document document = new Document();

// DocumentBuilder lets us insert text, tables, and controls.
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

> **Por qué es importante:** Comenzar con un `Document` limpio garantiza que el marcador de posición que establezcamos más adelante no entre en conflicto con contenido existente.

## Paso 2: Crear el StructuredDocumentTag (SDT)

Ahora veremos **cómo crear sdt**: un control de contenido que puede contener texto plano, fechas, listas desplegables, etc. En este caso necesitamos un control de texto plano.

```csharp
// Create a plain‑text StructuredDocumentTag (content control).
StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
    document, SdtType.PlainText, true);

// Give the control a friendly name and a tag for later lookup.
plainTextSdt.Title = "CustomerName";
plainTextSdt.Tag   = "CustomerNameTag";

// Here’s the crucial part: set the placeholder text that the user sees.
plainTextSdt.PlaceholderText = "Enter name here";
```

> **Consejo profesional:** La propiedad `PlaceholderText` es lo que el usuario ve antes de escribir cualquier cosa. Es diferente del texto predeterminado que podrías escribir después.

## Paso 3: Insertar el Control en el Documento

Con el SDT listo, necesitamos **cómo agregar control** al documento. El método `InsertNode` hace exactamente eso.

```csharp
// Insert the content control at the current cursor position.
docBuilder.InsertNode(plainTextSdt);
```

> **¿Qué ocurre bajo el capó?** `InsertNode` coloca el SDT como hijo del párrafo actual, preservando cualquier formato circundante.

## Paso 4: Moverse al Control y Escribir Contenido Predeterminado (Opcional)

Si deseas pre‑poblar el control con un valor (por ejemplo, un nombre de cliente predeterminado), primero **move to control** y luego escribe.

```csharp
// Optionally clear the placeholder and write a default name.
plainTextSdt.RemoveAllChildren();          // Remove the placeholder node.
docBuilder.MoveTo(plainTextSdt);           // Move cursor inside the SDT.
docBuilder.Write("John Doe");              // Write default text.
```

> **Por qué eliminamos el marcador de posición:** El marcador de posición es una pista visual, no contenido real del documento. Eliminarlo antes de escribir asegura que el documento final solo contenga el texto real.

## Paso 5: Guardar el Documento

Finalmente, persiste el archivo en disco. También puedes enviarlo como flujo en una respuesta web—simplemente reemplaza la llamada a `Save`.

```csharp
// Save the Word document to the desired location.
document.Save("C:/Temp/SDTExample.docx");
```

### Resultado esperado

Abre `SDTExample.docx` en Microsoft Word:

- Verás un control de contenido de texto plano titulado **CustomerName**.
- El control muestra “Enter name here” como texto de marcador de posición tenue (si no escribiste contenido predeterminado).
- Si mantuviste la línea `Write("John Doe")`, “John Doe” aparece dentro del control y el marcador de posición desaparece.

## Ejemplo completo funcional

A continuación tienes el programa completo, listo para copiar y pegar. Incluye todos los pasos anteriores, más algunas comprobaciones defensivas.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise document and builder.
        Document document = new Document();
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // 2️⃣ Create a plain‑text SDT (content control).
        StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
            document, SdtType.PlainText, true);
        plainTextSdt.Title = "CustomerName";
        plainTextSdt.Tag   = "CustomerNameTag";
        plainTextSdt.PlaceholderText = "Enter name here";

        // 3️⃣ Insert the control into the document.
        docBuilder.InsertNode(plainTextSdt);

        // 4️⃣ (Optional) Move to the control and set default text.
        plainTextSdt.RemoveAllChildren();   // Clear placeholder.
        docBuilder.MoveTo(plainTextSdt);    // Move cursor inside.
        docBuilder.Write("John Doe");       // Write default value.

        // 5️⃣ Save the file.
        string outputPath = @"C:\Temp\SDTExample.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ejecuta el programa, abre el archivo generado y verás todo funcionando exactamente como se describe.

## Preguntas comunes y casos límite

### ¿Qué pasa si necesito un **dropdown** en lugar de texto plano?

Reemplaza `SdtType.PlainText` con `SdtType.DropDownList` y rellena la colección `ListItems`. El resto del flujo—`InsertNode`, `MoveTo`, `SetTagAttribute`—permanece igual.

### ¿Puedo **establecer el atributo de etiqueta** después de la inserción?

Absolutamente. La propiedad `Tag` puede modificarse en cualquier momento:

```csharp
plainTextSdt.Tag = "NewTagValue";
```

Solo recuerda guardar el documento nuevamente para que el cambio persista.

### ¿Cómo **encuentro un control más tarde** en un documento grande?

Utiliza el método `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` y filtra por `Tag` o `Title`. Esto es útil cuando necesitas reemplazar texto de marcador de posición en bloque.

```csharp
foreach (StructuredDocumentTag sdt in document.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    if (sdt.Tag == "CustomerNameTag")
    {
        // Do something with this control.
    }
}
```

### ¿Qué pasa si quiero que el marcador de posición aparezca en **todos los idiomas**?

Aspose.Words admite texto de marcador de posición localizado mediante la propiedad `PlaceholderName`. Asigna una cadena de recursos que varíe según la cultura.

## Consejos y trucos (Pro Tips)

- **Reutiliza el mismo SDT** en varios documentos clonándolo (`plainTextSdt.Clone(true)`), luego inserta el clon donde sea necesario.
- **Evita etiquetas duplicadas**; hacen que la búsqueda posterior sea ambigua. Mantén las etiquetas únicas por documento.
- **Consejo de rendimiento:** Si estás generando miles de documentos, reutiliza una única instancia de `Document` como plantilla y solo reemplaza el texto del marcador de posición. Esto reduce la sobrecarga de creación de objetos.

## Conclusión

Hemos cubierto todo lo que necesitas para **establecer texto de marcador de posición** en un StructuredDocumentTag de Aspose.Words, desde crear el control hasta moverte a él, escribir contenido predeterminado y asignar un atributo de etiqueta. Con este conocimiento puedes crear plantillas de Word dinámicas que guíen a los usuarios, apliquen reglas de ingreso de datos y sean fáciles de mantener.

¿Listo para el próximo desafío? Prueba cambiar el SDT de texto plano por un **selector de fecha** o un **cuadro combinado**, o explora cómo enlazar SDTs a fuentes de datos XML para una automatización de documentos aún más rica.

¡Feliz codificación, y que tus documentos siempre estén perfectamente plantillados!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Establecer estilo de control de contenido](/words/hindi/net/programming-with-sdt/set-content-control-style/)
- [Establecer color de control de contenido](/words/hindi/net/programming-with-sdt/set-content-control-color/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}