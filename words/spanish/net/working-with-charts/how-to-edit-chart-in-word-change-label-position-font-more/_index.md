---
category: general
date: 2026-07-29
description: 'Cómo editar un gráfico en un documento de Word: aprende a cambiar la
  posición de la etiqueta del gráfico, ajustar las etiquetas de un gráfico de barras,
  modificar las etiquetas de datos del gráfico y cambiar la fuente de la etiqueta
  del gráfico.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: es
lastmod: 2026-07-29
og_description: Cómo editar un gráfico en Word rápidamente. Domina el cambio de la
  posición de las etiquetas del gráfico, el ajuste de las etiquetas de los gráficos
  de barras, la modificación de las etiquetas de datos del gráfico y el cambio de
  la fuente de las etiquetas del gráfico.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Cómo editar un gráfico en Word – Cambiar etiquetas y fuente
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Cómo editar un gráfico en Word: cambiar la posición de la etiqueta, la fuente
  y más'
url: /es/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo editar un gráfico en Word: cambiar la posición de la etiqueta, la fuente y más

Editar un gráfico en un documento de Word es una necesidad común cuando deseas que tus informes se vean pulidos. ¿Alguna vez has tenido problemas para **cambiar la posición de la etiqueta del gráfico** o hacer que las etiquetas sean legibles sin buscar en interminables menús? No estás solo—la mayoría de los desarrolladores se topan con este obstáculo al automatizar la generación de informes. En esta guía recorreremos un ejemplo completo y ejecutable que te muestra exactamente cómo **ajustar las etiquetas de un gráfico de barras**, **modificar las etiquetas de datos del gráfico**, y **cambiar la fuente de la etiqueta del gráfico** usando C# y la biblioteca Aspose.Words.

## Lo que aprenderás

- Cargar un archivo .docx que ya contiene un gráfico de barras.  
- Recuperar la primera forma de gráfico y acceder a su colección de etiquetas de datos.  
- **Cambiar la posición de la etiqueta del gráfico** para que las barras se vean más limpias.  
- **Ajustar las etiquetas del gráfico de barras** tamaño de fuente para una mejor legibilidad.  
- Guardar el documento modificado de nuevo en disco.  

> **Prerequisitos**  
> - .NET 6.0 o posterior (el código también funciona en .NET Framework 4.7+).  
> - Aspose.Words for .NET (disponible vía NuGet).  
> - Un archivo Word (`BarChart.docx`) que ya contiene un gráfico de barras.  

Si te falta alguno de estos, obtén el paquete más reciente de Aspose.Words ahora:

```bash
dotnet add package Aspose.Words
```

---

## Cómo editar un gráfico: recuperar el gráfico del documento Word

El primer paso en **cómo editar un gráfico** es cargar el documento y localizar la forma del gráfico. Aspose.Words trata los gráficos como nodos `Shape`, por lo que podemos usar `GetChild` con `NodeType.Shape` para obtener el primer gráfico que encontramos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Por qué es importante:**  
> Al acceder directamente al objeto `Chart`, evitas la sobrecarga de abrir el archivo en Word y ajustar manualmente cada etiqueta. Esto es la piedra angular de cualquier automatización de **modificar etiquetas de datos del gráfico**.

## Ajustar las etiquetas del gráfico de barras: cambiar la posición de la etiqueta del gráfico

Ahora que tenemos la instancia `Chart`, iteremos sobre su `DataLabelCollection`. El objetivo es **cambiar la posición de la etiqueta del gráfico** para que cada etiqueta se sitúe cómodamente dentro de la base de su barra, en lugar de flotar incómodamente encima.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Consejo profesional:**  
> `InsideBase` funciona bien para gráficos de barras verticales. Si trabajas con un gráfico de barras horizontal, prueba `InsideEnd` en su lugar. Experimentar con posiciones es barato—simplemente vuelve a ejecutar el código y abre el documento guardado.

## Cambiar la fuente de la etiqueta del gráfico: ajustar el tamaño de fuente para mayor legibilidad

Una fuente diminuta es el asesino silencioso de la claridad de los informes. Para **cambiar la fuente de la etiqueta del gráfico**, simplemente establece la propiedad `Font.Size` en cada `ChartDataLabel`. La aumentaremos a 9 pt, que es un punto óptimo para la mayoría de los informes impresos.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Por qué hacemos esto:**  
> Ajustar el tamaño de fuente es parte de las mejores prácticas para **modificar etiquetas de datos del gráfico**. Fuentes más grandes mejoran la accesibilidad y reducen la necesidad de procesamiento manual posterior.

## Guardar el documento actualizado

Después de ajustar posiciones y fuentes, el paso final en **cómo editar un gráfico** es persistir los cambios. Aspose.Words lo hace en una sola línea.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Abre `BarChartCustomLabels.docx` en Word y verás las etiquetas ajustadas dentro de las barras, renderizadas con una fuente clara de 9 pt. No más entrecerrar los ojos ante números diminutos.

---

## Ejemplo completo funcional (todos los pasos en un solo archivo)

A continuación hay un programa de consola completo y listo para ejecutar que demuestra todo el flujo—desde cargar el documento hasta guardar la versión actualizada. Copia y pega en un nuevo proyecto de consola .NET y pulsa **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Salida esperada** al ejecutar el programa:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Abre el archivo resultante y verás las **etiquetas del gráfico de barras ajustadas** posicionadas dentro de las barras con un tamaño de fuente cómodo.

---

## Preguntas comunes y casos límite

### ¿Qué pasa si el documento contiene varios gráficos?

El código anterior obtiene el *primer* gráfico (`GetChild(NodeType.Shape, 0, true)`). Para editar todos los gráficos, reemplaza la obtención única con un bucle:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### ¿Cómo **cambiar la fuente de la etiqueta del gráfico** solo para una serie específica?

Cada `ChartSeries` tiene su propia `DataLabelCollection`. Apunta a una serie por índice:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### ¿Esto funciona con gráficos de pastel o de líneas?

Sí—`ChartDataLabelPosition` admite valores como `InsideEnd`, `OutsideEnd` y `BestFit`. Para un gráfico de pastel podrías preferir `OutsideEnd` para mantener las etiquetas legibles.

### ¿Qué pasa con la localización (p.ej., diferentes separadores decimales)?

Aspose.Words respeta la configuración regional del documento. Si necesitas imponer un formato específico, ajusta `label.NumberFormat` antes de guardar.

## Resumen y próximos pasos

Hemos cubierto **cómo editar un gráfico** en un documento Word de principio a fin: cargar el archivo, recuperar el gráfico, **cambiar la posición de la etiqueta del gráfico**, **ajustar las etiquetas del gráfico de barras**, **modificar las etiquetas de datos del gráfico**, y finalmente **cambiar la fuente de la etiqueta del gráfico** antes de guardar. El ejemplo completo está listo para producción y puede integrarse en cualquier canal de automatización.

¿Listo para subir de nivel? Considera estas ideas de seguimiento:

- **Agregar colores a las etiquetas de datos** (`dataLabel.Font.Color = Color.Blue;`).  
- **Mostrar valores como porcentajes** (`dataLabel.NumberFormat = "0%";`).  
- **Crear gráficos programáticamente** en lugar de cargar los existentes.  

Todas estas se basan en la misma superficie de API que usamos hoy, así que te sentirás como en casa.

Si encontraste algún problema, deja un comentario abajo o consulta la documentación de Aspose.Words para opciones de personalización de gráficos más avanzadas. ¡Feliz codificación y disfruta de esos gráficos bellamente etiquetados!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}