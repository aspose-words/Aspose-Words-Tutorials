---
category: general
date: 2026-10-20
description: Crear gráfico de pastel en un documento Word usando Aspose.Words – guía
  paso a paso que muestra cómo establecer el color, separar una porción y guardar
  el documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: es
lastmod: 2026-10-20
og_description: Crear un gráfico circular en un documento de Word con Aspose.Words.
  Aprende a establecer el color, separar una porción y guardar el documento de Word
  en un único ejemplo ejecutable.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Crear un gráfico circular en un documento de Word – guía completa de C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Cómo crear un gráfico circular en un documento de Word con Aspose.Words
url: /es/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico circular en un documento Word con Aspose.Words

Si necesitas **crear un gráfico circular** dentro de un archivo Word, esta guía te muestra exactamente cómo hacerlo. Verás cómo establecer un color personalizado, “explotar” una porción para resaltarla y, finalmente, **guardar el documento Word** con el gráfico incrustado.

Generar gráficos de forma programática elimina los pasos manuales de abrir Word, insertar un gráfico y ajustar su apariencia. Al final de este tutorial tendrás una aplicación de consola C# completa y ejecutable que crea un gráfico circular, lo personaliza y escribe el resultado en disco.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado  
* Una licencia válida de Aspose.Words for .NET (o una clave de evaluación gratuita)  
* Un IDE como Visual Studio 2022 o VS Code  

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Cómo crear un gráfico circular en un documento Word

El primer paso es instanciar un `Document` y un `DocumentBuilder`. El builder te brinda acceso a funciones de alto nivel de Word, incluida la inserción de gráficos.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

En este punto el documento ya contiene un gráfico circular básico. Las siguientes secciones explican **cómo “explotar” una porción**, **cómo establecer el color** y **cómo guardar el documento Word**.

## Cómo “explotar” una porción para resaltarla

“Explotar” una porción la separa del resto del círculo, atrayendo la atención del lector. La API de Aspose.Words permite especificar una distancia de explosión en puntos.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

¿Por qué “explotar” la porción? En informes que resaltan una categoría particular —por ejemplo, “Producto más vendido”— la separación visual hace que el punto de datos sea instantáneamente reconocible.

## Cómo establecer el color en una porción del gráfico

Los colores personalizados mejoran la consistencia de marca y la legibilidad. Puedes asignar cualquier `System.Drawing.Color` a un punto de datos específico.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

No estás limitado a colores predefinidos; puedes crear un valor `Color.FromArgb` para obtener tonos precisos.

## Cómo guardar el documento Word con el gráfico

Una vez que el gráfico tiene el aspecto deseado, persistir el archivo es sencillo. El método `Document.Save` escribe el documento en el formato que especifiques; aquí usamos el predeterminado `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Al ejecutar el programa se crea `PieChart.docx`. Abrir el archivo en Microsoft Word muestra un gráfico circular donde la primera porción está “explotada” y coloreada de rojo, exactamente como indica el código.

### Resultado esperado

* Un archivo Word llamado **PieChart.docx** en `C:\Temp`.  
* El documento contiene un único gráfico circular, de 400 × 300 puntos de tamaño.  
* La porción 0 está desplazada 20 puntos y rellenada de rojo, mientras que las demás porciones conservan el color predeterminado.  

Puedes verificar la explosión y el color seleccionando el gráfico en Word y examinando las propiedades de la porción.

## Consejos profesionales y errores comunes

* **Consejo pro:** Si necesitas cambiar el título del gráfico o la leyenda, usa las propiedades `pieChart.Title.Text` y `pieChart.Legend` antes de guardar.  
* **Cuidado con:** Olvidar limpiar los puntos de datos predeterminados puede generar porciones extra e indeseadas. Siempre llama a `Series[0].DataPoints.Clear()` antes de añadir tus propios datos.  
* **Consejo de rendimiento:** Para documentos grandes, reutiliza una única instancia de `DocumentBuilder` en lugar de crear muchos builders; esto reduce la sobrecarga de memoria.

## Cómo crear un gráfico usando Aspose.Words (contexto adicional)

El método `InsertChart` admite muchos tipos de gráficos además de los circulares, como columnas, líneas y áreas. Para cambiar a otro tipo, reemplaza `ChartType.Pie` por el valor de enumeración deseado, por ejemplo, `ChartType.Column`. El resto de los pasos de personalización (explotar porciones, establecer colores) siguen el mismo patrón, aunque no todos los tipos de gráficos exponen una propiedad de “explosión”.

## Cómo “explotar” una porción en otros tipos de gráficos

Solo los gráficos de tipo circular exponen el método `SetExplosion`. Si intentas llamarlo en un gráfico de barras, la API lanza una `ArgumentException`. En esos casos, considera usar etiquetas de datos o llamadas de texto para resaltar una barra particular.

## Cómo establecer el color en una serie en lugar de una sola porción

Si deseas que todas las porciones de una serie compartan el mismo color, recorre los puntos de datos:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Este enfoque es útil cuando necesitas un esquema de color uniforme en varios gráficos.

## Cómo guardar el documento Word en otros formatos

Aspose.Words puede exportar a PDF, HTML y muchos otros formatos. Cambia la extensión del archivo en `Save` y, opcionalmente, pasa un objeto `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

El motor de renderizado del gráfico convierte automáticamente el gráfico al formato de destino, preservando colores y configuraciones de explosión.

## Conclusión

Ahora sabes cómo **crear un gráfico circular** en un documento Word, personalizar su apariencia **explotando una porción** y **estableciendo el color**, y finalmente **guardar el documento Word** con el gráfico incrustado. Este ejemplo de extremo a extremo te brinda una base sólida para automatizar la generación de informes, paneles de control o cualquier escenario donde se necesite insertar datos visuales de forma programática.

### Próximos pasos

* Explora otros tipos de gráficos (`ChartType.Column`, `ChartType.Line`) para ampliar tu conjunto de herramientas de informes.  
* Combina varios gráficos en un solo documento para crear paneles de control completos.  
* Experimenta con `ChartDataLabel` para mostrar porcentajes o valores directamente en las porciones.  

Siéntete libre de adaptar el código a tus propias fuentes de datos —ya sea que extraigas valores de una base de datos, una API o un archivo CSV— el mismo flujo de trabajo de Aspose.Words se aplica. ¡Feliz creación de gráficos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}