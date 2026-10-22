---
category: general
date: 2026-09-05
description: Crear un gráfico de radar en Word usando C#. Aprende a generar un documento
  Word en blanco, agregar un gráfico de radar, establecer el tamaño del gráfico y
  habilitar las marcas de graduación rápidamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: es
lastmod: 2026-09-05
og_description: Crear un gráfico de radar en Word usando C#. Esta guía muestra cómo
  generar un documento Word en blanco, añadir un gráfico de radar, establecer el tamaño
  del gráfico y habilitar las marcas de graduación, todo en minutos.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Crear gráfico de radar en Word – guía paso a paso de C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Cómo crear un gráfico de radar y agregar el gráfico a Word con C#
url: /es/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico de radar y agregarlo a Word con C#

Si necesitas **crear un gráfico de radar** dentro de un archivo Word, esta guía te lleva paso a paso por todo el proceso. Aprenderás cómo **generar un documento Word en blanco**, insertar un gráfico de radar, **establecer el tamaño del gráfico en Word**, y habilitar las graduaciones del eje, todo con unas pocas líneas de código C#.

Agregar datos visuales a los informes es un requisito común, y usar Aspose.Words lo hace sencillo. En los pasos siguientes también cubrimos cómo **agregar un gráfico a Word** documentos programáticamente, para que puedas automatizar paneles, resúmenes financieros o cualquier contenido basado en datos.

## Requisitos previos

* .NET 6.0 o posterior instalado  
* Una licencia de Aspose.Words para .NET (o una prueba gratuita) – la biblioteca proporciona los APIs `Document`, `DocumentBuilder` y de gráficos usados en este tutorial  
* Visual Studio 2022 (o cualquier IDE de C#)  

> **Consejo profesional:** Si estás probando, coloca el DLL de Aspose.Words en la carpeta `bin` de tu proyecto y haz referencia a él mediante NuGet (`Install-Package Aspose.Words`).

## Cómo crear un gráfico de radar en un documento Word

El primer paso es **generar un documento Word en blanco** que alojará el gráfico. Esto te brinda un lienzo limpio y te permite controlar los metadatos del documento antes de que se añada cualquier contenido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Por qué es importante:* Un objeto `Document` vacío garantiza que no haya estilos o secciones ocultas que interfieran con el diseño del gráfico. También te permite establecer propiedades del documento (autor, título) más adelante si es necesario.

## Cómo agregar un gráfico a Word usando Aspose.Words

A continuación, crea un `DocumentBuilder`. El builder es la pieza clave que te permite insertar texto, imágenes y gráficos en el documento.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Ahora puedes **agregar un gráfico de radar** directamente donde está posicionado el cursor. El método `InsertChart` acepta un enum `ChartType`, ancho y alto en puntos.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*¿Por qué 400 × 300?* Estas dimensiones proporcionan un gráfico claro y legible en una página A4 estándar. Puedes ajustar el tamaño más adelante con el paso **establecer el tamaño del gráfico en Word** si tu diseño requiere una relación de aspecto diferente.

## Establecer el tamaño del gráfico en Word

Si necesitas afinar el tamaño después de la inserción, puedes modificar las propiedades `Width` y `Height` del gráfico. Esto es útil cuando el texto circundante o los márgenes de la página dictan un equilibrio visual diferente.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Nota:** La sobrecarga `InsertChart` ya establece el tamaño, por lo que el código anterior es opcional y se muestra para mayor claridad.

## Habilitar marcas de graduación en el eje radial

Un gráfico de radar es más útil cuando el eje radial muestra graduaciones claras. La siguiente configuración activa las marcas de graduación y establece el intervalo a 30 grados, lo que se alinea con las típicas pantallas de radar estilo brújula.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Por qué es importante:* Las graduaciones ayudan a los lectores a medir los valores en cada ángulo, mejorando la legibilidad para los interesados que no están familiarizados con los datos.

## Guardar el documento que contiene el gráfico

Finalmente, escribe el documento en disco. Puedes elegir cualquier carpeta que desees; solo asegúrate de que la ruta exista.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Cuando abras `RadialChart.docx` en Microsoft Word, verás un gráfico de radar completamente renderizado centrado en la página, con el tamaño especificado y marcas de graduación cada 30 grados.

### Resultado esperado

* Un archivo `.docx` llamado **RadialChart.docx**  
* La primera página contiene un gráfico de radar de tamaño 400 × 300 puntos  
* El eje X (eje radial) muestra marcas de graduación en 0°, 30°, 60°, …, 330°  

Ahora puedes reemplazar la serie de datos de marcador de posición con tus propios valores accediendo a `radarChart.Series`, pero eso está fuera del alcance de este tutorial básico de **agregar un gráfico de radar**.

## Variaciones comunes y casos límite

| Escenario | Ajuste |
|----------|------------|
| **Tipo de gráfico diferente** | Reemplaza `ChartType.Radar` con `ChartType.Column`, `ChartType.Pie`, etc. |
| **Múltiples gráficos** | Llama a `InsertChart` repetidamente; cada llamada posiciona el nuevo gráfico después del anterior. |
| **Conjuntos de datos grandes** | Usa `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` para poblar muchos puntos. |
| **Guardar como PDF** | Llama a `document.Save("RadialChart.pdf", SaveFormat.Pdf);` después de agregar el gráfico. |
| **Ejecutar en .NET Core** | Asegúrate de referenciar el paquete `Aspose.Words.NETCore`; el uso de la API es idéntico. |

## Ejemplo completo, ejecutable

A continuación se muestra el programa completo que puedes copiar y pegar en una aplicación de consola. Incluye todos los pasos, ajustes opcionales de tamaño y comentarios para mayor claridad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Ejecuta el programa, abre el archivo resultante y verás el gráfico de radar exactamente como se describe.

## Conclusión

Ahora sabes cómo **crear un gráfico de radar** y **agregar un gráfico a Word** documentos usando C#. El tutorial cubrió la generación de un **documento Word en blanco**, la inserción de un gráfico de radar, **establecer el tamaño del gráfico en Word**, y la habilitación de graduaciones del eje. Con esta base puedes ampliar la solución a múltiples gráficos, series de datos personalizadas o exportar a PDF.

### Próximos pasos

* Explora otros tipos de gráficos con `ChartType` (p. ej., `Bar`, `Line`) – consulta la palabra clave **add radar chart** para ejemplos relacionados.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques alternativos de implementación en tus propios proyectos.

- [Insertar gráfico de dispersión en documento Word](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Ocultar eje del gráfico en un documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}