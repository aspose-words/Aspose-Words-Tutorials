---
category: general
date: 2026-09-21
description: Aprende cómo crear un gráfico de pastel e insertarlo en Word usando Aspose.Words,
  agregar etiquetas de datos al gráfico de pastel y mostrar porcentajes en el gráfico
  de pastel en solo unos pocos pasos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: es
lastmod: 2026-09-21
og_description: Crear un gráfico circular en Word usando Aspose.Words, insertar el
  gráfico en Word, agregar etiquetas de datos al gráfico circular y mostrar porcentajes
  en el gráfico circular, todo con ejemplos de código claros.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Crea un gráfico circular en Word con Aspose.Words – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Cómo crear un gráfico circular en un documento de Word con Aspose.Words
url: /es/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico circular en un documento Word con Aspose.Words

Si necesitas **crear un gráfico circular** programáticamente, Aspose.Words lo hace sencillo. En este tutorial verás cómo **insertar un gráfico en Word**, configurar la serie, **agregar etiquetas de datos al gráfico circular**, y finalmente **mostrar porcentajes en el gráfico circular** para que la visualización transmita valores exactos. Al final tendrás un ejemplo completo y ejecutable que puedes incorporar a cualquier proyecto .NET.

Esta guía cubre todo lo que necesitas saber: paquetes NuGet requeridos, el código fuente completo en C#, explicaciones de por qué cada llamada a la API es importante y consejos para personalizar el gráfico. No se requiere documentación externa—simplemente copia, ejecuta y adapta.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK .NET 6.0 o posterior instalado.  
* Visual Studio 2022 (o cualquier IDE que soporte .NET).  
* Una licencia de Aspose.Words para .NET (la versión de prueba gratuita funciona para pruebas).  
* Familiaridad básica con C# y la estructura de documentos Word.

Si ya cuentas con estos elementos, puedes pasar directamente al código.

## Paso 1: Configurar el proyecto e importar Aspose.Words

Crea un nuevo proyecto de consola y agrega el paquete NuGet Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

El paquete incluye el espacio de nombres `Aspose.Words.Drawing.Charts`, que contiene las clases `Chart` y `ChartSeries` que utilizaremos.

**Pro tip:** Mantén tu archivo de licencia (`Aspose.Words.lic`) en la raíz del proyecto y cárgalo al iniciar para evitar marcas de agua de evaluación.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Paso 2: Crear un documento en blanco y un DocumentBuilder

Un `Document` representa el archivo Word, mientras que `DocumentBuilder` proporciona una API fluida para insertar contenido.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:** El `DocumentBuilder` mantiene el punto de inserción actual, asegurando que el gráfico aparezca exactamente donde lo deseas en el flujo del documento.

## Paso 3: Insertar un gráfico circular en el documento Word

Ahora **insertamos un gráfico en Word**. El método `InsertChart` recibe el tipo de gráfico, el ancho y la altura (en puntos).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

En este punto el gráfico contiene una serie de datos predeterminada con valores de marcador de posición (25, 25, 25, 25). Puedes reemplazarlos más adelante si lo necesitas.

## Paso 4: Acceder a la primera serie y personalizar las etiquetas de datos

Un gráfico circular normalmente tiene una sola serie. Para **agregar etiquetas de datos al gráfico circular**, la recuperamos y habilitamos la visualización de porcentajes.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Por qué establecemos `ShowPercentage`:** Esta bandera indica a Aspose.Words que calcule la contribución de cada porción y la muestre como porcentaje. La propiedad `Position` garantiza que la etiqueta no se superponga a la porción, lo que mejora la legibilidad—especialmente cuando las porciones son pequeñas.

## Paso 5: (Opcional) Reemplazar los datos de marcador de posición

Si deseas valores específicos, reemplaza los puntos predeterminados:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Los porcentajes mostrados se ajustarán automáticamente para reflejar los nuevos valores.

## Paso 6: Guardar el documento

Finalmente, escribe el documento en disco. La extensión determina el formato; `.docx` crea un archivo Word moderno.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Ejecutar el programa genera un archivo llamado **PieChart.docx** en la carpeta de salida. Al abrirlo en Microsoft Word se muestra un gráfico circular con cada porción etiquetada con su porcentaje, posicionada fuera de las porciones.

### Resultado esperado

Al abrir el documento generado, deberías ver:

* Un único gráfico circular, de 400 × 300 pt de tamaño.  
* Cuatro secciones (o la cantidad de puntos que hayas añadido).  
* Etiquetas de porcentaje como “40 %”, “30 %”, etc., mostradas fuera de cada sección.

Si las etiquetas aparecen dentro de las porciones, verifica que `ChartDataLabelPosition.OutsideEnd` esté configurado correctamente.

## Paso 7: Variaciones comunes y casos límite

### Agregar un título al gráfico

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Cambiar colores de las secciones

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Manejar una serie vacía

Si tu fuente de datos podría estar vacía, protege contra `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exportar a PDF en lugar de Word

La misma lógica de renderizado del gráfico se aplica; Aspose.Words convierte automáticamente el diseño de Word a PDF.

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

## Listado completo del código fuente

A continuación se muestra el programa completo, listo para ejecutar. Cópialo en `Program.cs` y ejecuta `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusión

Ahora sabes cómo **crear un gráfico circular** en un archivo Word usando Aspose.Words, **insertar un gráfico en Word**, **agregar etiquetas de datos al gráfico circular**, y **mostrar porcentajes en el gráfico circular**. El ejemplo demuestra todo el flujo de trabajo—desde la configuración del proyecto hasta el documento final—para que puedas adaptarlo a paneles, informes o generación automática de facturas.

A continuación, explora temas relacionados como **cómo mostrar porcentajes en las leyendas del gráfico**, personalizar colores del gráfico o convertir el documento Word a PDF para su distribución. Experimenta con diferentes tipos de gráficos (Barra, Línea) usando el mismo método `InsertChart` para ampliar tus capacidades de automatización.

¡Feliz creación de gráficos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Crear gráfico de dispersión en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insertar gráfico de áreas en documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}