---
category: general
date: 2026-10-13
description: Ejemplo de gráfico radial de Aspose.Words que muestra cómo habilitar
  graduaciones en un gráfico radial usando C# y Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: es
lastmod: 2026-10-13
og_description: Ejemplo de gráfico radial de Aspose.Words que muestra cómo habilitar
  graduaciones en un gráfico radial con C# y la última biblioteca 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Ejemplo de gráfico radial de Aspose.Words – habilitar graduaciones en C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Ejemplo de gráfico radial de Aspose.Words: habilitar graduaciones en C#'
url: /es/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ejemplo de gráfico radial de Aspose.Words: habilitar graduaciones en C#

Si está buscando un **aspose.words radial chart example**, ha llegado al lugar correcto. Este tutorial le guía paso a paso para activar las graduaciones en un gráfico radial usando la API Aspose.Words para .NET.

Los gráficos radiales son útiles para visualizar datos cíclicos como métricas de hora del día o tendencias estacionales. Por defecto, las graduaciones (las marcas de graduación alrededor del eje circular) están ocultas, lo que puede dificultar la lectura del gráfico. Habilitarlas es un cambio de una sola línea, pero necesita conocer el modelo de objetos correcto y la versión que admite la función.

En esta guía aprenderá a:

* Cargar un documento Word que ya contiene un gráfico radial.  
* Acceder a la forma del gráfico mediante la API de gráficos de Aspose.Words.  
* Activar la **visibilidad de graduaciones** (disponible a partir de **Aspose.Words versión 24.9**).  
* Guardar el documento modificado y verificar el resultado.

El código completo y ejecutable está incluido, para que pueda copiar‑pegarlo en un nuevo proyecto de consola y ver el efecto de inmediato.

![Ejemplo de gráfico radial de Aspose.Words con graduaciones](https://example.com/images/radial-chart-graduations.png "Ejemplo de gráfico radial de Aspose.Words mostrando graduaciones habilitadas")

## Requisitos previos

Antes de comenzar, asegúrese de contar con:

| Requisito | Por qué es importante |
|-------------|----------------|
| .NET 6.0 o posterior | Aspose.Words for .NET 24.9+ tiene como objetivo .NET Standard 2.0 y funciona en .NET 6+. |
| Aspose.Words for .NET **24.9** o más reciente | La propiedad `IsGraduationsVisible` se introdujo en la versión 24.9. Las versiones anteriores lanzarán una `MissingMemberException`. |
| Un documento Word (`RadialChart.docx`) que contenga un gráfico radial | El ejemplo manipula un gráfico existente; crear uno desde cero es un tema aparte. |
| Un IDE de C# (Visual Studio, Rider, VS Code) | Cualquier IDE que pueda compilar proyectos .NET funcionará. |
| Paquete NuGet `Aspose.Words` | Instálelo mediante `dotnet add package Aspose.Words --version 24.9.0` (o posterior). |

> **Consejo profesional:** Si no puede actualizar a la versión 24.9, aún puede modificar otras propiedades del gráfico, pero las graduaciones permanecerán ocultas porque la API no expone esa bandera.

## Ejemplo de gráfico radial de Aspose.Words – guía paso a paso

Las siguientes secciones dividen el proceso en pasos discretos y fáciles de seguir. Cada paso incluye el código exacto que necesita y una breve explicación del *por qué* del paso.

### Paso 1: Cargar el documento que contiene un gráfico radial

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Por qué es importante:**  
`Document` es el punto de entrada de la **API de gráficos Aspose.Words**. Carga el archivo DOCX en memoria, dándole acceso a cada nodo—párrafos, tablas y formas de gráficos. Si el archivo no se encuentra, `Document` lanza una `FileNotFoundException`, que debe manejarse en código de producción.

### Paso 2: Recuperar la primera forma de gráfico del documento

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Por qué es importante:**  
Los gráficos se almacenan como nodos `Shape`. El método `GetChild` con `NodeType.Shape` recorre el DOM y devuelve la primera forma coincidente. Convertirla a `Chart` le brinda acceso a propiedades específicas del gráfico, como `RadialChart`. La verificación de nulidad garantiza un error claro si el documento no contiene un gráfico, lo cual es un caso límite frecuente al reutilizar plantillas.

### Paso 3: Habilitar las graduaciones en el gráfico radial

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Por qué es importante:**  
`IsGraduationsVisible` controla las marcas de graduación alrededor del eje circular. Cuando se establece en `true`, el gráfico muestra las graduaciones, mejorando la legibilidad para quienes necesitan medir valores con precisión. La propiedad se encuentra bajo `RadialChart`, que es un subtipo de `Chart`. Si intenta usarla en un gráfico que no sea radial (por ejemplo, un gráfico de barras), la propiedad `RadialChart` será `null`, por lo que debe verificar el tipo de gráfico primero en escenarios más complejos.

#### Manejo de gráficos no radiales (opcional)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Esta protección hace que el código sea robusto cuando el documento de origen pueda contener diferentes tipos de gráficos.

### Paso 4: Guardar el documento modificado

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Por qué es importante:**  
Llamar a `Save` escribe el DOM en memoria de vuelta a un archivo .docx, persistiendo el cambio realizado en el gráfico. El archivo de salida puede abrirse en Microsoft Word, LibreOffice o cualquier visor que admita DOCX. Verá el gráfico radial con graduaciones visibles.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puede pegar en `Program.cs` de un proyecto de consola .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Resultado esperado

Al abrir `RadialChart_Graduations.docx` en Word, el gráfico radial mostrará marcas de graduación alrededor del eje circular, similar a la captura de pantalla mostrada anteriormente. El resto del gráfico (series de datos, leyenda, título) permanecerá sin cambios.

## Variaciones comunes y casos límite

| Situación | Solución |
|-----------|----------|
| **Versión antigua de Aspose.Words (< 24.9)** | Actualice al paquete NuGet más reciente. La propiedad `IsGraduationsVisible` no existe en versiones anteriores. |
| **Múltiples gráficos en el mismo documento** | Use `doc.GetChild(NodeType.Shape, index, true)` con el `index` apropiado o itere sobre `doc.GetChildNodes(NodeType.Shape, true)` y filtre por `ChartType.Radial`. |
| **Gráfico creado programáticamente** | Use `DocumentBuilder` para insertar un gráfico, luego establezca `RadialChart.IsGraduationsVisible` en el |

## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Actualizar datos de series de gráfico en un documento Word usando Aspose.Words para .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Eliminar una serie de gráfico de un documento Word usando Aspose.Words para .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Ocultar el borde del área de trazado en un gráfico de columnas con Aspose.Words para .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}