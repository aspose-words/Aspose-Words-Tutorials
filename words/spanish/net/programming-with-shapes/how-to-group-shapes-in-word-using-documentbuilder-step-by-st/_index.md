---
category: general
date: 2026-09-08
description: Aprende a agrupar formas en Word con DocumentBuilder, crear un documento
  Word en blanco e insertar una forma rectangular en solo unas pocas líneas de código
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: es
lastmod: 2026-09-08
og_description: Agrupa formas en Word usando DocumentBuilder. Este tutorial muestra
  cómo crear un documento Word en blanco, insertar una forma rectangular y combinar
  formas en un GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Agrupar formas en Word con DocumentBuilder – ejemplo completo en C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo agrupar formas en Word usando DocumentBuilder – guía paso a paso
url: /es/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Word usando DocumentBuilder – guía paso a paso

Si necesitas **agrupar formas en Word** de forma programática, este tutorial muestra una solución completa en C#. Verás cómo **crear un documento Word en blanco**, usar **DocumentBuilder** y **insertar una forma rectangular** antes de agruparla con una elipse. El resultado es un único `GroupShape` que puedes mover, redimensionar o aplicar estilo como un solo objeto.

Esta guía cubre todo lo que necesitas saber para generar un documento Word con gráficos agrupados usando la biblioteca Aspose.Words for .NET. Al final del artículo tendrás un proyecto ejecutable que produce `GroupedShapes.docx` que contiene un rectángulo y una elipse combinados en una sola forma.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7.2+)
- Paquete NuGet Aspose.Words for .NET (`Aspose.Words`) – versión 23.12 o más reciente
- Un IDE de C# como Visual Studio 2022 o Visual Studio Code
- Familiaridad básica con la sintaxis de C# y la programación orientada a objetos

> **Consejo profesional:** Instala el paquete NuGet desde la línea de comandos para mantener tu proyecto ordenado:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Paso 1: Crear un documento Word en blanco

La primera operación es instanciar un objeto `Document`, que representa un archivo Word vacío, y un `DocumentBuilder` que te permite añadir contenido.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por qué es importante:** `Document` proporciona el contenedor del archivo, mientras que `DocumentBuilder` ofrece una API fluida para insertar texto, imágenes y formas. Sin un `DocumentBuilder` tendrías que manipular manualmente el árbol de nodos del documento, lo que es propenso a errores.

## Paso 2: Insertar una forma rectangular

Un rectángulo es un bloque de construcción común para diagramas. Usa `InsertShape` con `ShapeType.Rectangle` y especifica el ancho y alto en puntos (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Por qué es importante:** Establecer `Left` y `Top` posiciona el rectángulo con precisión en la página, lo cual es esencial cuando luego lo agrupes con otras formas. El método `InsertShape` añade automáticamente la forma al párrafo actual.

## Paso 3: Insertar una forma elíptica

A continuación, agrega una elipse que quedará al lado del rectángulo.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Por qué es importante:** Usar un `ShapeType` diferente demuestra cómo la misma API de `DocumentBuilder` puede crear gráficos variados. Posicionar la elipse de modo que se superponga al rectángulo hace que el efecto de agrupación sea evidente.

## Paso 4: Agrupar las dos formas

Un `GroupShape` actúa como un contenedor. Al añadir el rectángulo y la elipse como hijos, se comportan como un solo objeto.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Por qué es importante:** La propiedad `Bounds` indica a Word dónde se sitúa el grupo en la página. Al añadir las formas hijas, conservas su formato individual mientras habilitas transformaciones colectivas (mover, rotar, redimensionar).

## Paso 5: Guardar el documento

Finalmente, escribe el documento en disco. Puedes cambiar la ruta a cualquier carpeta que prefieras.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Al abrir `GroupedShapes.docx` en Microsoft Word, verás un rectángulo y una elipse agrupados. Seleccionar el grupo resaltará ambas formas, permitiéndote arrastrarlas o redimensionarlas como una única unidad.

### Resultado esperado

- Un archivo Word llamado **GroupedShapes.docx**
- La primera página contiene un **rectángulo** (100 pt × 50 pt) en la posición (50, 50)
- Una **elipse** (80 pt × 80 pt) en la posición (200, 70)
- Ambas formas forman parte de un **GroupShape** con un cuadro delimitador de 300 pt × 200 pt

## Variaciones comunes y casos límite

| Escenario | Ajuste |
|----------|------------|
| **Tamaño de página diferente** | Establece `document.Sections[0].PageSetup.PageWidth` y `PageHeight` antes de insertar las formas. |
| **Más de dos formas** | Crea objetos `Shape` adicionales y llama `groupShape.AppendChild(newShape)` para cada una. |
| **Aplicar color de relleno** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Rotar el grupo** | `groupShape.Rotation = 45;` (grados) |
| **Exportar a PDF** | Después de guardar el DOCX, llama `document.Save("GroupedShapes.pdf");` |

## Código fuente completo (listo para ejecutar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Copia el código en un nuevo proyecto de consola, restaura el paquete NuGet Aspose.Words y ejecútalo. La consola confirmará la ubicación del archivo, y al abrirlo verás los gráficos agrupados.

## Conclusión

Ahora sabes **cómo agrupar formas en Word** con el `DocumentBuilder` de Aspose.Words. El tutorial mostró cómo crear un **documento Word en blanco**, **insertar una forma rectangular**, añadir una elipse y combinarlas en un `GroupShape`. Con esta base puedes crear diagramas más complejos, diagramas de flujo o gráficos personalizados directamente desde C#.

### ¿Qué sigue?

- Explora **cómo usar DocumentBuilder** para tablas, encabezados y pies de página.
- Combina las técnicas de **insertar forma rectangular Word** con cuadros de texto para diagramas anotados.
- Usa **crear documento Word en blanco** como plantilla para la generación automática de informes.

¡Siéntete libre de experimentar con colores, degradados y formas adicionales! ¡Feliz codificación!


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}