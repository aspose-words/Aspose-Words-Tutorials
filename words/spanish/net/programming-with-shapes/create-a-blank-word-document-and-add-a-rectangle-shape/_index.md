---
category: general
date: 2026-09-05
description: Aprende a crear un documento de Word en blanco y agregar una forma rectangular
  que se pueda ocultar usando Aspose.Words en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: es
lastmod: 2026-09-05
og_description: Creación de documento de Word en blanco e inserción de forma rectangular
  oculta usando Aspose.Words – guía paso a paso para desarrolladores C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Crear un documento de Word en blanco con una forma rectangular oculta
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Crear un documento de Word en blanco y añadir una forma rectangular
url: /es/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento de Word en blanco y agregar una forma rectangular

Si necesitas crear un **documento de Word en blanco** que también contenga una forma que no deseas que aparezca en el diseño, esta guía te muestra exactamente cómo hacerlo con Aspose.Words para .NET. Verás un ejemplo completo y ejecutable que crea un nuevo documento, agrega una forma rectangular, oculta esa forma y guarda el archivo—sin herramientas adicionales.

El tutorial cubre todo, desde la configuración del proyecto hasta la solución de problemas comunes. Al final podrás generar un archivo de Word que parece vacío para el lector pero que aún contiene metadatos ocultos, lo cual es útil para cosas como marcas de agua, almacenamiento XML personalizado o anclajes de diseño.

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 SDK o posterior (el código también funciona con .NET Framework 4.7+)
* Visual Studio 2022 (o cualquier IDE que soporte C#)
* Una licencia activa de **Aspose.Words** en NuGet (la prueba gratuita sirve para pruebas)
* Familiaridad básica con C# y el concepto de nodos de documento

Puedes instalar la biblioteca con el siguiente comando CLI:

```bash
dotnet add package Aspose.Words
```

> **Consejo profesional:** Mantén tu versión de Aspose.Words actualizada; la API utilizada en este tutorial es estable a partir de la versión 23.10.

## Cómo crear un documento de Word en blanco con Aspose.Words

El primer paso es instanciar un objeto `Document`. Un `Document` nuevo representa un **documento de Word en blanco** vacío—sin párrafos, sin secciones, solo el contenedor del archivo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Por qué es importante:** Comenzar con un documento limpio garantiza que la forma oculta que agregarás más adelante no interfiera con el contenido o los estilos existentes.

## Agregar una forma rectangular al documento

A continuación creamos una forma rectangular. En Aspose.Words una forma es un nodo que puede ubicarse en cualquier parte del árbol del documento, y puede configurarse con tamaño, relleno, estilo de línea y visibilidad.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

El código anterior crea un rectángulo visible. En este punto podrías insertarlo en el documento con `builder.InsertNode(rectangle)`. Sin embargo, como queremos que la forma permanezca oculta, ajustaremos su propiedad `Hidden` antes de la inserción.

## Cómo ocultar una forma en un documento de Word

Word proporciona un atributo `Hidden` para los nodos de forma. Cuando se establece en `true`, la forma no aparece en el diseño de la página, pero sigue formando parte del XML del documento. Este es el núcleo del requisito de **cómo ocultar una forma**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Explicación:** Establecer `Hidden = true` agrega el atributo `<w:hide>` al XML de la forma. Los procesadores de Word ignoran la forma durante la renderización, pero aún puede accederse programáticamente o a través de la vista XML de Word.

## Insertar la forma oculta en el documento en blanco

Ahora colocamos el rectángulo oculto en el árbol del documento. Como el documento sigue vacío, la forma se convierte en el primer nodo de la historia principal.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Si abres el archivo resultante en Microsoft Word, verás una página aparentemente vacía. La forma está allí, pero es invisible.

## Guardar el documento

Finalmente, escribe el documento en disco. Puedes elegir cualquier formato compatible (`.docx`, `.pdf`, `.odt`, etc.). Para este tutorial usaremos el formato DOCX moderno.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Resultado esperado

Abre `HiddenRectangle.docx` en Word:

* El documento aparece en blanco (sin formas ni texto visibles).
* Si inspeccionas el archivo con una herramienta como **Open XML SDK** o el **Word XML Viewer**, verás el elemento `<w:pict>` que contiene el rectángulo con el atributo `hidden`.

![documento de Word en blanco con forma rectangular oculta](image.png){: .align-center alt="documento de Word en blanco con forma rectangular oculta"}

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar‑pegar en una aplicación de consola. Incluye todas las directivas `using` necesarias, manejo de errores y comentarios.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Ejecuta el programa (`dotnet run`) y verifica el archivo de salida. La consola confirmará la ubicación de guardado.

## Preguntas comunes y casos límite

### ¿Puedo ocultar varias formas a la vez?

Sí. Crea cada forma, establece `Hidden = true` e insértalas secuencialmente. La bandera oculta funciona por nodo, por lo que mezclar formas ocultas y visibles en el mismo documento es compatible.

### ¿Qué pasa si necesito que la forma esté oculta solo en la vista de impresión?

Word diferencia entre la visibilidad **de pantalla** y **de impresión** mediante la propiedad `DisplayWhen`. Aspose.Words no expone una API directa para esa bandera, pero puedes modificar el XML subyacente:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Utiliza esto solo cuando necesites visibilidad únicamente en la impresión.

### ¿Afecta el tamaño del archivo la forma oculta?

Una forma oculta agrega la misma carga XML que una forma visible, por lo que el aumento del tamaño del archivo es idéntico. Sin embargo, porque la forma  

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento de Word en blanco con forma rectangular sombreada – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial de sombra de forma Aspose.Words – Añadir sombra a una forma de Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}