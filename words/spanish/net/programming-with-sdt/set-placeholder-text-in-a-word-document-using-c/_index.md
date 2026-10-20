---
category: general
date: 2026-10-20
description: Establezca texto de marcador de posición en un documento de Word usando
  C#. Aprenda a agregar control y establecer el marcador de posición rápidamente con
  Aspose.Words para .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: es
lastmod: 2026-10-20
og_description: Establecer texto de marcador de posición en un documento de Word con
  C#. Este tutorial le muestra cómo agregar control, establecer el marcador de posición
  y generar archivos de Word de forma programática.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Establecer texto de marcador de posición en un documento Word con C# – guía
  paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Establecer texto de marcador de posición en un documento de Word usando C#
url: /es/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer texto de marcador de posición en un documento Word usando C#

Si necesitas **establecer texto de marcador de posición** en un archivo Microsoft Word mientras lo generas con C#, esta guía te muestra exactamente cómo. Verás una solución concisa, de extremo a extremo, que agrega un control de contenido, define su marcador de posición y guarda el documento, todo con Aspose.Words para .NET.

Muchos desarrolladores se preguntan **cómo agregar control** a un documento Word o **cómo establecer marcador de posición** sin abrir Word manualmente. Este tutorial responde a esas preguntas y también muestra una forma limpia de **generar Word C#** archivos que están listos para la entrada del usuario.

## Lo que lograrás

* Crear un documento Word en blanco de forma programática.
* Insertar una etiqueta de documento estructurado (SDT) de texto sin formato, que es el nombre técnico de un control de contenido.
* Asignar un título significativo y texto de marcador de posición al SDT.
* Guardar el archivo `.docx` resultante en disco.

No se requieren herramientas adicionales más allá de la biblioteca Aspose.Words y un entorno de desarrollo .NET 6 (o posterior).

## Requisitos previos

* SDK de .NET 6 o una versión más reciente instalada.  
* Visual Studio 2022 (o cualquier IDE que soporte .NET).  
* Paquete NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`).  

> **Consejo profesional:** Usa la versión de evaluación gratuita de Aspose.Words si solo estás probando; agrega una marca de agua pero funciona igual que la versión con licencia.

## Paso 1: Configurar el proyecto e importar espacios de nombres

Crea un nuevo proyecto de consola y agrega las directivas `using` requeridas. Estas traen las clases principales de Aspose.Words y el espacio de nombres de marcado al alcance.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Por qué este paso es importante:* Importar `Aspose.Words.Markup` te da acceso a `StructuredDocumentTag`, `SdtType` y `MarkupLevel`, los objetos necesarios para **agregar control** y **establecer marcador de posición**.

## Paso 2: Crear un documento en blanco y un DocumentBuilder

Un `Document` representa todo el archivo Word, mientras que un `DocumentBuilder` proporciona un cursor conveniente para insertar elementos.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué este paso es importante:* Comenzar con un documento limpio asegura que el marcador de posición que establezcas aparezca exactamente donde lo deseas, sin interferencia del contenido existente.

## Paso 3: Crear el control de contenido (Etiqueta de Documento Estructurado)

Aquí creamos un SDT de texto sin formato, le asignamos un título y establecemos el texto de marcador de posición que el usuario verá cuando el control esté vacío.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Por qué este paso es importante:* La propiedad `Title` te permite referenciar el control más adelante (p. ej., para enlace de datos). `PlaceholderName` es precisamente el **texto de marcador de posición** que deseas que aparezca, guiando al usuario final.

## Paso 4: Insertar el control en la posición actual del cursor

Usando el `DocumentBuilder`, inserta el SDT en el documento donde el builder está posicionado actualmente.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Por qué este paso es importante:* Insertar el nodo adjunta el control al DOM del documento. Si necesitas agregar varios marcadores de posición, puedes mover el cursor del builder y repetir este paso.

## Paso 5: Guardar el documento

Finalmente, escribe el documento en disco. Reemplaza `YOUR_DIRECTORY` con una ruta real en tu máquina.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Cuando abras `SDT.docx` en Microsoft Word, verás un cuadro de texto en línea con sombreado gris que dice **Enter name here**. Al hacer clic dentro del cuadro se borra el marcador de posición, permitiendo al usuario escribir un nombre de cliente.

### Resultado esperado

| Ubicación del archivo | Vista previa del contenido |
|-----------------------|----------------------------|
| `C:\Temp\SDT.docx` | Marcador de posición en línea **Enter name here** dentro de un control de contenido de texto sin formato titulado *CustomerName*. |

## Casos límite y variaciones

| Situación | Ajuste recomendado |
|-----------|--------------------|
| **Múltiples marcadores de posición** | Crea objetos `StructuredDocumentTag` adicionales con diferentes valores de `Title` y `PlaceholderName`, luego inserta cada uno donde sea necesario. |
| **Marcador de posición de texto enriquecido** | Usa `SdtType.RichText` en lugar de `PlainText` para permitir formato dentro del marcador de posición. |
| **Control a nivel de bloque** | Cambia `MarkupLevel.Inline` a `MarkupLevel.Block` para que el control se comporte como un párrafo completo. |
| **Marcador de posición no visible** | Asegúrate de que la configuración de vista del documento en Word no esté configurada para ocultar los controles de contenido (`File → Options → Advanced → Show content controls`). |
| **Guardar en un stream** | Llama a `doc.Save(stream, SaveFormat.Docx)` si necesitas enviar el archivo por HTTP en lugar de escribirlo en disco. |

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar, pegar y ejecutar. Incluye todos los pasos anteriores en un único método `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Ejecuta el programa, abre el archivo generado y verás el texto de marcador de posición listo para la entrada del usuario.

## Preguntas frecuentes respondidas

**P: ¿Esto funciona con .NET Core?**  
R: Sí. Aspose.Words para .NET es compatible con .NET Core, .NET 5 y .NET 6+. El mismo código se ejecuta sin cambios.

**P: ¿Puedo establecer un valor predeterminado además del marcador de posición?**  
R: Usa `sdt.SetText("Default value")` después de crear el SDT. El marcador de posición desaparece una vez que se establece un valor.

**P: ¿Qué pasa si necesito recuperar el valor ingresado más tarde?**  
R: Carga el documento, localiza el SDT por su `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) y lee `sdt.GetText()`.

## Conclusión

Ahora sabes cómo **establecer texto de marcador de posición** en un documento Word usando C#. Creando un `StructuredDocumentTag` de texto sin formato, asignando un título y marcador de posición, insertándolo con un `DocumentBuilder` y guardando el archivo, puedes **agregar control** y **generar Word C#** archivos programáticamente.  

A partir de aquí podrías explorar:

* Agregar controles de texto enriquecido o listas desplegables (`SdtType.RichText`, `SdtType.DropDownList`).  
* Poblar múltiples marcadores de posición desde una base de datos.  
* Convertir el `.docx` generado a PDF con Aspose.Words.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Establecer texto de marcador de posición en Aspose.Words – Guía completa C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Crear documento Word programáticamente – agregar control de contenido y marcador de posición](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Cómo agregar control de contenido y crear documento Word con Aspose – Completo](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}