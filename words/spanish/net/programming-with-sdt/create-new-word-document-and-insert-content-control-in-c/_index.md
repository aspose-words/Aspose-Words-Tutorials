---
category: general
date: 2026-10-13
description: Crear un nuevo documento de Word en C# e insertar un control de contenido
  con texto de marcador de posición. Aprende cómo establecer el texto del marcador
  de posición y guardar el documento de Word de manera eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: es
lastmod: 2026-10-13
og_description: Crear un nuevo documento de Word en C# con Aspose.Words, insertar
  un control de contenido, establecer texto de marcador de posición y guardar el documento
  de Word, todo en una sola guía.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Crear un nuevo documento de Word e insertar un control de contenido en C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Crear un nuevo documento de Word e insertar un control de contenido en C#
url: /es/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un nuevo documento Word e insertar control de contenido en C#

Si necesitas **crear un nuevo documento Word** de forma programática, esta guía te muestra cómo hacerlo con Aspose.Words para .NET. Aprenderás a **insertar un control de contenido**, asignar **texto de marcador de posición**, y finalmente **guardar el documento Word C#** con código que puedes copiar en tu proyecto.

El tutorial recorre cada paso, explica por qué cada llamada a la API es importante y cubre variaciones comunes como agregar un SDT de texto enriquecido o manejar documentos existentes. Al final tendrás un ejemplo completo y ejecutable que podrás adaptar a facturas, contratos o cualquier salida de Word basada en plantillas.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
* Paquete NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`)
* Un IDE como Visual Studio 2022 o Visual Studio Code

No se requieren bibliotecas adicionales.

## Crear un nuevo documento Word con Aspose.Words

El primer paso es instanciar un objeto `Document`. Este objeto representa un archivo Word vacío en memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` te brinda una API fluida para insertar elementos en la posición actual del cursor. Como el documento está vacío, el cursor comienza al inicio de la primera (y única) sección.

## Insertar control de contenido (StructuredDocumentTag)

Un **control de contenido** en Word se llama Structured Document Tag (SDT). El siguiente código crea un SDT de texto plano, establece su título y define el texto de marcador de posición que aparece cuando el usuario abre el archivo.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Por qué es importante:**  
* `SdtType.PlainText` restringe el contenido a una sola línea de texto plano, lo que es ideal para campos simples como un nombre o correo electrónico.  
* Establecer `PlaceholderName` proporciona una pista visual (`Enter name here`) que guía al usuario final.  

Si necesitas un campo más rico (p. ej., texto multilínea o un selector de fecha), reemplaza `SdtType.PlainText` por `SdtType.RichText` o `SdtType.Date`.

## Agregar texto opcional alrededor

La mayoría de las plantillas incluyen una etiqueta antes del control de contenido. Puedes añadirla con la misma instancia de `DocumentBuilder`:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

El archivo Word resultante muestra:

```
Customer Name: [Enter name here]
```

## Guardar documento Word al estilo C#

Finalmente, escribe el documento en disco. Aspose.Words determina automáticamente el formato a partir de la extensión del archivo.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Al abrir `output.docx` en Microsoft Word, verás el texto de marcador de posición dentro de un control de contenido sombreado en gris. Los usuarios pueden hacer clic en el control y reemplazar el marcador con su propio valor.

## Ejemplo completo y ejecutable

A continuación tienes un programa de consola autocontenido que reúne todo. Copia el código en un nuevo proyecto de consola y ejecútalo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Salida esperada** (consola):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Abrir `output.docx` muestra una sola línea con la etiqueta *Customer Name:* seguida de un control de contenido que muestra *Enter name here*.

## Variaciones comunes y casos límite

| Escenario | Cambio de código | Motivo |
|----------|------------------|--------|
| **Campo de texto enriquecido** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Permite entrada multilínea y formato básico. |
| **Control de solo lectura** | `sdt.LockContentControl = true;` | Impide que los usuarios editen el contenido del control. |
| **Poblar con datos** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Inserta un valor predeterminado que sobrescribe el marcador. |
| **Agregar a un documento existente** | Cargar con `new Document("template.docx")` en lugar de un `Document` vacío | Habilita escenarios de plantillas donde el control se coloca en un diseño predefinido. |
| **Múltiples controles** | Repetir el bloque de creación con diferentes títulos y marcadores | Útil para formularios que recopilan varias piezas de información. |

### Consejo profesional

Al generar documentos grandes, reutiliza una única instancia de `DocumentBuilder` en lugar de crear una nueva para cada control. Esto reduce la sobrecarga de memoria y mejora el rendimiento.

## Probar el resultado

1. Ejecuta la aplicación de consola.  
2. Abre `output.docx` en Microsoft Word.  
3. Verifica que el texto de marcador de posición aparezca dentro de un cuadro sombreado en gris.  
4. Haz clic en el cuadro, escribe un nombre y guarda el archivo. El texto ingresado reemplaza el marcador.

Si el marcador no aparece, confirma que estás usando Aspose.Words versión 23.9 o posterior, ya que versiones anteriores tenían un error con `PlaceholderName` en SDT de texto plano.

## Conclusión

Ahora sabes cómo **crear un nuevo documento Word**, **insertar un control de contenido**, **establecer texto de marcador de posición** y **guardar el documento Word C#** usando Aspose.Words. El ejemplo completo muestra el patrón estándar, y la tabla de variaciones indica cómo adaptar la solución a escenarios más avanzados.

A continuación, podrías explorar:

* **Insertar control de contenido para fechas** – usa la enumeración `SdtType.Date`.  
* **Poblar una plantilla con datos** – combina `StructuredDocumentTag` con campos de combinación de correspondencia.  
* **Exportar a PDF** – llama a `doc.Save("output.pdf")` después de agregar los controles.

¡Siéntete libre de experimentar con diferentes tipos de SDT, configuraciones de bloqueo y estilos para que coincidan con los requisitos de tu proyecto! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}