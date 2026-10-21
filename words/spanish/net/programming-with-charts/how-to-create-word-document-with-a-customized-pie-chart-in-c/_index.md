---
category: general
date: 2026-10-07
description: Aprende cómo crear un documento de Word e insertar un gráfico circular
  usando Aspose.Words en C#. La guía también muestra cómo generar un archivo de Word
  con etiquetas de gráfico personalizadas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: es
lastmod: 2026-10-07
og_description: Crea un documento de Word e inserta un gráfico circular en C#. Sigue
  esta guía paso a paso para generar un archivo de Word con etiquetas de gráfico totalmente
  personalizadas.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Crear un documento Word con un gráfico circular personalizado en C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Cómo crear un documento de Word con un gráfico circular personalizado en C#
url: /es/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word con un gráfico circular personalizado en C#

Si necesitas **crear un documento Word** de forma programática, este tutorial te muestra cómo **insertar un gráfico circular** y personalizar sus etiquetas de datos usando Aspose.Words para .NET. También aprenderás a **generar un archivo Word** que contiene un gráfico completamente estilizado, cubriendo todo, desde la configuración del proyecto hasta el guardado del documento final.

La guía recorre cada paso necesario para agregar un gráfico, ajustar la posición de las etiquetas, habilitar líneas guía y, finalmente, guardar el resultado como un archivo `.docx`. No se requieren herramientas externas más allá de la biblioteca Aspose.Words, y el código fuente completo se proporciona para que puedas copiar, pegar y ejecutar al instante.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK .NET 6.0 o posterior instalado  
* Una licencia válida de Aspose.Words para .NET (o una clave de evaluación gratuita)  
* Un IDE como Visual Studio 2022 o Visual Studio Code  

También necesitarás agregar los siguientes paquetes NuGet a tu proyecto:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Estos paquetes exponen las clases `Document`, `DocumentBuilder` y las relacionadas con gráficos que se usan en los ejemplos a continuación.

## Crear documento Word y agregar un gráfico

El primer paso es **crear un documento Word** y obtener un `DocumentBuilder` que te permite insertar contenido. El builder funciona como un cursor posicionado dentro del documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

El objeto `Document` representa todo el archivo Word, mientras que el `DocumentBuilder` proporciona métodos como `InsertChart` que colocan objetos directamente en el flujo del documento.

## Insertar gráfico circular en el documento

Ahora que el builder está listo, puedes **insertar un gráfico circular** con un tamaño específico. El gráfico se agrega en la posición actual del builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` devuelve un objeto `Chart` que puedes manipular más adelante. Los datos de ejemplo crean cuatro porciones que representan ventas trimestrales.

## Personalizar las etiquetas de datos del gráfico circular

Para que el gráfico sea más legible, a menudo es necesario **personalizar las etiquetas del gráfico circular**, posicionándolas fuera de las porciones y mostrando líneas guía. Aquí es donde entra en juego `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Establecer `Position` a `OutsideEnd` mueve cada etiqueta más allá del borde de la porción, mientras que `ShowLeaderLines` dibuja una línea que conecta la etiqueta con su porción. Las banderas opcionales `ShowValue` y `ShowPercentage` brindan a los lectores tanto los números crudos como los porcentajes relativos.

**Consejo profesional:** Si necesitas formatear la fuente de la etiqueta, usa `dataLabels.Font` para establecer tamaño, color y estilo. Esto asegura que el gráfico coincida con la identidad corporativa.

## Guardar y generar el archivo Word

Una vez que el gráfico está completamente configurado, puedes **generar un archivo Word** guardando la instancia `Document` en disco. Elige el formato `.docx` para máxima compatibilidad con versiones modernas de Word.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Cuando abras `CustomPieChart.docx`, verás un gráfico circular con cuatro porciones, cada una etiquetada fuera de la porción, conectada por líneas guía y mostrando tanto el valor como el porcentaje.

![Captura de pantalla de un documento Word que contiene un gráfico circular personalizado creado con C#](image-placeholder.png)

*La imagen muestra el resultado final del tutorial **create word document**.*

## Variaciones comunes y casos límite

| Escenario | Cómo adaptar el código |
|----------|------------------------|
| **Múltiples series** | Agrega objetos `ChartSeries` adicionales a `pieChart.Series`. Cada serie puede tener su propia colección `DataLabels` para estilos independientes. |
| **Tamaño de gráfico diferente** | Cambia los parámetros de ancho y alto en `InsertChart(width, height)`. Los valores están en puntos (1 pt ≈ 1/72 in). |
| **Título del gráfico** | Usa `pieChart.Title.Text = "Quarterly Sales"` para añadir un título descriptivo. |
| **Exportar a PDF** | Llama a `document.Save("Report.pdf", SaveFormat.Pdf);` después de construir el gráfico. |
| **Manejo de licencia** | Coloca tu archivo de licencia (`Aspose.Words.lic`) en la carpeta de la aplicación y cárgalo con `new License().SetLicense("Aspose.Words.lic");` antes de crear el documento. |

Estas variaciones te permiten responder a la pregunta **how to add pie chart** en muchos escenarios del mundo real, desde informes simples hasta paneles complejos.

## Conclusión

Ahora sabes cómo **crear un documento Word**, **insertar un gráfico circular** y **personalizar las etiquetas del gráfico circular** usando Aspose.Words para .NET. El ejemplo completo demuestra un flujo de trabajo limpio: inicializar el documento, agregar un gráfico, ajustar la posición de las etiquetas de datos, habilitar líneas guía y, finalmente, **generar un archivo Word** que puede compartirse con cualquiera.

Intenta ampliar este tutorial experimentando con diferentes tipos de gráficos (`ChartType.Column`, `ChartType.Line`) o aplicando paletas de colores personalizadas para que coincidan con tu marca. Si encuentras problemas, consulta la documentación de Aspose.Words o explora temas relacionados como “how to add pie chart” con múltiples series y fuentes de datos dinámicas.

¡Feliz codificación, y no dudes en compartir tus resultados o hacer preguntas de seguimiento en los comentarios!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de columnas en un documento Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insertar gráfico de áreas en un documento Word](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insertar gráfico de dispersión en un documento Word](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}