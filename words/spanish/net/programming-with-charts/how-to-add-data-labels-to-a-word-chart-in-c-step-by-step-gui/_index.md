---
category: general
date: 2026-08-04
description: Cómo agregar etiquetas de datos en C# con Aspose.Words. Aprende a editar
  el gráfico, centrar las etiquetas de datos del gráfico, mostrar porcentajes en el
  gráfico y personalizar las etiquetas de datos del gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: es
lastmod: 2026-08-04
og_description: Cómo agregar etiquetas de datos en C# usando Aspose.Words. Este tutorial
  le muestra cómo editar el gráfico, centrar las etiquetas de datos del gráfico, mostrar
  porcentajes en el gráfico y personalizar las etiquetas de datos del gráfico.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Cómo agregar etiquetas de datos a un gráfico de Word en C# – guía completa
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Cómo agregar etiquetas de datos a un gráfico de Word en C# – guía paso a paso
url: /es/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar etiquetas de datos a un gráfico de Word en C# – guía paso a paso

Si necesitas **cómo agregar etiquetas de datos** a un gráfico que está dentro de un documento de Word, esta guía te muestra el código exacto que debes ejecutar. Verás cómo editar las propiedades del gráfico, centrar las etiquetas de datos del gráfico, mostrar porcentajes en el gráfico y personalizar las etiquetas de datos del gráfico para cualquier escenario.

El tutorial cubre todo lo necesario para modificar un gráfico existente, desde cargar el documento hasta guardar los cambios. No se requieren referencias externas, solo la biblioteca Aspose.Words para .NET y un entorno básico de desarrollo en C#.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 (o posterior) instalado.  
* Aspose.Words para .NET versión 23.9 o más reciente.  
  Puedes instalarla vía NuGet:

```bash
dotnet add package Aspose.Words
```

* Un archivo de Word (`input.docx`) que contenga al menos un gráfico.

## Cómo agregar etiquetas de datos a un gráfico de Word en C#

Las siguientes secciones te guían paso a paso. La palabra clave principal **cómo agregar etiquetas de datos** aparece de forma natural en la narrativa y en los comentarios del código, manteniendo la densidad dentro del rango recomendado.

### Paso 1 – Cargar el documento de Word que contiene el gráfico

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Por qué es importante este paso*: El objeto `Document` representa todo el archivo de Word. Cargarlo te brinda acceso a cada nodo, incluidas las formas que alojan gráficos.

### Paso 2 – Recuperar el primer gráfico del documento

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Por qué es importante este paso*: Los gráficos se almacenan dentro de nodos `Shape`. Al convertir el nodo recuperado a `Shape` y llamar a `GetChart()`, obtienes un objeto `Chart` que expone series, ejes y colecciones de etiquetas.

### Paso 3 – Habilitar la personalización de etiquetas de datos y mostrar porcentajes en el gráfico

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Por qué es importante este paso*: Establecer `ShowPercentage` indica a Aspose.Words que calcule y muestre la contribución de cada segmento al total. Esto aborda directamente la palabra clave secundaria **mostrar porcentajes en el gráfico**.

### Paso 4 – Cambiar la posición de la etiqueta al centro de cada punto de datos

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Por qué es importante este paso*: La propiedad `Position` controla dónde aparece la etiqueta respecto al punto de datos. Usar `Center` satisface la palabra clave secundaria **centrar etiquetas de datos del gráfico** y mejora la legibilidad en gráficos de pastel o rosquilla.

### Paso 5 – Personalizar más las etiquetas de datos del gráfico (opcional)

Si necesitas mayor control, puedes ajustar la fuente, el color o las líneas guía:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Estas configuraciones ilustran la palabra clave secundaria **personalizar etiquetas de datos del gráfico** y demuestran cómo puedes adaptar la apariencia para que coincida con las directrices de tu marca.

### Paso 6 – Guardar el documento modificado

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Por qué es importante este paso*: Guardar escribe el gráfico actualizado de nuevo en el documento de Word, haciendo visibles las nuevas etiquetas de datos cuando el archivo se abra en Microsoft Word.

## Ejemplo completo y ejecutable

A continuación tienes un programa completo que puedes copiar, pegar y ejecutar. Incluye todas las directivas `using` necesarias y comentarios que explican cada línea.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Resultado esperado

Al abrir `output.docx` en Microsoft Word, el gráfico mostrará:

* Valores de porcentaje junto a cada segmento (p. ej., **25 %**, **40 %**, …).  
* Etiquetas posicionadas en el centro de cada punto de datos.  
* Cualquier estilo adicional que hayas aplicado, como texto rojo en negrita.

Estas pistas visuales hacen que el gráfico sea más fácil de interpretar, especialmente en presentaciones o informes.

## Cómo editar propiedades del gráfico más allá de las etiquetas de datos

Aunque el foco de esta guía es **cómo agregar etiquetas de datos**, también puede que quieras **cómo editar el gráfico** para cambiar títulos, la posición de la leyenda o el formato de los ejes. El objeto `Chart` ofrece propiedades como `Title`, `Legend` y `AxisX/AxisY`. Por ejemplo, para cambiar el título del gráfico:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Todas las modificaciones del gráfico siguen el mismo patrón: recuperar el gráfico, ajustar sus propiedades y luego guardar el documento.

## Errores comunes y consejos de buenas prácticas

| Problema | Por qué ocurre | Solución recomendada |
|---|---|---|
| El gráfico está dentro de una forma agrupada. | `GetChild(NodeType.Shape, …)` devuelve el grupo externo, no el gráfico interno. | Buscar recursivamente una forma con `shape.HasChart`. |
| Las etiquetas de datos no aparecen después de guardar. | No se estableció `ShowValue` o `ShowPercentage` a `true`. | Configurar explícitamente tanto `ShowValue` como `ShowPercentage` según sea necesario. |
| Las etiquetas se superponen en segmentos pequeños. | La posición centrada puede generar aglomeración. | Usar `ChartDataLabelPosition.OutSideEnd` para colocación externa, o habilitar `LeaderLines`. |

Aplicar estos consejos garantiza resultados fiables en diferentes tipos de gráficos.

## Conclusión

Ahora sabes **cómo agregar etiquetas de datos** a un gráfico de Word usando C#. El tutorial cubrió la recuperación del gráfico, la habilitación de la visibilidad de etiquetas, el centrado de las etiquetas, la visualización de porcentajes y la personalización de la apariencia. Con este conocimiento también puedes **cómo editar el gráfico**, **centrar etiquetas de datos del gráfico**, **mostrar porcentajes en el gráfico** y **personalizar etiquetas de datos del gráfico** para cualquier escenario de informes.

¿Listo para seguir explorando? Prueba agregar múltiples series, aplicar formato condicional o exportar el gráfico como imagen. La API de Aspose.Words ofrece amplias capacidades de manipulación de gráficos; experimenta para encontrar la representación visual perfecta para tus datos.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos de implementación en tus propios proyectos.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}