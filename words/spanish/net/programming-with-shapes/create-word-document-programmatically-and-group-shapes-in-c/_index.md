---
category: general
date: 2026-08-10
description: Crear documento de Word programáticamente usando Aspose.Words, aprender
  cómo agrupar múltiples formas en Word, añadir un rectángulo a Word y crear una forma
  agrupada en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: es
lastmod: 2026-08-10
og_description: Crea documentos Word programáticamente con Aspose.Words. Esta guía
  muestra cómo agrupar múltiples formas en Word, añadir un rectángulo a Word e incrustar
  un control de contenido de texto sin formato, todo en C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Crear documento Word programáticamente – agrupar formas en C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Crear documento Word programáticamente y agrupar formas en C#
url: /es/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word programáticamente y agrupar formas en C#

Si necesitas **crear documento Word programáticamente**, este tutorial te muestra cómo construir un archivo DOCX con Aspose.Words y **agrupar múltiples formas en Word**. También cubriremos **añadir rectángulo a Word** y **cómo crear una forma grupal** que contenga tanto un rectángulo como una elipse, más un StructuredDocumentTag de texto plano para la entrada del usuario.

Terminarás con un archivo Word listo para usar que contiene una forma grupal de rectángulo‑elipse y un control de contenido donde el usuario puede escribir un nombre. No se requiere edición manual en Word después de ejecutar el código.

## Lo que necesitarás

- .NET 6.0 o posterior (el ejemplo está dirigido a .NET 6, pero cualquier versión reciente de .NET funciona)
- Una licencia de Aspose.Words para .NET (la prueba gratuita sirve para pruebas)
- Visual Studio 2022 o cualquier IDE de C# que prefieras
- Familiaridad básica con la sintaxis de C#

## Crear documento Word programáticamente – flujo de trabajo general

El proceso consta de tres fases lógicas:

1. **Inicializar** un `Document` y un `DocumentBuilder` – la base para cualquier archivo Word que generes.
2. **Construir una forma grupal** que contenga un rectángulo y una elipse – demuestra **agrupar múltiples formas en Word** y **cómo crear una forma grupal**.
3. **Insertar un StructuredDocumentTag (SDT)** – un control de contenido de texto plano que permite a los usuarios finales rellenar datos, ilustrando **añadir rectángulo a Word** como parte del diseño general del documento.

A continuación se muestra el código completo y ejecutable, seguido de una explicación paso a paso.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Paso 1 – Inicializar el documento y el builder
El objeto `Document` representa todo el archivo DOCX, mientras que `DocumentBuilder` proporciona una API conveniente para añadir contenido. Inicializarlos es el primer requisito siempre que **crees documento Word programáticamente**.

> **Consejo profesional:** Si planeas reutilizar el mismo documento en múltiples operaciones, mantén una única instancia de `DocumentBuilder` para evitar la creación innecesaria de objetos.

### Paso 2 – Crear un contenedor de forma grupal
Un `Shape` con `ShapeType.Group` actúa como un lienzo que puede contener otras formas. Establecer `Width` y `Height` define el cuadro delimitador del grupo. Este es el núcleo de **cómo crear una forma grupal** en Aspose.Words.

> **Caso límite:** Si el ancho del grupo es menor que la suma de los anchos de sus hijos, los hijos se recortarán. Siempre haz el grupo lo suficientemente grande para contener cada forma hija.

### Paso 3 – Añadir un rectángulo a Word
Se crea un rectángulo con `ShapeType.Rectangle`. Sus propiedades `Left` y `Top` lo posicionan respecto al origen del grupo. Este paso demuestra **añadir rectángulo a Word** y muestra cómo puedes controlar la ubicación exacta.

> **Error común:** Olvidar establecer `Left`/`Top` hace que el rectángulo aparezca en el origen predeterminado del grupo (0,0), lo que puede solaparse con otros hijos.

### Paso 4 – Añadir una elipse (círculo) al grupo
Una elipse se añade de la misma forma que el rectángulo, pero con `ShapeType.Ellipse`. `Left = 210` la desplaza a la derecha del rectángulo, creando un par de formas visualmente distintas dentro del mismo grupo.

> **¿Por qué usar un grupo?** Agrupar permite mover, rotar o cambiar el tamaño de ambas formas juntas con una sola operación más adelante, preservando su disposición relativa.

### Paso 5 – Insertar la forma grupal completada en el documento
`builder.InsertNode(groupShape)` coloca todo el grupo en la posición actual del cursor. Como el grupo ya contiene sus hijos, no necesitas llamadas de inserción adicionales para el rectángulo o la elipse.

### Paso 6 – Crear un StructuredDocumentTag (SDT) de texto plano
Un StructuredDocumentTag es un control de contenido que los usuarios finales pueden rellenar cuando el documento se abre en Word. Establecer `Title = "CustomerName"` le da al control un identificador significativo, útil para la extracción de datos posterior.

> **¿Por qué un SDT de texto plano?** Restringe la entrada a texto sin formato, evitando formateos accidentales que podrían romper el procesamiento posterior.

### Paso 7 – Guardar el documento
`doc.Save("GroupAndSDT.docx")` escribe el archivo en disco. El DOCX resultante contiene las formas agrupadas y el SDT. Al abrir el archivo en Microsoft Word verás un rectángulo junto a un círculo, ambos seleccionables como un solo objeto, seguido de un marcador de posición “Enter name here …”.

#### Resultado esperado
- Un archivo llamado **GroupAndSDT.docx** en la carpeta de ejecución.
- En Word: una forma grupal (rectángulo + elipse) que puedes mover como una unidad.
- Directamente bajo el grupo, un control de contenido sombreado en gris que invita al usuario a escribir un nombre.

## Variaciones adicionales y buenas prácticas

### Uso de diferentes tipos de forma
Puedes reemplazar `ShapeType.Rectangle` o `ShapeType.Ellipse` por cualquier otro `ShapeType` (p. ej., `ShapeType.Polygon`, `ShapeType.Line`). La lógica de agrupación sigue siendo idéntica.

### Establecer color de relleno y bordes
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Añadir relleno y trazo mejora la distinción visual, especialmente cuando el documento se comparte con partes interesadas no técnicas.

### Rotar todo el grupo
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Rotar el grupo es más eficiente que rotar cada hijo individualmente.

### Exportar a PDF
Si necesitas una versión PDF, simplemente llama:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Todas las formas agrupadas y el SDT (renderizado como un campo de texto) aparecerán en el PDF.

## Problemas comunes y cómo evitarlos

| Síntoma | Causa | Solución |
|---------|-------|----------|
|         |       |          |

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}