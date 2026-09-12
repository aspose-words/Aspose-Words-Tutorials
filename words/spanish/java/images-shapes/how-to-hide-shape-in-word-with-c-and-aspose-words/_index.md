---
category: general
date: 2026-09-11
description: Aprende cómo ocultar una forma en Word usando C#. Esta guía también muestra
  cómo insertar una forma rectangular e insertar una forma en un documento de Word
  con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: es
lastmod: 2026-09-11
og_description: Cómo ocultar una forma en Word usando C# y Aspose.Words. Sigue el
  tutorial paso a paso para insertar una forma rectangular y gestionar las formas
  en un documento de Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Cómo ocultar una forma en Word – guía completa de C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo ocultar una forma en Word con C# y Aspose.Words
url: /es/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo ocultar una forma en Word con C# y Aspose.Words

Si necesitas ocultar una forma en Word manteniendo la forma en la estructura del documento, este tutorial te muestra exactamente cómo. Usando Aspose.Words para .NET puedes insertar una forma rectangular, ocultarla y conservar su posición para procesamiento posterior.

La automatización de Word a menudo requiere un control fino sobre las formas—ya sea que estés generando plantillas, preparando informes o construyendo un servicio de edición de documentos. Al final de esta guía podrás:

* Insertar una forma rectangular en un documento Word (`insert rectangle shape`).
* Ocultar cualquier forma sin eliminarla (`how to hide shape in word`).
* Guardar el resultado y verificar que la forma oculta no aparezca en la vista renderizada (`insert shape into word document`).

El ejemplo funciona con Aspose.Words 24.10 o posterior y tiene como objetivo .NET 6.0+, pero los conceptos se aplican también a versiones anteriores.

## Requisitos previos

* **Aspose.Words for .NET** ≥ 24.10. Puedes obtener una licencia temporal gratuita del sitio web de Aspose.
* **.NET SDK** 6.0 o más reciente instalado en tu máquina.
* Un entorno de desarrollo como Visual Studio 2022, VS Code o Rider.
* Familiaridad básica con C# y el concepto Word Open XML (opcional pero útil).

## Cómo ocultar una forma en Word con Aspose.Words

A continuación se muestra un programa completo y ejecutable que demuestra todo el flujo de trabajo—desde crear un documento hasta insertar una forma rectangular y, finalmente, ocultarla.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Explicación de cada paso

1. **Crear un nuevo documento** – `Document` representa el archivo Word en memoria. `DocumentBuilder` proporciona una API fluida para insertar contenido.  
2. **Insertar forma rectangular** – `InsertShape` crea un objeto de dibujo del tipo `Rectangle`. Las dimensiones se expresan en puntos (1 pt ≈ 1/72 in). Esto satisface el requisito `insert rectangle shape`.  
3. **Ocultar la forma** – Establecer `Shape.Hidden = true` marca la forma como oculta en el marcado Word (`<w:hidden/>`). La forma sigue formando parte del árbol del documento, por lo que puedes volver a mostrarla o referenciarla programáticamente más adelante. Este es el núcleo de `how to hide shape in word`.  
4. **Guardar el archivo** – El documento se escribe en `output.docx`. Al abrirlo en Microsoft Word, el rectángulo no será visible, pero aún existirá en el XML y puede inspeccionarse con un visor ZIP o el Open XML SDK.

### Resultado esperado

Abre `output.docx` en Microsoft Word:

* El documento aparece vacío—sin forma visible.  
* Si inspeccionas el XML subyacente (`word/document.xml`) encontrarás un elemento `<w:pict>` con un atributo `<w:hidden/>`, confirmando que la forma está presente pero oculta.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

La forma oculta puede volver a ser visible estableciendo `Hidden = false` y volviendo a guardar el documento.

## Insertar forma rectangular en un documento Word

