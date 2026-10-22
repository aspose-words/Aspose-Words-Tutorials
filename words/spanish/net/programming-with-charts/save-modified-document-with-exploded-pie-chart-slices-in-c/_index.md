---
category: general
date: 2026-10-13
description: 'Guardar el documento modificado después de personalizar un gráfico circular:
  explotar las porciones, cambiar el ángulo de la primera porción y mostrar etiquetas
  de porcentaje en C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: es
lastmod: 2026-10-13
og_description: Guarda el documento modificado después de personalizar un gráfico
  circular en C#. Aprende cómo separar las porciones del gráfico, cambiar el ángulo
  de la primera porción y mostrar etiquetas de porcentaje.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Guardar documento modificado con secciones de gráfico de pastel separadas
  – Guía de C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Guardar documento modificado con porciones de gráfico circular explotadas en
  C#
url: /es/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Guardar documento modificado con porciones de gráfico circular explotadas en C#

Si necesitas **guardar documento modificado** después de ajustar un gráfico circular en Word, esta guía te muestra exactamente cómo hacerlo. Aprenderás a explotar las porciones del gráfico, cambiar el ángulo de la primera porción y mostrar etiquetas de porcentaje, todo con unas pocas líneas de código C#.

Personalizar gráficos es un requisito frecuente al generar informes, facturas o paneles de control de forma programática. Al final de este tutorial podrás cargar un archivo DOCX, modificar la apariencia del gráfico y **guardar documento modificado** listo para su distribución.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
- Aspose.Words para .NET 23.10 o más reciente (versión de prueba gratuita o copia con licencia)
- Un archivo Word (`input.docx`) que contenga un único gráfico circular
- Visual Studio 2022 o cualquier IDE de C#

> **Consejo:** El paquete NuGet de Aspose.Words se agrega con `dotnet add package Aspose.Words`.

## Paso 1: Cargar el documento Word que contiene el gráfico

El primer paso es abrir el archivo DOCX de origen. La clase `Document` representa todo el archivo Word en memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Cargar el documento te brinda acceso completo a cada nodo, incluidas las formas que alojan los gráficos.

## Paso 2: Obtener la primera forma de gráfico del documento

Los gráficos se almacenan dentro de nodos `Shape`. Puedes localizar el primer gráfico con `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Si el documento contiene varios gráficos, ajusta el índice (`0`) o recorre la colección. Esta línea garantiza que tengas una referencia al objeto `Chart` que vas a modificar.

## Paso 3: Explotar las porciones del gráfico circular

Explotar una porción la separa del resto del círculo, facilitando la lectura del gráfico. La propiedad `Explode` funciona para toda la serie.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Establecer `Explode` en `true` **explota porciones del gráfico circular** para toda la serie, lo cual es útil cuando deseas que cada porción destaque.

## Paso 4: Cambiar el ángulo de la primera porción

A veces necesitas que la primera porción comience en un ángulo personalizado, por ejemplo para alinearla con una guía de diseño.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

La propiedad `FirstSliceAngle` **cambia la primera porción**, rotando todo el círculo de modo que la primera porción empiece a 30 grados.

## Paso 5: Mostrar etiquetas de porcentaje en las porciones

Mostrar la contribución numérica de cada porción suele ser necesario en los informes. La bandera `DataLabel.ShowPercentage` activa los valores de porcentaje.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Este paso **muestra etiquetas de porcentaje** directamente en el gráfico, cumpliendo también con el requisito de **mostrar porcentajes en el gráfico**.

## Paso 6: Guardar el documento modificado

Una vez aplicadas todas las personalizaciones, persiste los cambios en un nuevo archivo. El método `Save` escribe el DOCX actualizado en disco.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Ahora tienes un **guardar documento modificado** que contiene un gráfico circular explotado, una primera porción rotada y etiquetas de porcentaje visibles.

![Guardar documento modificado mostrando gráfico circular explotado](/images/pie-chart-exploded.png "Guardar documento modificado con porciones de gráfico circular explotadas y etiquetas de porcentaje")

*La captura de pantalla ilustra el resultado final después de guardar el documento.*

## Ejemplo completo y ejecutable

Uniendo todas las piezas, aquí tienes el programa completo que puedes copiar‑pegar en un proyecto de consola:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Resultado esperado

Al abrir `output.docx` se mostrará un gráfico circular donde:

- Cada porción está ligeramente separada (**porciones de gráfico circular explotadas**)
- La primera porción comienza con un desplazamiento de 30 grados (**cambiar primera porción**)
- Cada porción muestra su contribución como porcentaje (**mostrar etiquetas de porcentaje**, **mostrar porcentajes en el gráfico**)
- El archivo ha sido **guardado documento modificado** sin alterar el original.

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué ocurre si el documento no tiene gráfico?** | El código verifica `null` después de `GetChild`. Si no existe ningún gráfico, puedes agregar uno programáticamente o abortar con un mensaje claro. |
| **¿Puedo explotar solo una única porción?** | Sí. Usa `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` donde `i` es el índice de la porción. |
| **¿Cómo cambio el formato de la etiqueta (p. ej., mostrar valor + %)?** | Configura `chart.PieChart.DataLabel.ShowValue = true;` y opcionalmente `chart.PieChart.DataLabel.ShowPercentage = true;` para combinar ambos. |
| **¿Se conserva el estilo del gráfico después de guardar?** | Aspose.Words mantiene todo el estilo, incluidos colores y fuentes, cuando **guardas documento modificado**. |
| **¿Puedo procesar varios gráficos en el mismo archivo?** | Recorre todos los nodos `Shape` con `NodeType.Shape` y filtra por `shape.HasChart`. Aplica los mismos pasos a cada gráfico. |

## Conclusión

Ahora sabes cómo **guardar documento modificado** después de personalizar programáticamente un gráfico circular en Word. La guía cubrió la explosión de porciones, el cambio del ángulo de la primera porción y la visualización de etiquetas de porcentaje, cumpliendo los requisitos de **mostrar etiquetas de porcentaje**, **explotar porciones del gráfico circular**, **mostrar porcentajes en el gráfico** y **cambiar primera porción**.

A continuación, considera explorar:

- Añadir series de datos dinámicamente (`chart.Series.Add(...)`)  
- Personalizar la ubicación de la leyenda y los títulos del gráfico  
- Convertir el DOCX a PDF manteniendo el estilo del gráfico  

¡Experimenta con diferentes ángulos, configuraciones de explosión o formatos de etiqueta para adaptarlos a tus necesidades de reporte! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos en tus propios proyectos.

- [How to Save Edited Document in C# with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}