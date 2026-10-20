---
category: general
date: 2026-09-21
description: Crea un documento Word en blanco y aprende cómo insertar un gráfico de
  radar en un archivo Word usando DocumentBuilder – guía paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: es
lastmod: 2026-09-21
og_description: Cree un documento de Word en blanco e inserte un gráfico de radar
  en un archivo de Word con Aspose.Words. Siga este tutorial para generar rápidamente
  un gráfico en un documento de Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Crea un documento Word en blanco y agrega un gráfico de radar – guía completa
  de C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Cómo crear un documento Word en blanco y agregar un gráfico de radar en C#
url: /es/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y agregar un gráfico de radar en C#

Si necesitas **crear un documento Word en blanco** e incrustar un gráfico de radar (radial), este tutorial ofrece una solución lista para ejecutar. Verás cómo usar Aspose.Words .NET para generar el archivo, insertar el gráfico y guardar el resultado, todo en unos pocos pasos concisos.

Un documento en blanco proporciona un lienzo limpio para cualquier escenario de generación automática de informes, y agregar un gráfico de radar te permite visualizar datos multidimensionales directamente dentro de Word. Al final de esta guía podrás generar un documento Word con gráfico sin necesidad de edición manual.

## Lo que aprenderás

* Cómo **crear un documento Word en blanco** programáticamente con C#.
* El código exacto para **insertar un gráfico de radar** usando `DocumentBuilder`.
* Formas de **insertar un gráfico en un archivo Word** y personalizar su tamaño.
* Cómo **generar un gráfico en un documento Word** y verificar la salida.
* Consejos para **agregar archivos de gráficos radiales en Word**, incluyendo errores comunes.

### Requisitos previos

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+).
* Aspose.Words for .NET (paquete NuGet `Aspose.Words` versión 23.9 o más reciente).
* Familiaridad básica con C# y Visual Studio o tu IDE preferido.

## Crear un documento Word en blanco con C#

El primer paso es instanciar un objeto `Document` vacío. Este objeto representa un archivo `.docx` completamente en blanco.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` crea la estructura del archivo pero aún no contiene secciones ni páginas. Aspose.Words agrega automáticamente una sección predeterminada cuando comienzas a añadir contenido, por lo que el paso siguiente funciona sin configuración adicional.

## Cómo insertar un gráfico de radar en el archivo Word

Un gráfico de radar (también llamado gráfico radial) visualiza puntos de datos en ejes que irradian desde un punto central. Aspose.Words proporciona `DocumentBuilder.insertChart` para este propósito.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` devuelve un objeto `Chart` que puedes configurar más adelante. El gráfico aparece en la primera página del documento en blanco porque el builder está posicionado al inicio del documento por defecto.

## Insertar gráfico en un archivo Word – agregando series de datos

Un gráfico sin datos es invisible. Pobla el gráfico de radar con una o más series para que tenga sentido.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Puedes agregar tantas series como necesites. Cada serie puede tener un nombre distinto, que aparece en la leyenda del gráfico. Los puntos de datos corresponden a los ejes radiales; el orden en que los añades define su posición alrededor del círculo.

## Generar un gráfico en un documento Word – guardando el archivo

Después de construir el gráfico, persiste el documento en disco. Elige una ubicación a la que tengas permiso de escritura.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Al abrir el archivo `.docx` resultante en Microsoft Word, verás una página en blanco con un gráfico de radar de tamaño 400 × 300 puntos, poblado con los datos de ejemplo.

### Resultado esperado

* Un archivo `RadialChartExample.docx` en tu escritorio.
* La primera página contiene un gráfico de radar con cinco puntos de datos etiquetados como “Series 1”.
* No aparece texto adicional porque el documento comenzó en blanco.

## Agregar gráfico radial en Word – manejando casos límite comunes

### 1. Cambiar el tamaño del gráfico después de la inserción

Si las dimensiones iniciales no se ajustan a tu diseño, cambia el tamaño del gráfico así:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Insertar el gráfico en una ubicación específica

Puedes mover el cursor del builder a un marcador, celda de tabla o párrafo antes de llamar a `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Personalizar la apariencia del gráfico

Aspose.Words expone todo el modelo de objetos del gráfico, lo que permite establecer títulos, etiquetas de ejes y colores.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Gestionar fuentes faltantes

Si el entorno de destino no tiene una fuente utilizada en el gráfico, Aspose.Words sustituye una fuente predeterminada. Para garantizar consistencia, incrusta las fuentes requeridas:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Exportar a otros formatos

El mismo documento puede guardarse como PDF, HTML o PNG sin cambios adicionales en el código:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Ejemplo completo y ejecutable

Unir todas las piezas te brinda un programa único que puedes copiar, pegar y ejecutar.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Ejecuta este programa, abre el archivo generado y verás un gráfico de radar profesional listo para distribuir.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **insertar un gráfico de radar** y **generar un gráfico en un documento Word** usando Aspose.Words. Siguiendo los pasos anteriores también puedes **agregar archivos de gráficos radiales en Word** a cualquier canal de generación automática de informes, personalizar tamaño, estilo y exportar a formatos adicionales.

**Próximos pasos**

* Explora otros tipos de gráficos (`ChartType.Column`, `ChartType.Pie`) para ampliar tu conjunto de herramientas de informes.
* Combina varios gráficos en una sola página llamando a `InsertChart` repetidamente.
* Integra datos de una base de datos o archivo CSV para poblar series dinámicamente.
* Revisa la documentación de Aspose.Words para opciones avanzadas de formato, como etiquetas de datos condicionales y plantillas de gráficos.

Siéntete libre de experimentar con el código, ajustar dimensiones o reemplazar los datos de ejemplo con métricas reales de negocio. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Crear gráfico de dispersión en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insertar un gráfico de burbujas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}