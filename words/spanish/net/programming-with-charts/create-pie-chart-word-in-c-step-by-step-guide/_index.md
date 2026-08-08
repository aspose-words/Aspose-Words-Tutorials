---
category: general
date: 2026-08-07
description: Crear rápidamente un gráfico circular en Word con C#. Aprende cómo insertar
  un gráfico circular, agregar etiquetas de datos al gráfico, mostrar el porcentaje
  del gráfico y personalizar las etiquetas de datos del gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: es
lastmod: 2026-08-07
og_description: Crear gráfico circular en Word con C# y Aspose.Words. Este tutorial
  muestra cómo insertar un gráfico circular, agregar etiquetas de datos al gráfico
  y mostrar el porcentaje del gráfico mientras se personalizan las etiquetas de datos.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Crear gráfico de pastel en C# – tutorial completo
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Crear gráfico de pastel en C# – guía paso a paso
url: /es/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear gráfico circular en Word con C# – guía paso a paso

Si necesitas **crear gráficos circulares en documentos Word** con C#, esta guía ofrece una solución completa y lista para ejecutar. Verás cómo **insertar un gráfico circular**, **añadir etiquetas de datos al gráfico circular** y **mostrar el porcentaje en el gráfico** mientras **personalizas las etiquetas de datos del gráfico** para obtener un aspecto pulido.

Generar gráficos de forma programática te ahorra la edición manual, especialmente cuando los informes o paneles deben producirse automáticamente. En las secciones siguientes aprenderás todo lo necesario para incrustar un gráfico circular totalmente etiquetado en un archivo Word usando Aspose.Words para .NET.

## Requisitos previos y configuración

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado.  
* Una licencia válida de Aspose.Words para .NET (o una clave de evaluación temporal).  
* Visual Studio 2022 (o cualquier IDE que admita C#).  

Agrega el paquete NuGet Aspose.Words a tu proyecto:

```bash
dotnet add package Aspose.Words
```

> **Consejo profesional:** Si planeas generar muchos gráficos, habilita el modo **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) para obtener mejor rendimiento.

## Crear gráfico circular en Word con Aspose.Words

El primer paso importante es crear un documento Word en blanco y un `DocumentBuilder`. Este objeto controla todas las inserciones posteriores.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué es importante*: `Document` representa todo el archivo `.docx`, mientras que `DocumentBuilder` proporciona una API fluida para añadir párrafos, tablas y gráficos. Comenzar con un documento limpio garantiza que no haya formato oculto que interfiera con el diseño del gráfico.

## Insertar gráfico circular en el documento

Ahora colocamos un gráfico circular del tamaño deseado. El método `InsertChart` devuelve un objeto `Chart` que podemos configurar más adelante.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Por qué es importante*: La bandera `ChartType.Pie` indica a Aspose.Words que genere un gráfico circular. El ancho (`400`) y la altura (`300`) se expresan en puntos, dándote un control preciso sobre la huella visual.

## Poblar el gráfico con datos

Un gráfico circular necesita al menos una serie de valores numéricos. Aquí añadimos tres categorías: “Apples”, “Bananas” y “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Por qué es importante*: Cada llamada a `AddCategory` crea una porción. El valor numérico determina el tamaño de la porción, mientras que la etiqueta se convierte en el nombre de la categoría que se muestra cuando se activan las etiquetas de datos.

## Añadir etiquetas de datos al gráfico circular y mostrar porcentaje

Para que el gráfico sea informativo, habilitamos las etiquetas de datos, las posicionamos fuera de las porciones y solicitamos a Aspose.Words que muestre tanto el nombre de la categoría como el porcentaje.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Por qué es importante*: Establecer `Position` a `OutsideEnd` mejora la legibilidad, especialmente cuando las porciones son pequeñas. Habilitar `ShowCategoryName` y `ShowPercentage` cumple con el requisito de **mostrar porcentaje en el gráfico** y satisface el objetivo de **añadir etiquetas de datos al gráfico circular**.

## Personalizar más las etiquetas de datos del gráfico (opcional)

