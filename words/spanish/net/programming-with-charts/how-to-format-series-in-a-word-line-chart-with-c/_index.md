---
category: general
date: 2026-09-21
description: Cómo formatear series en un gráfico de líneas de Word usando C#. Aprende
  a crear un documento de Word, insertar un gráfico de líneas y aplicar un formato
  numérico personalizado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: es
lastmod: 2026-09-21
og_description: Cómo formatear series en un gráfico de líneas de Word usando C#. Este
  tutorial le muestra cómo crear un documento de Word, insertar un gráfico de líneas
  y aplicar un formato numérico personalizado.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Cómo formatear series en un gráfico de líneas de Word con C# – guía paso
  a paso
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Cómo dar formato a series en un gráfico de líneas de Word con C#
url: /es/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo formatear series en un gráfico de líneas de Word con C#

Si necesitas **cómo formatear series** en un gráfico de líneas de Word, esta guía te brinda una solución completa y lista‑para‑ejecutar. Verás cómo **crear un documento Word**, **insertar un gráfico de líneas** y **aplicar un formato numérico personalizado** a los valores Y, todo con Aspose.Words for .NET.

La automatización de Word se vuelve sencilla una vez que comprendes el modelo de objetos del gráfico. Al final de este tutorial tendrás un archivo Word que contiene un gráfico de líneas cuyas series de datos se muestran como porcentajes con dos decimales.

## Lo que lograrás

* Generar programáticamente un archivo `.docx` vacío.  
* Añadir un gráfico de líneas de tamaño 400 × 300 puntos.  
* Acceder a la primera serie de datos del gráfico.  
* Aplicar el código de formato `#,##0.00%` para que los valores Y aparezcan como porcentajes.  

No se requieren herramientas externas más allá del paquete NuGet de Aspose.Words.

## Requisitos previos

* .NET 6.0 SDK o posterior.  
* Visual Studio 2022 (o cualquier IDE de C#).  
* Aspose.Words for .NET 23.10 o más reciente – instalar mediante `dotnet add package Aspose.Words`.  

El código funciona en Windows, Linux y macOS porque Aspose.Words es independiente de la plataforma.

## Crear un documento Word con Aspose.Words

El primer paso es instanciar un objeto `Document`. Este objeto representa todo el archivo Word en memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Por qué es importante*: `Document` es el punto de entrada para todas las operaciones de procesamiento de Word. Sin él no puedes añadir párrafos, tablas o gráficos.

## Insertar un gráfico de líneas en el documento

Un `DocumentBuilder` escribe contenido dentro del `Document`. Llamar a `InsertChart` crea una forma de gráfico en la página actual.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Por qué es importante*: `InsertChart` devuelve un objeto `Chart` que te brinda control total sobre series, ejes y formato. Los parámetros de tamaño se expresan en puntos (1 punto = 1/72 pulgada).

## Acceder a la primera serie de datos

Cada gráfico contiene una o más `ChartSeries`. La primera serie está en el índice 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Por qué es importante*: El objeto `ChartSeries` contiene los valores Y, los valores X y las opciones de formato para una única línea en un gráfico de líneas. Modificar este objeto cambia la representación visual de los datos.

## Aplicar un formato numérico personalizado a la serie

La propiedad `FormatCode` controla cómo se muestran los valores numéricos. Establecerla en `#,##0.00%` indica a Word que trate los valores como porcentajes con dos decimales.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Por qué es importante*: Sin un formato personalizado, Word muestra números decimales sin procesar (p. ej., `0.15`). El código de formato los convierte a `15.00%`, que es lo que suelen requerir los informes empresariales.

## Guardar el documento y verificar el resultado

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Al abrir `FormattedSeriesLineChart.docx` en Microsoft Word, verás un gráfico de líneas donde las etiquetas del eje Y aparecen como `15.00%`, `30.00%`, `45.00%` y `60.00%`. El tamaño del gráfico coincide con las dimensiones suministradas en `InsertChart`.

### Captura de pantalla del resultado esperado

> *Imagen: Una página de documento Word que muestra un gráfico de líneas con valores del eje Y formateados como porcentajes.*  
> *(Texto alternativo: Captura de pantalla de un documento Word que muestra un gráfico de líneas con valores del eje Y formateados como porcentajes)*

## Variaciones comunes y casos límite

| Situación | Ajuste |
|-----------|--------|
| **Series múltiples** | Recorrer `chart.Series` y establecer `FormatCode` para cada serie. |
| **Tipo de gráfico diferente** | Reemplazar `ChartType.Line` por `ChartType.Column`, `ChartType.Pie`, etc. |
| **Separadores específicos de la configuración regional** | Utilizar cadenas de formato dependientes de `CultureInfo`, por ejemplo, `"# ##0,00 %"` para configuraciones regionales francesas. |
| **Fuente de datos dinámica** | Poblar `series.YValues` desde una base de datos o archivo CSV antes de aplicar el formato. |

**Consejo profesional:** Aplica siempre el formato **después** de haber añadido los valores Y. Cambiar el formato primero y luego añadir los valores también funciona, pero aplicarlo después garantiza que el formato se aplique al conjunto de datos final.

## Recapitulación

Ahora sabes **cómo formatear series** en un gráfico de líneas de Word usando C#. El tutorial cubrió:

* Crear un documento Word (`create word document`).  
* Insertar un gráfico de líneas (`insert line chart`, `add chart to word`).  
* Acceder a la primera serie del gráfico.  
* Aplicar un formato numérico personalizado (`apply custom number format`) para mostrar porcentajes.

## Próximos pasos

* Experimenta con diferentes valores de `ChartType` para ver cómo se comportan otras visualizaciones.  
* Añade títulos, etiquetas de ejes y leyendas usando `chart.Title`, `chart.AxisX.Title` y `chart.AxisY.Title`.  
* Exporta el gráfico como imagen (`chart.Save` con `SaveFormat.Png`) para usarlo en informes web.

¡Siéntete libre de adaptar este patrón para generar paneles, informes financieros o cualquier documento que requiera gráficos programáticos! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}