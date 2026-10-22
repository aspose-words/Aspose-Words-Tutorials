---
category: general
date: 2026-08-17
description: Cómo agregar controles ActiveX e insertar un gráfico circular en un documento
  de Word usando Aspose.Words. Explotar una porción y guardar como DOCX en unos pocos
  pasos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: es
lastmod: 2026-08-17
og_description: Cómo agregar controles ActiveX, insertar un gráfico circular, separar
  una porción y guardar como DOCX con Aspose.Words – guía completa paso a paso.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Cómo agregar ActiveX e insertar un gráfico circular en un documento de Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Cómo agregar ActiveX e insertar un gráfico circular en un documento de Word
url: /es/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar ActiveX e insertar un gráfico circular en un documento Word

Si necesitas **cómo agregar ActiveX** controles e incrustar un gráfico en un documento Word, este tutorial te muestra una solución completa y ejecutable. Usando Aspose.Words puedes colocar un ActiveX CommandButton, crear un gráfico circular, separar una porción para resaltarla y, finalmente, **guardar como DOCX** en solo unas pocas líneas de C#.

En las secciones siguientes verás cada importación requerida, un listado completo de código y explicaciones de por qué cada paso es importante. Al final podrás integrar controles interactivos y datos visuales en cualquier archivo .docx que generes programáticamente.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
* Paquete Aspose.Words for .NET (disponible vía NuGet)
* Un entorno de desarrollo como Visual Studio 2022 o VS Code
* Familiaridad básica con C# y el modelo de objetos de Word

No se requieren bibliotecas de gráficos de terceros; Aspose.Words proporciona creación de gráficos integrada.

## Cómo agregar controles ActiveX con Aspose.Words

Los controles ActiveX te permiten incrustar elementos de UI interactivos directamente en un archivo Word. En esta guía añadimos un **CommandButton** que luego podrá enlazarse a código VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Por qué funciona esto:**  
`InsertForms2OleControl` crea un contenedor OLE que la UI de Word reconoce como un control ActiveX. Establecer el tipo de control a `CommandButton` y asignarle un texto hace que se comporte como un botón estándar cuando el usuario abre el archivo en Word.

## Insertar gráfico circular y separar una porción

Los gráficos son útiles para visualizar datos sin salir del documento. Los pasos siguientes demuestran **cómo insertar un gráfico** y, específicamente, un **gráfico circular** cuya primera porción está separada.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Por qué separar la porción:**  
Llamar a `SetExplode(0, true)` indica a Aspose.Words que desplace el primer punto de datos, atrayendo la mirada del observador a ese segmento. Esta es una técnica común en presentaciones para resaltar un valor clave.

## Guardar como DOCX

Después de agregar el botón ActiveX y el gráfico, persiste el documento en disco. Este paso muestra **guardar como DOCX** usando el método estándar.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

El archivo `Output.docx` ahora contiene un botón interactivo, un gráfico circular con una porción separada y puede abrirse en Microsoft Word sin complementos adicionales.

## Ejemplo completo ejecutable

Juntando todo, aquí tienes un programa autocontenido que puedes copiar en una aplicación de consola y ejecutar de inmediato.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Resultado esperado:**  
Al abrir `Output.docx` en Word se muestra un botón con la etiqueta *Click Me* y un gráfico circular donde la primera porción (Enero) está desplazada del resto. El botón está listo para manejar eventos VBA, y el gráfico puede editarse usando las herramientas de gráficos integradas de Word.

## Preguntas frecuentes y casos especiales

* **¿Puedo agregar otros tipos de ActiveX?**  
  Sí. Reemplaza `Forms2OleControlType.CommandButton` por cualquier valor del enum `Forms2OleControlType` (p. ej., `CheckBox`, `OptionButton`). El mismo patrón de inserción se aplica.

* **¿Qué pasa si necesito un tipo de gráfico diferente?**  
  Usa `ChartType.Bar`, `ChartType.Line`, etc., en la llamada a `InsertChart`. El paso **cómo insertar gráfico** permanece idéntico; solo cambia el valor del enum.

* **¿Cómo controlar el tamaño de la porción separada?**  
  Actualmente Aspose.Words admite una bandera binaria de separación (true/false). Para un control más fino (p. ej., distancia de desplazamiento) tendrías que editar el OOXML subyacente después de guardar.

* **¿Es el documento compatible con versiones antiguas de Word?**  
  Guardar como DOCX garantiza compatibilidad con Word 2007 y posteriores. Para Word 2003 podrías cambiar a `SaveFormat.Doc`, pero el soporte de ActiveX es limitado en ese formato.

* **¿Necesito referenciar `System.Drawing`?**  
  No. Todos los objetos de dibujo los proporciona Aspose.Words, por lo que el único paquete NuGet requerido es `Aspose.Words`.

## Conclusión

Ahora sabes **cómo agregar ActiveX**, **insertar un gráfico circular**, **separar una porción del gráfico** y **guardar como DOCX** usando Aspose.Words para .NET. El ejemplo completo cubre cada paso, desde la creación del documento hasta su persistencia final, y explica el razonamiento detrás de cada llamada a la API.

A continuación, podrías explorar:

* Agregar macros VBA que respondan al clic del CommandButton (**cómo insertar gráfico** y automatizar actualizaciones de datos)
* Personalizar la apariencia del gráfico (colores, etiquetas de datos) para que coincida con la identidad corporativa
* Incrustar controles ActiveX adicionales como **ComboBox** o **ListBox** para formularios más ricos

¡Siéntete libre de experimentar con el código, reemplazar los datos de ejemplo e integrar la solución en tus propias canalizaciones de generación de documentos! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}