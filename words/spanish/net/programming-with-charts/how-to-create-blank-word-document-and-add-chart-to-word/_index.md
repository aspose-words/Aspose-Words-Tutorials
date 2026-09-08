---
category: general
date: 2026-09-08
description: Crea un documento Word en blanco y agrega un gráfico a Word con Aspose.Words.
  Aprende cómo insertar un gráfico de radar, activar graduaciones y guardar el archivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: es
lastmod: 2026-09-08
og_description: Crear un documento Word en blanco y agregar un gráfico a Word usando
  Aspose.Words. Este tutorial muestra cómo insertar un gráfico de radar, configurar
  los ejes y guardar el documento.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Crea un documento de Word en blanco y agrega un gráfico de radar – guía
  paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Cómo crear un documento de Word en blanco y agregar un gráfico a Word
url: /es/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y agregar un gráfico a Word

Si necesitas **crear un documento Word en blanco** para un informe, plantilla o combinación de correspondencia automatizada, esta guía te lleva paso a paso por todo el proceso con C# y Aspose.Words. También aprenderás cómo **agregar un gráfico a Word**, específicamente cómo **insertar un gráfico de radar**, activar las graduaciones y guardar el resultado como un archivo .docx.

Este tutorial cubre todo, desde la configuración del proyecto hasta el paso final de verificación. Al final tendrás un fragmento de código reutilizable que puedes insertar en cualquier aplicación .NET. No se requiere experiencia previa con Aspose.Words, pero deberías tener conocimientos básicos de C# y un SDK reciente de .NET instalado.

## Prerrequisitos

- .NET 6.0 SDK o posterior  
- Aspose.Words for .NET (paquete NuGet `Aspose.Words`)  
- Un IDE como Visual Studio 2022 o VS Code  
- Permiso de escritura en la carpeta donde se guardará el documento  

Puedes instalar la biblioteca con el siguiente comando:

```bash
dotnet add package Aspose.Words
```

## Paso 1: Crear un documento Word en blanco

El primer paso es **crear un documento Word en blanco** en memoria. La clase `Document` representa todo el archivo, mientras que `DocumentBuilder` proporciona una API fluida para agregar contenido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` comienza vacío, por lo que tienes un lienzo limpio donde colocar el gráfico. Mantener el documento en blanco en esta etapa facilita reutilizar el mismo código para diferentes plantillas.

## Paso 2: Agregar un gráfico a Word

A continuación, **agregamos un gráfico a Word** llamando a `InsertChart`. El método requiere el tipo de gráfico y las dimensiones deseadas en puntos (1 punto = 1/72 de pulgada).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` indica a Aspose.Words que genere un gráfico radial, ideal para mostrar datos multivariados en un diseño circular. Los valores de tamaño (400 × 300) funcionan bien para la mayoría de las páginas en orientación vertical, pero puedes ajustarlos según tu diseño.

## Paso 3: Insertar gráfico de radar y configurar graduaciones

Ahora **insertamos el gráfico de radar** y habilitamos las graduaciones (marcas) tanto en el eje de categorías (X) como en el eje de valores (Y). Las graduaciones mejoran la legibilidad al mostrar posiciones exactas para cada punto de datos.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Establecer `HasGraduations` a `true` dibuja marcas en los ejes. El opcional `GraduationStep` controla el espacio entre marcas en el eje radial; un paso de 10 significa una marca cada 10 grados.

### Consejo profesional
Si necesitas mostrar etiquetas de datos, llama a `radarChart.Series[0].HasDataLabel = true;`. Esto agrega el valor numérico junto a cada punto, lo cual es útil para presentaciones.

## Paso 4: Poblar el gráfico con datos de ejemplo (opcional)

Un gráfico de radar sin datos es invisible. A continuación tienes una forma rápida de agregar una serie de valores de ejemplo. Puedes reemplazar este bloque con tu propia fuente de datos.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Cada llamada a `Add` inserta un punto en la serie. El orden de los puntos corresponde a las posiciones angulares alrededor del círculo.

## Paso 5: Guardar el documento que contiene el gráfico

Finalmente, almacena el documento en disco. El método `Save` escribe automáticamente el archivo .docx, preservando el gráfico y todo el formato.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Ejecutar el programa crea un **documento Word en blanco** que ahora contiene un gráfico de radar totalmente funcional. Abre el archivo en Microsoft Word para ver el resultado.

![Radar chart in Word document](radar_chart.png){alt="Gráfico de radar insertado en un documento Word en blanco"}

## Variaciones comunes y casos límite

| Situación | Qué cambiar |
|-----------|-------------|
| **Tamaño de gráfico diferente** | Ajusta los parámetros de ancho/alto de `InsertChart`. |
| **Otros tipos de gráfico** | Reemplaza `ChartType.Radar` por `ChartType.Column`, `ChartType.Pie`, etc., y mantén la misma lógica de graduaciones. |
| **Guardar en un flujo** | Usa `document.Save(Stream, SaveFormat.Docx)` |

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de área en un documento Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Crear gráfico de dispersión en Word usando Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insertar gráfico de columnas en Word usando Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}