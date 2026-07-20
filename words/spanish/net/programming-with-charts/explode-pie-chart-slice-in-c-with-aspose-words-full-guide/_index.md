---
category: general
date: 2026-07-19
description: Explotar una porción de gráfico circular usando Aspose.Words para C#.
  Aprende cómo explotar una porción de pastel, ajustar el tamaño del agujero del donut
  y cambiar rápidamente los puntos de datos del gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: es
lastmod: 2026-07-19
og_description: Explota una porción de gráfico circular con Aspose.Words para C#.
  Esta guía te muestra cómo explotar una porción de pastel, ajustar el tamaño del
  agujero del donut y cambiar los puntos de datos del gráfico de manera eficiente.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Separar porción de gráfico circular en C# – Tutorial de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Separar porción de gráfico de pastel en C# con Aspose.Words – Guía completa
url: /es/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rebanada de Gráfico de Tarta Explosiva en C# con Aspose.Words – Guía Completa

¿Alguna vez te has preguntado cómo **explotar una rebanada de gráfico de tarta** en un documento Word usando C#? No eres el único. Ya sea que estés preparando una presentación de ventas o visualizando resultados de una encuesta, una rebanada explotada puede atraer la atención exactamente donde la necesitas. En este tutorial recorreremos todo el proceso: cargar un documento, obtener el gráfico, explotar la primera rebanada, ajustar el agujero de un gráfico de rosquilla y, incluso, cambiar los puntos de datos del gráfico.

También incluiremos los conceptos secundarios que podrías estar buscando: **cómo explotar una rebanada de tarta**, **ajustar el tamaño del agujero de la rosquilla** y **cambiar los puntos de datos del gráfico**. Sin rodeos, solo una solución completa lista para copiar y pegar.

---

## Qué Necesitarás

Antes de comenzar, asegúrate de tener:

- **Aspose.Words for .NET** (la última versión a fecha de 2026‑07‑19). Puedes obtenerlo desde NuGet con `Install-Package Aspose.Words`.
- Un proyecto **.NET 6+** (o .NET Framework 4.7.2+ si aún trabajas con la versión heredada).
- Un archivo Word (`Chart.docx`) que ya contenga un gráfico de tarta o rosquilla. Si no tienes uno, crea un gráfico rápido en Word y guárdalo.

Eso es todo: sin bibliotecas adicionales, sin interop COM, solo código administrado puro.

---

## Explode Pie Chart Slice – Implementación Paso a Paso

A continuación dividimos la tarea en pasos manejables. Cada sección tiene un encabezado claro, un fragmento de código y una breve explicación del *por qué* hacemos lo que hacemos.

### Paso 1: Instalar y Referenciar Aspose.Words

Lo primero, agrega el paquete Aspose.Words a tu proyecto. En la Consola del Administrador de Paquetes:

```powershell
Install-Package Aspose.Words
```

> **Consejo profesional:** Si utilizas la UI de NuGet integrada en Visual Studio, busca “Aspose.Words” y pulsa Instalar. Así obtienes las últimas correcciones y la capacidad de trabajar con gráficos directamente.

### Paso 2: Cargar el Documento Word que Contiene el Gráfico

Necesitamos un objeto `Document` que apunte al `.docx` con el gráfico que deseas modificar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Por qué es importante:** `Document` es el punto de entrada para cualquier operación en Aspose.Words. Al comprobar la existencia de gráficos al principio, evitamos una referencia nula más adelante cuando intentemos explotar una rebanada.

### Paso 3: Obtener el Primer Nodo de Gráfico

La mayoría de los ejemplos asumen un solo gráfico, así que tomaremos el primero. Si tienes varios gráficos, ajusta el índice según corresponda.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Nota:** El casting a `Chart` es seguro después de haber confirmado que existe un gráfico. Este objeto nos brinda acceso a series, puntos de datos y configuraciones específicas del tipo de gráfico.

### Paso 4: Explotar la Primera Rebanada de un Gráfico de Tarta

Ahora lo más importante—**cómo explotar una rebanada de tarta**. Estableceremos la propiedad `Exploded` del primer punto de datos.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Por qué funciona:** `Exploded` indica a Word que aleje esa rebanada del centro, creando el clásico efecto de “tarta explotada”. La propiedad es booleana, por lo que asignarle `true` logra el objetivo.

