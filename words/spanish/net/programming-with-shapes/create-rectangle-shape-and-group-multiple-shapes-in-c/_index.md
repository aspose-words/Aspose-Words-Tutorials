---
category: general
date: 2026-09-18
description: Crear forma rectangular en un documento de Word usando C#. Aprende cómo
  agregar múltiples formas, agregar formas a un grupo e insertar un grupo de formas
  con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: es
lastmod: 2026-09-18
og_description: Crear una forma rectangular en un archivo de Word con C#. Esta guía
  muestra cómo agregar múltiples formas, añadir formas a un grupo e insertar una forma
  de grupo usando Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Crear forma de rectángulo y agrupar formas en C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Crear forma de rectángulo y agrupar múltiples formas en C#
url: /es/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular y agrupar múltiples formas en C#

Si necesita **crear forma rectangular** en un documento de Word, este tutorial muestra una solución completa. Verá cómo **agregar múltiples formas**, **agregar formas a un grupo** y **insertar forma de grupo** usando la API Aspose.Words para .NET.

Trabajar con formas es un requisito común al generar informes, contratos o materiales de marketing de forma programática. Al final de esta guía tendrá una aplicación de consola C# ejecutable que produce un archivo `.docx` que contiene un rectángulo, una elipse y un grupo que contiene ambas formas.

Los únicos requisitos previos son un SDK de .NET reciente (6.0 o posterior) y una copia con licencia de Aspose.Words para .NET. No se requieren herramientas adicionales.

## Requisitos previos

- .NET 6.0 SDK o más reciente  
- Aspose.Words para .NET (paquete NuGet `Aspose.Words`)  
- Familiaridad básica con la sintaxis de C#  

Puede instalar el paquete con el siguiente comando:

```bash
dotnet add package Aspose.Words
```

## Paso 1: Crear forma rectangular con Aspose.Words

El primer paso es crear un objeto `Shape` de tipo `Rectangle`. Este objeto representa el rectángulo visual que aparecerá en el documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Por qué es importante:** `ShapeType.Rectangle` indica a Aspose.Words que renderice un rectángulo geométrico. Establecer `Width` y `Height` define su tamaño en puntos (1 punto = 1/72 de pulgada). Añadir colores de relleno y trazo hace que la forma sea visible sin necesidad de estilos adicionales.

## Paso 2: Agregar múltiples formas al documento

Después del rectángulo, puede crear cualquier número de formas adicionales. En este ejemplo agregamos una elipse para demostrar cómo funciona **agregar múltiples formas**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Por qué es importante:** Cada llamada a `new Shape` crea un objeto de dibujo independiente. Al insertarlos secuencialmente, construye una colección de formas que luego pueden agruparse o posicionarse individualmente.

## Paso 3: Agregar formas al grupo

Agrupar formas simplifica la gestión del diseño porque el grupo se comporta como un solo nodo. Este paso muestra cómo **agregar formas al grupo** usando `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Por qué es importante:** `GroupShape` actúa como un contenedor. Cuando mueve, rota o cambia el tamaño del grupo, todas las formas hijas siguen automáticamente. El cuadro delimitador (200 × 200 puntos) define el espacio de coordenadas para las formas hijas.

## Paso 4: Insertar forma de grupo en el documento

Ahora que el grupo contiene el rectángulo y la elipse, necesita **insertar forma de grupo** en la ubicación deseada. El builder ya colocó el grupo vacío, pero también puede insertarlo en otro lugar si es necesario.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Por qué es importante:** Ajustar `Left` y `Top` mueve todo el grupo dentro de la página. Guardar el documento escribe la jerarquía de formas en un archivo `.docx` que puede abrirse en Microsoft Word, LibreOffice o cualquier visor compatible.

## Ejemplo completo ejecutable

A continuación se muestra el programa completo que combina todos los pasos. Copie el código en un nuevo proyecto de consola y ejecútelo para generar `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Salida esperada:**  
Al abrir `GroupShapeExample.docx` se muestra un único grupo que contiene un rectángulo azul claro y una elipse coral claro, ambos posicionados dentro de un contenedor de 200 × 200 puntos. El grupo puede seleccionarse como un solo objeto en Word, confirmando que **agregar formas al grupo** se realizó con éxito.

## Variaciones comunes y casos límite

| Situación | Ajuste recomendado |
|-----------|--------------------|
| Diferentes tipos de forma (p.ej., `ShapeType.Line`) | Crear la forma con el `ShapeType` deseado y establecer su geometría en consecuencia. |
| Necesidad de rotar una forma | Usar `shape.Rotation = 45;` (grados) antes de agregarla al grupo. |
| Documentos grandes con muchos grupos | Reutilizar una única instancia de `DocumentBuilder`; evitar crear un nuevo builder para cada grupo para reducir el uso de memoria. |
| Guardar como PDF en lugar de DOCX | Llamar a `doc.Save("output.pdf", SaveFormat.Pdf);` después de insertar el grupo. |

**Consejo profesional:** Siempre establezca valores explícitos de `Left` y `Top` para el grupo cuando necesite una colocación precisa. Si los omite, el grupo hereda la posición actual del cursor del builder, lo que puede generar resultados de diseño inesperados.

## Conclusión

Ahora sabe cómo **crear forma rectangular**, **agregar múltiples formas**, **agregar formas al grupo** y **insertar forma de grupo** en un documento de Word usando C#. El ejemplo completo demuestra el flujo de trabajo completo, desde la creación del documento hasta guardar el archivo final.  

A continuación, explore temas relacionados como **posicionar formas respecto al texto**, **aplicar ajuste de texto** y **exportar formas agrupadas a PDF**. Estas extensiones le permiten crear diseños de documentos sofisticados y programáticos con Aspose.Words.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear documento Word en blanco con forma rectangular con sombra – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}