Puede que desees cambiar la fuente, añadir una línea guía o ocultar la leyenda. El siguiente fragmento muestra personalizaciones comunes:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Por qué es importante*: Personalizar la apariencia de la etiqueta asegura que el gráfico coincida con la guía de estilo de tu documento. Eliminar la leyenda reduce el desorden visual cuando las etiquetas de datos ya transmiten la misma información.

## Guardar el documento con el gráfico personalizado

Finalmente, escribe el documento en disco. Elige una ruta a la que tengas permisos de escritura.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Al abrir `ChartWithCustomLabels.docx` en Microsoft Word, verás un gráfico circular donde cada porción está etiquetada con su nombre de categoría y porcentaje, posicionada fuera de la porción y con la fuente personalizada.

### Resultado esperado

| Porción | Valor | Porcentaje | Etiqueta mostrada en Word |
|---------|-------|------------|---------------------------|
| Apples  | 40    | 40 %       | Apples – 40 %             |
| Bananas | 35    | 35 %       | Bananas – 35 %            |
| Cherries| 25    | 25 %       | Cherries – 25 %           |

El gráfico debería verse similar a la ilustración a continuación:

![Documento Word que muestra un gráfico circular con etiquetas de porcentaje fuera de cada porción](pie-chart-word.png "Ejemplo de crear gráfico circular en Word")

*El texto alternativo de la imagen incluye la palabra clave principal para SEO.*

## Manejo de múltiples series y casos límite

El ejemplo básico usa una sola serie, lo cual es típico para un gráfico circular. Si necesitas mostrar varias series (p. ej., comparando dos años), debes:

1. Llamar a `chart.Series.Add()` para cada serie adicional.  
2. Asegurarte de que cada serie use las mismas categorías; de lo contrario, Aspose.Words lanzará una `ArgumentException`.  
3. Opcionalmente, establecer `labels.ShowSeriesName = true` para diferenciar las porciones.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Cuando existen múltiples series, el gráfico se renderiza automáticamente como un **pie agrupado** (también llamado “pie of pies”). Revisa el resultado para verificar que las etiquetas sigan siendo legibles.

## Problemas comunes y cómo evitarlos

| Problema | Causa | Solución |
|----------|-------|----------|
| Las etiquetas se superponen a las porciones | Área del gráfico pequeña o muchas categorías | Aumenta las dimensiones del gráfico (`InsertChart(width, height)`) o cambia `Position` a `InsideEnd`. |
| Los porcentajes no suman 100 % | Errores de redondeo en los datos | Usa `labels.ShowPercentage = true` (Aspose.Words normaliza automáticamente). |
| El gráfico aparece en blanco en Word | Licencia faltante o tiempo de evaluación expirado | Asegúrate de cargar una licencia válida de Aspose.Words antes de crear el documento. |
| Los colores de fuente difieren del tema de Word | Fuente personalizada establecida en el código | Elimina la configuración de fuente personalizada o iguala los colores del tema de Word (`System.Drawing.Color.Black`). |

## Código fuente completo (ejecutable)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Ejecutar el programa genera `ChartWithCustomLabels.docx`, que contiene un ejemplo de **crear gráfico circular en Word** que cumple con todos los requisitos listados en el tutorial.

## Conclusión

Ahora sabes cómo **crear gráficos circulares en documentos Word** con C# usando Aspose.Words. La guía cubrió la inserción de un gráfico circular, **añadir etiquetas de datos al gráfico circular**, **mostrar porcentaje en el gráfico** y **personalizar las etiquetas de datos del gráfico** para lograr un archivo Word profesional y basado en datos.  

A partir de aquí puedes explorar temas relacionados como **insertar gráfico circular** en párrafos existentes, generar gráficos de **barras** o **líneas**, o automatizar la creación por lotes de informes con diferentes conjuntos de datos. Experimenta con distintas posiciones de etiquetas, estilos de fuente y configuraciones de series múltiples para adaptar la salida a tus necesidades específicas de reporte.

¡Feliz creación de gráficos!


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Personalizar etiqueta de datos del gráfico](/words/english/net/programming-with-charts/chart-data-label/)
- [Establecer opciones predeterminadas para etiquetas de datos en un gráfico](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insertar gráfico de columnas en un documento Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}