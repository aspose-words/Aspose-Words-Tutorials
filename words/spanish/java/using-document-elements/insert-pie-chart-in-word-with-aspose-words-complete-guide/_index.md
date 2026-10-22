---
category: general
date: 2026-07-26
description: Inserte un gráfico circular en un documento de Word usando Aspose.Words.
  Aprenda cómo agregar el gráfico, separar una porción y mostrar los porcentajes en
  solo unos pocos pasos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: es
lastmod: 2026-07-26
og_description: Inserte un gráfico circular en un archivo de Word con Aspose.Words.
  Siga esta guía para aprender a agregar el gráfico, explotar la porción y mostrar
  los porcentajes rápidamente.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Insertar gráfico circular en Word – Tutorial paso a paso de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Insertar gráfico circular en Word con Aspose.Words – Guía completa
url: /es/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar gráfico circular en Word con Aspose.Words – Guía completa

¿Alguna vez necesitaste **insertar pie chart** en un informe de Word pero no sabías por dónde empezar? No estás solo. En muchas aplicaciones empresariales, el impacto visual de un gráfico circular hace que los datos sean instantáneamente digestibles, y Aspose.Words lo hace posible con solo unas pocas líneas de código.

En este tutorial recorreremos paso a paso cómo **add chart to Word**, explotar una porción para enfatizarla y mostrar porcentajes en las etiquetas de datos. Al final tendrás un ejemplo listo‑para‑ejecutar que podrás incorporar en cualquier proyecto .NET.

---

## Requisitos previos

Antes de sumergirnos, asegúrate de contar con:

- .NET 6.0 o posterior (el código funciona tanto con .NET Core como con .NET Framework)
- El paquete NuGet Aspose.Words for .NET instalado  
  ```bash
  dotnet add package Aspose.Words
  ```
- Un conocimiento básico de la sintaxis de C#—no se requiere nada avanzado
- Un IDE de tu elección (Visual Studio, Rider o VS Code)

Eso es todo. Pongámonos manos a la obra.

---

## Insertar gráfico circular en un documento Word

Lo primero que necesitamos es un objeto `Document` nuevo y un `DocumentBuilder`. Piensa en el builder como una pluma que escribe directamente sobre el lienzo de Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** El `Document` representa todo el archivo .docx, mientras que el `DocumentBuilder` nos brinda una API cómoda para insertar elementos como gráficos, tablas y texto. Esta es la base para cualquier operación **how to add chart**.

---

## Cómo agregar un gráfico a Word

Ahora que tenemos un builder, podemos **insert pie chart** realmente. El método `insertChart` recibe el tipo de gráfico y las dimensiones deseadas en puntos (1 punto = 1/72 de pulgada).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tip:** Si necesitas un tamaño diferente, simplemente ajusta los valores de ancho y alto. El gráfico se escalará automáticamente para ajustarse a los márgenes de la página.

---

## Cómo explotar una porción para enfatizar

Un ajuste visual común es “explotar” una porción para que sobresalga del círculo. Esto atrae la mirada del lector hacia el segmento más importante.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Why explode a slice?** Cuando deseas resaltar una categoría particular—por ejemplo, “Q1 revenue” en un informe financiero—explotar la porción la hace instantáneamente visible sin texto adicional.

---

## Cómo mostrar porcentajes en las etiquetas de datos

La mayoría de los gráficos circulares se ven mejor cuando cada porción muestra su porcentaje. Aspose.Words nos permite activar esto con una sola propiedad.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Quick note:** La bandera `ShowPercentage` funciona para todos los puntos de la serie, por lo que no necesitas configurarla por cada porción.

---

## Guardar el documento que contiene el gráfico

Finalmente, escribimos el documento en disco. Elige cualquier carpeta que prefieras; solo asegúrate de que la ruta exista.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Al abrir `PieChart.docx` en Microsoft Word verás un gráfico circular perfectamente renderizado con la primera porción explotada y los porcentajes mostrados—exactamente lo que esperas de un informe empresarial pulido.

---

## Ejemplo completo funcional

A continuación tienes el programa completo, listo para copiar y pegar. Ejecútalo como una aplicación de consola y verifica el archivo de salida.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected result:** Abre el `PieChart.docx` generado. Verás un gráfico circular de tres porciones titulado “Sales Q1”, con la primera porción extraída y cada porción etiquetada “30 %”, “45 %” y “25 %”. El visual coincide con los datos que proporcionamos.

---

## Preguntas comunes y casos límite

- **What if I need more than one series?**  
  Simplemente agrega objetos `ChartSeries` adicionales a `chart.Series`. Cada serie puede tener su propio conjunto de datos, colores y configuraciones de explosión.

- **Can I change the chart’s colors?**  
  Sí. Cada `ChartPoint` tiene una propiedad `Format.Fill.ForeColor` que puedes establecer a cualquier `System.Drawing.Color`.

- **What about different chart types?**  
  El enum `ChartType` incluye barra, línea, donut y muchos más. Sustituye `ChartType.Pie` por el tipo visual que necesites.

- **Is the chart editable in Word after insertion?**  
  Absolutamente. Word trata el gráfico como un gráfico nativo de Office, por lo que los usuarios pueden hacer doble clic para abrir el editor de gráficos incorporado.

---

## Conclusión

Ahora sabes exactamente cómo **insert pie chart** en un documento Word usando Aspose.Words, **how to add chart to word**, **how to explode slice**, y **how to show percentages** en las etiquetas de datos. El ejemplo completo anterior está listo para ejecutarse, y puedes ampliarlo con datos personalizados, estilos o series adicionales.

¿Listo para el siguiente paso? Prueba cambiar el gráfico circular por un donut, o genera un lote de informes con diferentes conjuntos de datos automáticamente. Si tienes curiosidad por otras visualizaciones, consulta nuestras guías sobre **how to add chart** para gráficos de barras y líneas, o explora la referencia de la API **add chart to word** para personalizaciones más profundas.

¡Feliz codificación, y que tus documentos sean siempre tan claros como una tarta perfectamente cortada!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insertar gráfico de áreas en documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Crear gráfico de dispersión en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}