---
category: general
date: 2026-09-05
description: Crea una forma rectangular en un documento de Word usando Aspose.Words,
  luego aprende cómo insertar una elipse y agrupar formas en Word para diseños más
  ricos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: es
lastmod: 2026-09-05
og_description: Crea una forma rectangular en un documento de Word con Aspose.Words,
  luego descubre cómo insertar una elipse y agrupar formas en Word para diseños complejos.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Crear forma rectangular y agrupar formas en Word – Guía de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo crear una forma rectangular y agrupar formas en Word con Aspose.Words
url: /es/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear una forma rectangular y agrupar formas en Word con Aspose.Words

Si necesita **crear una forma rectangular** en un documento Word, esta guía le muestra los pasos exactos con Aspose.Words para .NET. También verá cómo insertar la palabra elipse, agrupar formas en Word y guardar el resultado como un archivo DOCX. La solución funciona en cualquier proyecto .NET 6+ y no requiere que Microsoft Office esté instalado en el servidor.

El tutorial cubre todo, desde la configuración del proyecto hasta el manejo de problemas comunes de diseño, para que pueda copiar el código y ejecutarlo de inmediato.

## Requisitos previos

* SDK de .NET 6 o posterior instalado  
* Un IDE compatible con NuGet (Visual Studio, Rider o VS Code)  
* Una licencia de Aspose.Words para .NET (o una clave de evaluación temporal)  
* Conocimientos básicos de C# y la estructura de documentos Word  

Estos elementos permiten que el código compile y que las formas se rendericen correctamente.

## Paso 1: Configurar el proyecto y agregar Aspose.Words

Cree un nuevo proyecto de consola y agregue el paquete Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

El paquete proporciona las clases `Document`, `DocumentBuilder`, `Shape` y `GroupShape` utilizadas a lo largo de este tutorial.

## Paso 2: Inicializar un documento en blanco y un builder

El objeto `Document` representa todo el archivo Word, mientras que `DocumentBuilder` le permite insertar contenido programáticamente.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Crear el documento primero garantiza que todas las operaciones de forma posteriores tengan un contenedor válido.

## Paso 3: **Crear forma rectangular** y establecer sus dimensiones

Un rectángulo es el contenedor más común para texto o imágenes. Define su tamaño en puntos (1 pt ≈ 1/72 pulgada).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Por qué este paso es importante: la clase `Shape` encapsula la geometría, el relleno y las propiedades de línea. Establecer `Width` y `Height` antes de la inserción garantiza que la forma aparezca con el tamaño esperado.

## Paso 4: **Cómo insertar la palabra elipse** – agregar una forma elíptica

Una elipse puede usarse para íconos, marcadores o elementos decorativos. El código refleja la creación del rectángulo, solo cambia el `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Las propiedades `FillColor` y `Line.Color` ilustran cómo personalizar la apariencia sin imágenes externas.

## Paso 5: **Agrupar formas en Word** – combinar rectángulo y elipse

Agrupar le permite mover, cambiar el tamaño o rotar múltiples formas como una sola unidad. Esto es esencial cuando necesita un gráfico compuesto (p. ej., un ícono etiquetado).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Cuando llama a `AppendChild`, las formas originales se eliminan del flujo principal del documento y se convierten en hijos del `GroupShape`. El grupo se comporta como una sola forma, lo que simplifica los ajustes de diseño posteriores.

## Paso 6: Guardar el documento

Finalmente, escriba el documento en disco. Puede elegir cualquier formato compatible (`.docx`, `.pdf`, `.html`, etc.). Para este tutorial mantenemos el formato nativo de Word.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Después de ejecutar el programa, abra *GroupShape.docx* en Microsoft Word. Verá un rectángulo y una elipse agrupados, posicionados en las coordenadas que especificó.

## Variaciones comunes y casos límite

| Situación | Qué cambiar | Razón |
|-----------|-------------|-------|
| **Unidades de tamaño diferentes** | Use `ConvertUtil.InchToPoint(2.5)` for inches or `ConvertUtil.MillimeterToPoint(30)` for millimetres. | Mantiene el código legible cuando trabaja con medidas que no son puntos. |
| **Agregar texto dentro del rectángulo** | Create a `Paragraph` node, set its `Text` property, and add it to `rectangleShape` via `AppendChild`. | Le permite etiquetar la forma sin cuadros de texto separados. |
| **Rotar el grupo** | Set `groupShape.Rotation = 45;` (degrees). | Útil para crear insignias diagonales o marcas de agua. |
| **Guardar como PDF** | Call `doc.Save("GroupShape.pdf");`. | Aspose.Words rasteriza automáticamente las formas vectoriales para la salida PDF. |
| **Múltiples grupos** | Create additional `GroupShape` instances and repeat the append/insert steps. | Permite diseños de página complejos con varios compuestos independientes. |

### Consejo profesional

Siempre agregue formas **antes** de agruparlas. Si intenta agrupar una forma que ya forma parte de otro grupo, Aspose.Words lanza una `ArgumentException`. Construir el grupo en un solo método evita este error en tiempo de ejecución.

### Precauciones

* **Sistema de coordenadas** – `Left` y `Top` se miden desde los márgenes izquierdo y superior de la página, no desde el borde del documento. Un malentendido puede colocar las formas fuera de la página.
* **Licenciamiento** – Sin una licencia válida, el documento guardado contendrá una marca de agua que dice “Aspose.Words for .NET Evaluation”. Aplique su licencia al inicio del código (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) para evitarlo.

## Código fuente completo (ejecutable)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ejecutar este programa produce *GroupShape.docx* con las formas agrupadas exactamente como se describe.

## Conclusión

Ahora sabe cómo **crear una forma rectangular**, **cómo insertar la palabra elipse** y **agrupar formas en Word** usando Aspose.Words. El ejemplo completo muestra el flujo de trabajo completo—desde la inicialización de un documento hasta guardar el archivo final—para que pueda integrar el manejo de formas en cualquier solución de generación automática de informes o documentos.

### ¿Qué sigue?

* Explore **aspose.words create shapes** para geometrías más complejas como `Polygon` o `Freeform`.  
* Combine formas agrupadas con **content controls** para crear plantillas dinámicas.  
* Convierta el DOCX a PDF o HTML para ver cómo se renderizan las formas vectoriales en diferentes formatos.  

Siéntase libre de experimentar con diferentes tamaños, colores y rotaciones. Cuando domine el agrupamiento de formas, podrá crear diagramas sofisticados, insignias y elementos de UI personalizados directamente dentro de documentos Word.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}