---
category: general
date: 2026-08-04
description: La colocación personalizada de etiquetas de datos para gráficos en C#
  le permite centrar las etiquetas en las porciones del gráfico. Siga esta guía paso
  a paso usando la API de gráficos de Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: es
lastmod: 2026-08-04
og_description: La colocación personalizada de etiquetas de datos para gráficos en
  C# le muestra cómo centrar todas las etiquetas de datos en cada segmento de un gráfico
  de Word. Domine la posición de las etiquetas de datos del gráfico con Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Colocación personalizada de etiquetas de datos para gráficos en C# – guía
  paso a paso
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Colocación personalizada de etiquetas de datos para gráficos en C#
url: /es/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Colocación personalizada de etiquetas de datos para gráficos en C#

**Colocación personalizada de etiquetas de datos para gráficos** le permite controlar exactamente dónde aparece cada etiqueta en un gráfico dentro de un documento de Word. En este tutorial aprenderá a centrar todas las etiquetas de datos en cada porción usando C# y la API de gráficos de Aspose.Words.

Obtendrá un ejemplo completo y ejecutable que carga un archivo `.docx`, accede a la primera forma de gráfico, cambia la `Position` de cada etiqueta a `Center` y guarda el documento actualizado. No se requieren referencias externas, solo la biblioteca Aspose.Words para .NET y un entorno básico de desarrollo en C#.

**Lo que aprenderá**

* Cómo cargar un documento de Word que contiene un gráfico.  
* Cómo localizar la forma de gráfico con la API de gráficos de Aspose.Words.  
* Cómo aplicar **posicionamiento de etiquetas de datos del gráfico** a cada serie del gráfico.  
* Cómo guardar el documento para que las etiquetas centradas aparezcan en Word.  

**Requisitos previos**

* .NET 6.0 (o posterior) instalado.  
* Visual Studio 2022 (o cualquier IDE de C#).  
* Una referencia al paquete NuGet `Aspose.Words`.  
* Un archivo de Word (`Chart.docx`) que contenga al menos un gráfico.

---

## Colocación personalizada de etiquetas de datos para gráficos – paso 1: cargar el documento

La primera acción es abrir el archivo de Word que contiene el gráfico. `Document` es el punto de entrada para cualquier manipulación con Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Por qué este paso es importante*: Sin cargar el documento no puede acceder al objeto del gráfico. La validación asegura que reciba un error claro si el archivo no contiene un gráfico, evitando una referencia nula más adelante.

---

## Uso de la API de gráficos de Aspose.Words para acceder a las formas de gráfico

Aspose.Words trata un gráfico como un objeto `Chart` anidado dentro de una `Shape`. Lo recupera convirtiendo el nodo hijo apropiado.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Por qué este paso es importante*: Acceder directamente a `Chart` le brinda control total sobre series, puntos de datos y propiedades de etiquetas. Si la forma no es un gráfico, el código se aborta temprano con un mensaje informativo.

---

## Configuración del posicionamiento de etiquetas de datos del gráfico en C#

Ahora recorra cada serie y cada etiqueta de datos, estableciendo la `Position` a `Center`. Este es el núcleo de **Colocación personalizada de etiquetas de datos para gráficos**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Consejo profesional**: Si necesita una ubicación diferente (p. ej., `InsideEnd` para un gráfico de columnas), cambie el valor del enumerado en consecuencia. El enumerado `ChartDataLabelPosition` cubre todas las posiciones estándar admitidas por Word.

*Por qué este paso es importante*: Cambiar `label.Position` actualiza la representación OOXML subyacente, de modo que la etiqueta aparezca centrada cuando el documento se abra en Microsoft Word.

---

## Guardar el documento de Word con las etiquetas actualizadas

Después de modificar el gráfico, persista los cambios en un archivo. Puede sobrescribir el original o crear una copia nueva.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Por qué este paso es importante*: Guardar escribe el OOXML actualizado en el disco. Al abrir `ChartLabelsCentered.docx` en Word verá cada etiqueta de porción centrada, confirmando que **Colocación personalizada de etiquetas de datos para gráficos** se completó con éxito.

---

## Casos límite y variaciones

| Situación | Cómo manejarlo |
|-----------|----------------|
| **Múltiples gráficos** en el mismo documento | Recorrer `doc.GetChildNodes(NodeType.Shape, true)` y comprobar `shape.HasChart` para cada forma. |
| **Tipos de gráfico diferentes** (circular, rosquilla, barra) | `ChartDataLabelPosition.Center` funciona para gráficos tipo circular. Para gráficos de barra/columna puede preferir `InsideEnd` o `OutsideEnd`. |
| **El texto de la etiqueta necesita formato** | Acceda a `label.TextProperties` para establecer tamaño de fuente, color o negrita. |
| **Ejecutándose en .NET Core** | Asegúrese de referenciar la versión .NET Standard de Aspose.Words; la API es idéntica. |

---

## Ejemplo completo en funcionamiento

A continuación se muestra el programa completo que puede copiar y pegar en una aplicación de consola. Incluye todas las directivas `using` necesarias y el manejo de errores.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Resultado esperado**: Abra `ChartLabelsCentered.docx` en Microsoft Word. Cada porción del gráfico mostrará ahora su etiqueta de datos directamente en el centro de la porción, proporcionando una apariencia visual más limpia.

---

## Conclusión

Ahora dispone de una solución completa de **Colocación personalizada de etiquetas de datos para gráficos** en C#. Al cargar el documento, acceder al gráfico mediante la API de gráficos de Aspose.Words, establecer `ChartDataLabelPosition.Center` para cada etiqueta y guardar el archivo, puede automatizar el posicionamiento de etiquetas para cualquier gráfico basado en Word.

A continuación, explore otras opciones de **posicionamiento de etiquetas de datos del gráfico** como `InsideEnd` o `OutsideEnd`, o experimente con **manipulación de gráficos en C#** para cambiar colores, añadir leyendas o generar gráficos desde cero. Estas extensiones se basan directamente en las técnicas cubiertas aquí y amplían sus habilidades de automatización de gráficos en documentos Word. ¡Feliz codificación!

## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}