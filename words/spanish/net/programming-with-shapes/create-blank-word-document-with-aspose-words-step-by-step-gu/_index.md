---
category: general
date: 2026-02-23
description: Crea un documento de Word en blanco usando C# y Aspose.Words. Aprende
  a agregar una forma rectangular, añadir sombra a la palabra y guardar el documento
  de Word con la forma en minutos.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: es
og_description: Crear rápidamente un documento de Word en blanco. Esta guía muestra
  cómo agregar una forma de rectángulo, añadir sombra a la palabra y guardar el documento
  de Word con la forma usando Aspose.Words.
og_title: Crear documento de Word en blanco – Tutorial completo de C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear documento de Word en blanco con Aspose.Words – Guía paso a paso
url: /es/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word en blanco – Tutorial completo de C#

¿Alguna vez te has preguntado cómo **crear documento de Word en blanco** programáticamente sin abrir Microsoft Word? No estás solo. En muchos proyectos de automatización necesitamos un archivo .docx nuevo, colocar una forma en él, darle una buena sombra y luego **guardar Word con forma** para usarlo más tarde.  

En esta guía recorreremos exactamente eso: partir de un documento vacío, **agregar una forma rectangular**, configurar un efecto de **add shadow word**, y finalmente persistir el archivo. Al final tendrás un fragmento completo y ejecutable que puedes pegar en cualquier aplicación de consola .NET. Sin misterios, sin piezas faltantes.

## Lo que necesitarás

- **Aspose.Words for .NET** (cualquier versión reciente, por ejemplo, 24.10).  
- .NET 6 o posterior (el código también funciona con .NET Framework 4.7+).  
- Un IDE básico de C#—Visual Studio, Rider o incluso VS Code con la extensión C#.  

Eso es todo. No se requieren paquetes NuGet adicionales más allá de Aspose.Words, y no se necesita instalación de Word.

---

## Paso 1: Crear un documento de Word en blanco

Lo primero que haces cuando quieres **crear documento de Word en blanco** es instanciar la clase `Document`. Piensa en ella como un lienzo limpio que Aspose.Words te entrega.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Por qué es importante:** El objeto `Document` contiene todas las secciones, párrafos y formas. Comenzar con una instancia vacía garantiza que controles cada elemento que se añada después.

---

## Paso 2: Agregar una forma rectangular al documento

Ahora que tenemos un documento limpio, vamos a **agregar forma rectangular**. Un rectángulo es una simple `Shape` con `ShapeType.Rectangle`. Por supuesto puedes elegir otros tipos, pero un rectángulo funciona muy bien para la demostración.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Consejo:** Si alguna vez te preguntas **cómo agregar forma** que no sea un rectángulo, simplemente cambia `ShapeType.Rectangle` por cualquier otro valor del enum, como `ShapeType.Ellipse` o `ShapeType.Polygon`. El resto del código permanece igual.

---

## Paso 3: Configurar una sombra personalizada para la forma

Un rectángulo simple se ve un poco aburrido, así que **agregaremos add shadow word** para que destaque. Aspose.Words expone un objeto `ShadowFormat` con muchas propiedades.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Por qué es importante:** La sombra brinda una sutil sensación de profundidad, especialmente cuando el documento se visualiza en pantalla. Ajusta `OffsetX`, `OffsetY` y `BlurRadius` según el lenguaje de diseño que prefieras.

---

## Paso 4: Insertar la forma en el documento

Con la forma lista, necesitamos colocarla en algún lugar. El punto más sencillo es el primer párrafo de la primera sección. Si el documento aún no tiene párrafos, Aspose crea uno automáticamente.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Caso límite:** Si planeas insertar la forma en una ubicación específica (por ejemplo, después de un encabezado concreto), localiza el `Paragraph` objetivo mediante `document.GetChildNodes(NodeType.Paragraph, true)` y usa `InsertAfter` o `InsertBefore` según corresponda.

---

## Paso 5: Guardar el documento de Word con la forma

Finalmente, **guardamos Word con forma** en disco. El método `Save` determina automáticamente el formato a partir de la extensión del archivo.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **Lo que verás:** Abre `shadowedRectangle.docx` en Word (o cualquier visor compatible) y observarás un rectángulo gris con una sombra suave ubicado en la parte superior de la primera página.

---

## Ejemplo completo funcionando

A continuación tienes el programa completo que puedes copiar‑pegar en una aplicación de consola. Incluye todas las directivas `using`, comentarios y los pasos exactos que discutimos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Ejecuta el programa, navega a `YOUR_DIRECTORY` y abre el `shadow.docx` generado. Deberías ver el rectángulo con una sombra gris sutil—exactamente lo que nos propusimos lograr.

---

## Preguntas frecuentes y consejos

### ¿Cómo cambio el color de la forma?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Simplemente establece `FillColor` antes de añadir la forma.

### ¿Qué pasa si necesito varias formas en la misma página?
Crea objetos `Shape` adicionales y añádelos al mismo párrafo o a párrafos diferentes. También puedes controlar el diseño usando `WrapType` y `RelativeHorizontalPosition`.

### ¿Puedo exportar a PDF manteniendo la sombra?
Absolutamente. Usa `document.Save("output.pdf")`—Aspose.Words conserva el efecto de sombra en la conversión a PDF.

### ¿Esto funciona en .NET Core?
Sí. Aspose.Words es multiplataforma; el mismo código se ejecuta en .NET Core, .NET 5+ y .NET Framework.

### ¿Cómo agregar una forma sin un párrafo?
Puedes añadir la forma directamente a un `Run` o a un `Story`. Para una posición más precisa, establece `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` y ajusta las propiedades `Left`/`Top`.

---

## Resultado visual

![Rectangle shape with gray shadow in a Word document – add shadow word example](https://example.com/placeholder-image.png "add shadow word example")

*El texto alternativo de la imagen incluye la palabra clave secundaria **add shadow word** para satisfacer SEO.*

---

## Conclusión

Acabamos de demostrar cómo **crear documento de Word en blanco**, **agregar forma rectangular**, aplicar un efecto de **add shadow word**, y finalmente **guardar Word con forma** usando Aspose.Words for .NET. El proceso es sencillo: instanciar un `Document`, construir una `Shape`, ajustar su `ShadowFormat`, insertarla y llamar a `Save`.  

Desde aquí puedes experimentar—prueba diferentes tipos de forma, juega con colores o superpone varias formas. Si necesitas combinar este documento con contenido existente, simplemente carga el archivo existente mediante `new Document("existing.docx")` y sigue los mismos pasos.  

¿Tienes más preguntas? Deja un comentario, ¡y feliz codificación!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}