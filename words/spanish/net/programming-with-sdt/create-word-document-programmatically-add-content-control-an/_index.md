---
category: general
date: 2026-08-04
description: Crear documento de Word programáticamente usando C#. Aprende cómo agregar
  controles de contenido a Word y establecer texto de marcador de posición para plantillas
  dinámicas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: es
lastmod: 2026-08-04
og_description: Crear documento Word programáticamente con C#. Esta guía muestra cómo
  agregar controles de contenido a Word y establecer texto de marcador de posición
  para plantillas reutilizables.
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: Crear documento Word programáticamente – agregar control de contenido y
  marcador de posición
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Crear documento de Word programáticamente – agregar control de contenido y
  marcador de posición
url: /es/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word programáticamente – agregar control de contenido y marcador de posición

Si necesitas **crear documentos Word programáticamente**, este tutorial te muestra una solución completa, lista para ejecutar. Verás cómo **agregar control de contenido a Word**, darle un título significativo y **establecer texto de marcador de posición en Word** para que los usuarios finales puedan rellenar datos más tarde.

La guía recorre cada línea de código, explica por qué cada paso es importante y destaca los errores comunes. Al final tendrás un archivo .docx reutilizable que puede servir como plantilla para facturas, contratos o cualquier documento basado en formularios.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 (o posterior) instalado – el código usa las últimas características del lenguaje C#.
* Una licencia de Aspose.Words for .NET (la prueba gratuita funciona para desarrollo).
* Visual Studio 2022 o cualquier IDE que pueda compilar proyectos .NET.
* Familiaridad básica con C# y el concepto de Structured Document Tags (SDTs).

> **Consejo profesional:** Si ejecutas el ejemplo sin una licencia, Aspose.Words agrega una pequeña marca de agua al archivo guardado. Aplica tu licencia al inicio del programa para evitarla.

## Paso 1: Configurar el proyecto e importar espacios de nombres

Crea un nuevo proyecto de consola y agrega el paquete NuGet Aspose.Words.

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

Ahora importa los espacios de nombres requeridos en `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Estos espacios de nombres te dan acceso a las clases `Document`, `DocumentBuilder` y `StructuredDocumentTag`, que son esenciales para **crear documentos Word programáticamente**.

## Paso 2: Inicializar un documento en blanco y un builder

La clase `Document` representa todo el archivo .docx, mientras que `DocumentBuilder` te permite colocar contenido en una ubicación específica del cursor.

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Por qué es importante*: Comenzar con un `Document` vacío garantiza que tengas control total sobre cada elemento que insertes. El `DocumentBuilder` mantiene un cursor interno, de modo que puedes insertar nodos exactamente donde los necesites.

## Paso 3: Crear una etiqueta de documento estructurado (SDT) de texto plano

Una Structured Document Tag es el nombre técnico de un **control de contenido** en Word. Crearemos una etiqueta en línea de texto plano que se comporta como un campo de marcador de posición.

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*Por qué es importante*: Usar `StructuredDocumentTagType.PlainText` indica a Word que el control solo aceptará texto plano. `MarkupLevel.Inline` hace que el control se comporte como una palabra regular dentro de un párrafo, lo cual es ideal para campos de formulario.

## Paso 4: Asignar un título y texto de marcador de posición

El **título** es el identificador interno que tu aplicación podrá consultar más tarde. El **marcador de posición** es la pista gris que se muestra al usuario antes de que escriba algo.

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

Aquí **establecemos el texto de marcador de posición en Word** a “Enter name here”. Cuando el documento se abre en Microsoft Word, el marcador de posición aparece en gris claro hasta que el usuario escribe un valor.

## Paso 5: Insertar el control de contenido en la posición actual del cursor

`DocumentBuilder.InsertNode` coloca el SDT exactamente donde está ubicado el cursor del builder. Por defecto, el cursor está al inicio del primer párrafo.

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

Si necesitas el control dentro de un párrafo específico, mueve primero el cursor:

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

Este ejemplo muestra cómo **agregar control de contenido a Word** mientras se preserva el texto circundante.

## Paso 6: Guardar el documento

Finalmente, persiste el archivo en disco. Puedes elegir cualquier carpeta; solo asegúrate de que la aplicación tenga permiso de escritura.

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Cuando abras `SDT.docx` en Microsoft Word, verás el marcador de posición “Enter name here” dentro de un cuadro gris claro. Los usuarios pueden hacer clic en el cuadro y reemplazar la pista con el nombre real del cliente.

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar, pegar y ejecutar sin modificaciones (excepto la ruta de salida).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Salida esperada** – Al ejecutar el programa, la consola muestra la ruta del archivo, y el archivo Word generado contiene una única línea de texto seguida de un marcador de posición gris que dice “Enter name here”.

## Variaciones comunes y casos límite

| Escenario | Cómo adaptar el código |
|----------|-----------------------|
| **Marcador de posición de varias líneas** | Use `StructuredDocumentTagType.RichText` en lugar de `PlainText` y establezca `plainTextTag.MultipleLines = true;`. |
| **Repetir el mismo control** | Clone la etiqueta con `plainTextTag.Clone(true)` e inserte el clon donde sea necesario. |
| **Vincular a la fuente de datos** | Después de que el usuario complete el documento, recupere el valor con `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();`. |
| **Bloquear el control** | Establezca `plainTextTag.LockContentControl = true;` para evitar que los usuarios eliminen el control. |
| **Cambiar el color del marcador de posición** | Word no expone la estilización del marcador de posición a través del SDK; deberás editar la plantilla manualmente o usar una macro de Word. |

Estas variaciones te permiten **agregar control de contenido a Word** en escenarios más complejos, como tablas repetibles o secciones bloqueadas.

## Mejores prácticas y solución de problemas

* **Siempre establece un título** – Sin un título, localizar el control más tarde se vuelve engorroso.
* **Evita marcadores de posición vacíos** – Word oculta un marcador de posición vacío si la propiedad `ShowPlaceholderText` del control es false. Manténla en true para una mejor experiencia de usuario.
* **Valida la ruta de salida** – Si `document.Save` lanza una `UnauthorizedAccessException`, verifica que la carpeta exista y que tu proceso tenga derechos de escritura.
* **Licencia temprana** – Coloca el código de licencia antes de instanciar cualquier objeto de Aspose.Words para evitar la marca de agua de prueba.

## Conclusión

Ahora sabes cómo **crear documentos Word programáticamente**, **agregar control de contenido a Word** y **establecer texto de marcador de posición en Word** usando Aspose.Words para .NET. El ejemplo completo muestra cada paso necesario, desde la inicialización del documento hasta la persistencia de una plantilla que los usuarios finales pueden completar.

A continuación, podrías explorar:

* Añadir **controles de contenido repetibles** para tablas (palabra clave secundaria: add content control to word).
* Poblar los marcadores de posición con datos de una base de datos (palabra clave secundaria: set placeholder text word).
* Convertir el .docx generado a PDF o HTML para procesamiento posterior.

¡Siéntete libre de experimentar con diferentes tipos de etiquetas, estilos y técnicas de enlace de datos! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear nuevo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Crear documento Word con encabezado y pie de página usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Crear un documento Word con tabla usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}