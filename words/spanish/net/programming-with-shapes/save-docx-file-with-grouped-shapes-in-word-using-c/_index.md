---
category: general
date: 2026-08-04
description: Guardar archivo docx programáticamente mientras se agrega una forma rectangular
  y se agrupan formas en Word. Aprende a establecer las dimensiones de la forma y
  a crear un cuadro de texto programáticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: es
lastmod: 2026-08-04
og_description: Guardar archivo docx usando C# añadiendo una forma rectangular, agrupando
  formas en Word, estableciendo dimensiones de la forma y creando un cuadro de texto
  programáticamente.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Guardar archivo docx con formas agrupadas en Word – Guía paso a paso en
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Guardar archivo docx con formas agrupadas en Word usando C#
url: /es/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Guardar archivo docx con formas agrupadas en Word usando C#

Si necesitas **guardar archivo docx** que contiene varias formas organizadas juntas, esta guía te muestra cómo hacerlo con C#. Aprenderás cómo **agregar forma rectangular**, agrupar múltiples formas en un documento Word, **establecer dimensiones de la forma** y **crear cuadro de texto programáticamente**. La solución funciona con la última versión de Aspose.Words para .NET y se ejecuta en .NET 6 o posterior.

El tutorial recorre cada paso, desde la configuración del proyecto hasta la llamada final `doc.Save`. Al final tendrás un fragmento de código reutilizable que puedes pegar en cualquier proyecto de consola o ASP.NET. No se requieren scripts externos ni edición manual del archivo DOCX.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6 (o más reciente) instalado.
* Una licencia válida para **Aspose.Words for .NET** (la versión de prueba gratuita funciona para pruebas).
* Visual Studio 2022, VS Code o cualquier IDE que pueda compilar proyectos .NET.

El código usa solo el espacio de nombres Aspose.Words, por lo que no se necesitan paquetes NuGet adicionales.

## Guardar archivo docx con formas agrupadas en Word

El núcleo de la solución consiste en crear un `GroupShape` que contiene un rectángulo y un cuadro de texto, luego insertar el grupo en el documento y llamar a `doc.Save`. Las siguientes secciones dividen el proceso en partes manejables.

### 1. Crear un nuevo documento y un builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué este paso es importante* – Un objeto `Document` nuevo representa un archivo *.docx* vacío. `DocumentBuilder` proporciona métodos de alto nivel como `InsertNode`, que utilizaremos para colocar la forma de grupo.

### 2. Agregar forma rectangular a un grupo

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Por qué este paso es importante* – La operación **add rectangle shape** muestra cómo definir un elemento visual con tamaño y posición exactos. El rectángulo vive dentro de `group`, por lo que mover el grupo más tarde mueve el rectángulo automáticamente.

### 3. Agrupar formas en un documento Word

La clase `GroupShape` agrupa varios objetos de dibujo. Agrupar es útil cuando deseas tratar varios objetos como una sola unidad (p. ej., mover, rotar o copiar juntos).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Por qué agrupamos* – Agrupar reduce la complejidad del diseño. En lugar de posicionar cada forma individualmente en la página, ajustas `Left`, `Top`, `Width` y `Height` del grupo una sola vez.

### 4. Establecer dimensiones de la forma para un diseño preciso

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Por qué establecemos dimensiones* – Una medida precisa asegura que el rectángulo y el cuadro de texto no se superpongan inadvertidamente y que el **save docx file** final coincida con el diseño previsto.

### 5. Crear cuadro de texto programáticamente dentro del grupo

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Por qué este paso es importante* – El segmento **create textbox programmatically** muestra cómo incrustar texto enriquecido dentro de una forma. Usar un `Paragraph` y `Run` te brinda control total sobre el formato más adelante.

### 6. Insertar forma de grupo y **guardar archivo docx**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Por qué este paso final es importante* – La llamada `InsertNode` coloca las formas agrupadas exactamente donde se encuentra el cursor del builder. El método `doc.Save` realiza la operación **save docx file**, escribiendo un documento Word con todas sus funciones en el disco.

> **Resultado:** Al abrir *GroupShape.docx* en Microsoft Word se muestra un rectángulo a la izquierda y un cuadro de texto a la derecha, ambos bloqueados juntos dentro de un único grupo. Puedes mover el grupo como una unidad, cambiar su tamaño o aplicar formato adicional.

## Ejemplo completo y ejecutable

Copia el código a continuación en un nuevo proyecto de consola (`dotnet new console`) y ejecuta `dotnet run`. El programa crea `GroupShape.docx` en la carpeta de salida del proyecto.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Resultado esperado

* Aparece un archivo llamado **GroupShape.docx** en el directorio de salida.
* Al abrir el archivo se muestra una forma rectangular a la izquierda y un cuadro de texto que contiene “Grouped text” a la derecha, ambos bloqueados juntos.
* Seleccionar cualquiera de las formas mueve todo el grupo, confirmando que la funcionalidad **group shapes word** funciona como se espera.

## Variaciones comunes y casos límite

| Situación | Recomendación |
|-----------|----------------|
| Necesitas más de dos formas | Append additional `Shape` objects to `group` before calling `builder.InsertNode`. |
| Quieres que el grupo aparezca en una página específica | Move the builder’s cursor with `builder.MoveToDocumentEnd()` or `builder.MoveToPage(pageNumber)`. |
| Requieres unidades diferentes (p. ej., centímetros) | Use `ConvertUtil.InchToPoint(1.0)` to convert inches to points, the unit Word expects. |
| Quieres que el cuadro de texto ajuste el texto | Set `textBox.TextBoxWrap = TextBoxWrapType.Square` after creating the textbox. |
| Trabajando con versiones más antiguas de .NET Framework | The same API works with .NET Framework 4.7+, but ensure you reference the correct Aspose.Words version. |

**Consejo profesional:** Siempre establece el `Width` y `Height` del grupo *después* de agregar todas las formas hijas. Esto garantiza que el grupo envuelva completamente su contenido, evitando recortes al abrir el documento en Word.

## Conclusión

Ahora sabes cómo **save docx file** mientras **add rectangle shape**, **group shapes word**, **set shape dimensions** y **create textbox programmatically** usando Aspose.Words para .NET. El ejemplo completo muestra un patrón limpio y repetible que puedes adaptar a diseños más complejos, como gráficos, imágenes,

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tutorial de sombra de forma Aspose.Words – Añadir una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}