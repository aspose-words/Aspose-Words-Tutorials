---
category: general
date: 2026-10-10
description: Traduzca el párrafo al francés y aprenda cómo cambiar la etiqueta de
  datos del gráfico, personalizar la etiqueta de datos del gráfico y guardar el archivo
  docx editado usando Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: es
lastmod: 2026-10-10
og_description: Traduce el párrafo al francés y aprende cómo cambiar la etiqueta de
  datos del gráfico, personalizar la etiqueta de datos del gráfico y guardar el archivo
  docx editado usando Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Traducir párrafo al francés y cambiar la etiqueta del gráfico en Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Traducir párrafo al francés y cambiar la etiqueta del gráfico en Word
url: /es/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Traducir párrafo al francés y cambiar la etiqueta del gráfico en Word

Si necesita **traducir párrafo al francés** mientras también actualiza un gráfico dentro del mismo documento Word, esta guía le muestra exactamente cómo. Usando Aspose.Words AI puede traducir texto automáticamente, luego modificar la etiqueta de datos de un gráfico y finalmente guardar el archivo `.docx` editado, todo en unos pocos pasos sencillos.

El tutorial cubre todo, desde cargar el archivo fuente hasta persistir los cambios. Al final podrá traducir cualquier párrafo, personalizar la etiqueta de datos de un gráfico y generar un nuevo archivo Word listo para distribución. No se requieren scripts externos; todo el flujo de trabajo se encuentra en un único programa C#.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
- Una licencia de Aspose.Words para .NET (o una clave de evaluación gratuita)
- Acceso a Internet para el traductor de Google AI (la clase `Translator` usa la API de Google internamente)
- Un documento Word (`input.docx`) que contiene al menos un párrafo y un gráfico

## Paso 1: Configurar el proyecto e importar espacios de nombres

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Now include the required namespaces at the top of `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Estas importaciones le dan acceso a la carga de documentos, traducción AI y funcionalidad de edición de gráficos.

## Paso 2: Cargar el documento Word fuente

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Cargar el archivo crea una representación en memoria que puede consultar y modificar sin tocar el archivo original en disco.

## Paso 3: Traducir el primer párrafo al francés

The first paragraph is often a title or introductory sentence, making it a good candidate for translation. The `Translator` class abstracts the call to Google’s AI model.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Por qué funciona:**  
`paragraph.Runs.Clear()` elimina todas las ejecuciones de texto existentes, asegurando que la nueva traducción no se concatene con el contenido antiguo. `new Run(document, translatedText)` crea una nueva ejecución que hereda el formato del párrafo.

## Paso 4: Ubicar el primer gráfico y personalizar su etiqueta de datos

Charts are stored as `Shape` nodes of type `NodeType.Shape`. The first chart can be fetched with `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Explanation of the key steps:**

- `GetChild(NodeType.Shape, 0, true)` realiza una búsqueda en profundidad y devuelve la primera forma, que en nuestro caso es un gráfico.
- `ChartSeries` representa una colección de puntos de datos; la primera serie (`Series[0]`) típicamente corresponde al conjunto de datos principal.
- `ChartDataLabelPosition.OutsideEnd` mueve la etiqueta fuera del extremo de la barra, mejorando la legibilidad.
- Establecer `dataLabel.Text` a una cadena en francés alinea la etiqueta con el párrafo traducido.

## Paso 5: Guardar el documento con el párrafo traducido

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

En este punto el documento contiene el párrafo en francés pero aún mantiene la configuración original del gráfico.

## Paso 6: Guardar el documento con el gráfico actualizado

You can reuse the same `Document` instance—no need to reload it—because the chart modifications are already in memory.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Both files are now ready for distribution:

- **`translated.docx`** – contiene el párrafo en francés.
- **`chart-updated.docx`** – contiene el párrafo en francés *y* la etiqueta de gráfico personalizada.

## Ejemplo completo y ejecutable

Below is the full program you can copy‑paste into `Program.cs`. It compiles and runs as‑is, assuming you have replaced `YOUR_DIRECTORY` with a real folder path.



## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}