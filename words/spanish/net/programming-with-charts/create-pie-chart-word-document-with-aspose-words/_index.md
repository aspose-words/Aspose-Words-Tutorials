---
category: general
date: 2026-08-10
description: Crear documento Word con gráfico circular usando Aspose.Words. Aprende
  a insertar el gráfico, personalizar los colores del gráfico circular y cambiar el
  color de una porción del círculo en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: es
lastmod: 2026-08-10
og_description: Crear documento de Word con gráfico de pastel usando Aspose.Words.
  Esta guía explica cómo insertar un gráfico, personalizar los colores del gráfico
  de pastel y cambiar el color de una porción del pastel en una aplicación C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Crear documento Word con gráfico circular – Guía de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Crear documento Word con gráfico de pastel usando Aspose.Words
url: /es/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word con gráfico circular usando Aspose.Words

Si necesitas **crear un documento Word con gráfico circular** de forma programática, este tutorial te muestra exactamente cómo hacerlo. Recorreremos la inserción de un gráfico, **personalizar los colores del gráfico circular** y **cambiar el color de una porción del gráfico** usando Aspose.Words para .NET.

Verás un ejemplo completo y ejecutable que puedes copiar en Visual Studio, ejecutar y abrir inmediatamente el *.docx* generado para verificar el gráfico circular con estilo. No se requiere documentación externa; todo lo que necesitas está en esta guía.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado  
* Una licencia válida de Aspose.Words para .NET (o una clave de evaluación temporal)  
* Visual Studio 2022 (o cualquier IDE de C#)  

El código usa solo los espacios de nombres `Aspose.Words` y `Aspose.Words.Drawing.Charts`, por lo que no se requieren paquetes NuGet adicionales más allá de la biblioteca Aspose.Words.

## Crear documento Word con gráfico circular – ejemplo completo

El siguiente programa en C# crea un nuevo documento Word, inserta un gráfico circular, aplica estilo a las dos primeras porciones y guarda el archivo. Cada paso se explica en detalle.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Explicación de cada paso

| Paso | Qué hace | Por qué es importante |
|------|----------|-----------------------|
| **1** | Crea un nuevo `Document` y un `DocumentBuilder`. | El `DocumentBuilder` proporciona métodos fluidos para insertar contenido, como gráficos, en el archivo Word. |
| **2** | Llama a `InsertChart` con `ChartType.Pie` y un tamaño fijo. | `InsertChart` es el **método para insertar un gráfico**; especificar ancho/alto garantiza que el gráfico se ajuste bien a la página. |
| **3** | Añade una serie de datos con tres categorías y valores numéricos. | Un gráfico circular sin datos es invisible; poblarlo demuestra los pasos de estilo. |
| **4** | Establece `Explosion` en el primer punto. | "Explotar" una porción llama la atención sobre un segmento particular, útil para resaltar datos clave. |
| **5** | Establece `ForeColor` para los dos primeros puntos. | Este es el núcleo de **personalizar los colores del gráfico circular**; puedes usar cualquier `System.Drawing.Color`. |
| **6** | Muestra cómo **cambiar el color de una porción del gráfico** para porciones adicionales. | Demuestra que el estilo no está limitado a las dos primeras porciones; puedes colorear cada porción individualmente. |
| **7** | Guarda el documento como `PieChartStyled.docx`. | El resultado final puede abrirse en Microsoft Word, Google Docs o cualquier visor compatible. |

#### Resultado esperado

Al abrir `PieChartStyled.docx` se muestra una sola página con un gráfico circular de 400 × 300 pt:

* Porción 1 (naranja) está explotada hacia afuera.  
* Porción 2 (verde) aparece adyacente a la porción explotada.  
* Porción 3 (azul acero) llena el segmento restante.

El gráfico refleja los valores de datos (30, 45, 25) y los colores personalizados que definiste.

## Cómo dar estilo al gráfico circular – consejos adicionales

* **Usar colores del tema** – en lugar de codificar `Color.Orange`, puedes obtener colores del tema del documento:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Agregar etiquetas de datos** – si deseas mostrar porcentajes en el gráfico:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Redimensionar dinámicamente** – calcula el tamaño del gráfico según los márgenes de la página:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Estas variaciones demuestran la flexibilidad de **cómo dar estilo al gráfico circular** más allá del ejemplo básico.

## Preguntas frecuentes

**P: ¿Esto funciona con .NET Core?**  
R: Sí. Aspose.Words para .NET es compatible con .NET Core, .NET 5, .NET 6 y versiones posteriores. Simplemente referencia el mismo paquete NuGet.

**P: ¿Qué pasa si necesito un gráfico de rosquilla en lugar de un circular?**  
R: Reemplaza `ChartType.Pie` por `ChartType.Doughnut`. Las mismas API de estilo (`Explosion`, `ForeColor`) se aplican.

**P: ¿Puedo insertar el gráfico en un documento existente?**  
R: Abre el archivo existente con `new Document("Existing.docx")`, crea un `DocumentBuilder` para ese documento y llama a `InsertChart` en la posición del cursor deseada.

**P: ¿Cómo manejo conjuntos de datos grandes?**  
R: Los gráficos circulares son mejores para un número limitado de categorías (normalmente < 10). Para muchas categorías, considera un gráfico de barras o columnas.

## Recapitulación del código fuente completo

A continuación tienes el programa completo en un solo bloque para copiar y pegar fácilmente:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Ejecutar este código produce el documento Word con el gráfico circular con estilo descrito anteriormente.

## Conclusión

Ahora sabes cómo **crear documentos Word con gráficos circulares** usando Aspose.Words, **personalizar los colores del gráfico circular** y **cambiar el color de una porción del gráfico** de forma programática. La guía cubrió la inserción del gráfico, la población de datos, la explosión de una porción, la aplicación de colores personalizados y el guardado del resultado.

Desde aquí puedes explorar temas relacionados como **cómo insertar diferentes tipos de gráficos**, agregar leyendas o generar informes de varias páginas con múltiples gráficos. Experimenta con diferentes combinaciones de colores y conjuntos de datos para adaptar los informes a tus necesidades.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insertar gráfico de áreas en documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Crear gráfico de dispersión en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}