Aunque el objetivo principal es ocultar una forma, muchos escenarios comienzan insertando una forma primero. El método `InsertShape` admite muchos valores de `ShapeType`, incluidos `Rectangle`, `Ellipse`, `Line` y imágenes personalizadas.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**¿Por qué usar un rectángulo?**  
Un rectángulo proporciona un contenedor limpio y alineado a los ejes que puede contener texto, imágenes u otras formas anidadas. A menudo se usa como marcador de posición para contenido dinámico como tablas o gráficos. Al insertar el rectángulo primero, preservas la consistencia del diseño incluso después de ocultarlo más adelante.

## Insertar forma en documento Word – buenas prácticas

Cuando `insert shape into word document`, considera lo siguiente:

* **Establecer dimensiones explícitas** – Evita depender del dimensionado automático; especifica ancho y alto en puntos para garantizar un diseño consistente en todas las plataformas.  
* **Definir posicionamiento** – Por defecto la forma está anclada al párrafo actual. Usa `builder.MoveTo` o `builder.StartBookmark` para colocarla con precisión.  
* **Aplicar estilo temprano** – El color de relleno, estilo de línea y ajuste de texto afectan la apariencia final. Incluso las formas ocultas se benefician de un estilo adecuado porque el marcado permanece sin cambios.  
* **Compatibilidad de versiones** – La propiedad `Hidden` solo está disponible a partir de Aspose.Words 24.10. Si apuntas a una versión anterior, puedes añadir manualmente el atributo `<w:hidden/>` usando la API `Node`.

### Añadir manualmente el atributo hidden (alternativa)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Ejemplo completo de extremo a extremo

Juntando todo, aquí tienes un único programa que:

1. Inserta una forma rectangular.  
2. Oculta la forma.  
3. Inserta una elipse visible como contraste.  
4. Guarda el documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Ejecutar el programa genera `demo_output.docx`. Al abrirlo, verás solo la elipse coral; el rectángulo verde está presente en el XML pero oculto en la vista.

## Preguntas frecuentes y casos límite

**P: ¿Ocultar una forma afecta la paginación?**  
R: No. Las formas ocultas son ignoradas por el motor de diseño, por lo que no consumen espacio. Esto es útil para contenido de marcador de posición que no debe afectar los saltos de página.

**P: ¿Puedo ocultar una forma que forma parte de un encabezado o pie de página?**  
R: Sí. La misma propiedad `Hidden` funciona en formas ubicadas en cualquier parte del árbol del documento, incluidos encabezados, pies de página e incluso dentro de tablas.

**P: ¿Qué pasa si necesito ocultar varias formas a la vez?**  
R: Recorre la colección `Document.GetChildNodes(NodeType.Shape, true)` y establece `Hidden = true` para cada forma objetivo.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**P: ¿Se conserva el atributo hidden al convertir a PDF?**  
R: Al convertir a PDF, las formas ocultas se omiten por defecto, coincidiendo con el comportamiento de renderizado de Word. Si las necesitas en el PDF, debes mostrarlas antes de la conversión.

## Consejos y trampas

* **Consejo profesional:** Establece `shape.WrapType = WrapType.None` antes de ocultar si planeas volver a mostrar la forma sin alterar el texto circundante.  
* **Cuidado con versiones antiguas de Aspose.Words:** La propiedad `Hidden` lanza `NotSupportedException` antes de la 24.10. Usa el enfoque manual de XML en ese caso.  
* **Pruebas:** Siempre abre el `.docx` generado en Word y usa “Mostrar marcado XML” (pestaña Desarrollador) para verificar que el atributo `<w:hidden/>` está presente.

## Conclusión

Ahora sabes cómo ocultar una forma en Word usando C# y Aspose.Words, así como insertar una forma rectangular e insertar forma en documento Word con control total sobre la visibilidad. Al aprovechar la propiedad `Hidden` puedes mantener las formas en el modelo del documento para procesamiento posterior mientras presentas una vista limpia a los usuarios finales.

A continuación, explora temas relacionados como **actualizar propiedades de forma en tiempo de ejecución**, **convertir formas ocultas a imágenes** o **usar el Open XML SDK para manipular elementos ocultos directamente**. Estas extensiones profundizarán

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}