---
category: general
date: 2026-09-08
description: Crear una forma rectangular en un documento de Word con C#. Aprende a
  establecer el tamaño de la forma, agrupar varias formas y crear un documento de
  Word en blanco de forma programática.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: es
lastmod: 2026-09-08
og_description: Crear una forma rectangular en un documento de Word con C#. Esta guía
  muestra cómo establecer el tamaño de la forma, agrupar múltiples formas y crear
  un documento de Word en blanco de forma programática.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Crear forma rectangular y agrupar formas en Word usando C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Crear forma rectangular y agrupar formas en Word usando C#
url: /es/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular y agrupar formas en Word usando C#

Si necesitas **create rectangle shape** dentro de un archivo Word, este tutorial te brinda una solución completa y lista‑para‑ejecutar. Verás cómo set shape size, group multiple shapes y crear un documento Word en blanco desde cero, todo con la biblioteca Aspose.Words for .NET.

Trabajar con documentos Word de forma programática a menudo se siente como manejar muchos pequeños detalles. Al final de esta guía tendrás un único método que genera un archivo `.docx` que contiene un rectángulo y una elipse agrupados, listo para edición o impresión adicional.

## Requisitos previos

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
* Una copia con licencia de **Aspose.Words for .NET** (puedes usar una clave de evaluación gratuita)
* Un IDE como Visual Studio 2022 o Visual Studio Code
* Familiaridad básica con la sintaxis de C#

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Paso 1: Crear un documento Word en blanco

El primer paso es crear un documento vacío que alojará las formas. Esto cumple con el requisito de *create blank word document*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Crear un documento en blanco te brinda un lienzo limpio. El objeto `Document` representa todo el archivo `.docx`, y su `FirstSection.Body.FirstParagraph` es el punto de inserción predeterminado para nuevos nodos.

## Paso 2: Crear forma rectangular

Ahora puedes añadir el rectángulo. Aquí es donde ocurre la operación **create rectangle shape**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Establecer las dimensiones directamente responde a la palabra clave **set shape size**. Todos los valores de tamaño se expresan en puntos, lo que brinda un control preciso sobre cómo aparece la forma en el documento final.

## Paso 3: Crear una forma adicional (elipse)

Un caso de uso típico es combinar varias formas. Aquí añadimos una elipse que más adelante compartirá el mismo contenedor.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Ambas formas siguen siendo independientes en este punto. El siguiente paso muestra cómo **group multiple shapes** juntas.

## Paso 4: Agrupar formas en Word

Agrupar formas te permite mover, redimensionar o formatearlas como una sola unidad. Esto cumple con los requisitos **group shapes in word** y **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

La propiedad `GroupShape.Bounds` determina el sistema de coordenadas para las formas hijas. Al colocar el rectángulo y la elipse dentro del mismo `GroupShape`, podrás moverlos o rotarlos juntos con una única llamada.

## Paso 5: Guardar el documento

Finalmente, escribe el documento en disco. El archivo contendrá las formas agrupadas que acabas de crear.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Después de ejecutar el programa, abre `GroupedShapes.docx` en Microsoft Word. Deberías ver un rectángulo y una elipse agrupados; al seleccionar una forma también se selecciona la otra, confirmando que el agrupamiento tuvo éxito.

## Código fuente completo

Copia el siguiente programa completo en un nuevo proyecto de consola y ejecútalo. No se requiere código adicional.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Resultado esperado

Ejecutar el programa genera `GroupedShapes.docx`. Al abrir el archivo en Word se muestra:

* Un **rectangle** (100 pt × 50 pt) con un borde azul y relleno gris‑claro.
* Una **ellipse** (80 pt × 80 pt) con un borde verde‑oscuro y relleno amarillo‑claro.
* Ambas formas están dentro de un solo grupo, por lo que mover una mueve la otra.

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo añadir más de dos formas al grupo?** | Sí. Crea objetos `Shape` adicionales y llama a `group.AppendChild(yourShape)` para cada uno. |
| **¿Qué pasa si necesito rotar el grupo?** | Establece `group.RotationAngle = 45;` (grados). Todas las formas hijas rotan juntas. |
| **¿Es posible agrupar formas después de guardar el documento?** | Debes modificar la estructura del documento antes de guardarlo; de lo contrario tendrías que cargar el archivo, localizar las formas y recrear el grupo. |
| **¿Necesito disponer de algún objeto?** | Aspose.Words gestiona sus propios recursos, pero deberías disponer de los objetos `FileStream` si abres flujos manualmente. |
| **¿El código funcionará con formato .doc (binario)?** | Sí, cambia `doc.Save("output.doc")`. El comportamiento de agrupamiento es idéntico. |

## Conclusión

Ahora sabes cómo **create rectangle shape**, **set shape size** y **group multiple shapes** dentro de un archivo Word usando C#. Este enfoque te permite crear programáticamente diagramas complejos, marcas de agua o informes basados en plantillas sin edición manual.

### Próximos pasos

* Explora **group shapes in word** más a fondo añadiendo cuadros de texto o imágenes al mismo grupo.
* Utiliza el patrón `SetShapeSize` para calcular dinámicamente las dimensiones basadas en el diseño de la página.
* Combina esta técnica con campos de combinación de correspondencia para generar documentos personalizados a gran escala.

¡Siéntete libre de experimentar con diferentes tipos de formas, colores y transformaciones de grupo. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}