### Paso 5: Ajustar el Tamaño del Agujero de la Rosquilla (Si es un Gráfico de Rosquilla)

Si tu gráfico resulta ser una rosquilla, quizá quieras **ajustar el tamaño del agujero de la rosquilla**. El tamaño del agujero es un porcentaje del radio del gráfico.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Qué significa el número:** Un valor de `30` indica que el círculo interior ocupará el 30 % del radio total, dejando un anillo exterior más grueso.

### Paso 6: Cambiar los Puntos de Datos del Gráfico (Opcional)

A veces necesitas **cambiar los puntos de datos del gráfico**—tal vez hayas actualizado los números subyacentes y quieras que el visual los refleje.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Por qué hacerlo:** Cambiar el valor de un punto de datos recalcula automáticamente los porcentajes de las rebanadas, manteniendo el gráfico preciso sin necesidad de editar manualmente en Word.

### Paso 7: Guardar el Documento Modificado

Finalmente, escribe los cambios en disco. Puedes sobrescribir el archivo original o crear uno nuevo—tú decides.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Consejo:** Usa `SaveFormat.Docx` si necesitas ser explícito, pero `Save(string)` detecta automáticamente el formato a partir de la extensión del archivo.

---

## Resultado Esperado

Al abrir `FormattedChart.docx` en Microsoft Word, deberías ver:

- La primera rebanada de un gráfico de tarta **explotada** hacia afuera.
- Si el gráfico es una rosquilla, el agujero central ahora ocupa **30 %** del radio.
- Cualquier punto de datos modificado refleja los nuevos valores que estableciste.

A continuación tienes una maqueta de cómo se ve la rebanada explotada (imagen solo a modo ilustrativo).

![rebanada de gráfico de tarta explotada creada con Aspose.Words en C#](exploded-pie-slice.png)

*Texto alternativo:* **rebanada de gráfico de tarta explotada** que muestra un segmento alejado en un documento Word.

---

## Preguntas Frecuentes y Casos Especiales

**¿Qué pasa si el gráfico no es de tarta ni rosquilla?**  
El código verifica `ChartType` antes de aplicar `Exploded` o `HoleSize`. Para gráficos de barras, líneas o áreas esas propiedades simplemente no existen, por lo que la lógica las omite de forma segura.

**¿Puedo explotar varias rebanadas?**  
Claro. Recorre `chart.PieChartData.Series[0].DataPoints` y asigna `Exploded = true` a cualquier índice que desees.

**¿Debo preocuparme por formatos numéricos específicos de cultura?**  
Aspose.Words almacena los valores numéricos como `double`, independiente de la configuración regional, así que no tendrás problemas con comas vs puntos.

**¿Qué ocurre con los gráficos incrustados en encabezados/pies de página?**  
Utiliza `doc.GetChildNodes(NodeType.Chart, true)` para obtener todos los gráficos, luego inspecciona `ParentNode` de cada nodo para ver dónde está ubicado. La misma lógica de explosión se aplica.

---

## Conclusión

Ahora dispones de una solución completa, lista para copiar y pegar, sobre **cómo explotar una rebanada de gráfico de tarta** usando Aspose.Words en C#. Cubrimos todo el flujo de trabajo: cargar el documento, obtener el gráfico, explotar la rebanada, **ajustar el tamaño del agujero de la rosquilla**, **cambiar los puntos de datos del gráfico** y, finalmente, guardar el archivo.

Siéntete libre de experimentar: prueba a explotar otra rebanada, ajusta el tamaño del agujero al 45 %, o actualiza varios puntos de datos a la vez. La API de Aspose.Words hace que estos ajustes sean sencillos, y los cambios aparecen instantáneamente al abrir el archivo Word.

---

### ¿Qué Sigue?

- **Estilizar la rebanada explotada** (cambiar color de relleno, borde o añadir una etiqueta de datos). Busca “Aspose.Words chart formatting”.
- **Automatizar el procesamiento por lotes** de múltiples documentos—recorre una carpeta, explota rebanadas y guarda nuevas versiones.
- **Combinar con Aspose.Slides** si necesitas el mismo gráfico en una presentación de PowerPoint.

¿Tienes más preguntas sobre la manipulación de gráficos, o quieres profundizar en otros tipos de gráficos? Deja un comentario abajo, ¡y feliz codificación!

## ¿Qué Deberías Aprender a Continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos en tus propios proyectos.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}