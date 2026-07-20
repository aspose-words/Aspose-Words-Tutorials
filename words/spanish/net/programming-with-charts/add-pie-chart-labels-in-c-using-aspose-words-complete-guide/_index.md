---
category: general
date: 2026-07-20
description: Agregue etiquetas de gráfico circular con Aspose.Words para .NET. Aprenda
  cómo cambiar las etiquetas del gráfico circular, mostrar etiquetas de porcentaje
  y actualizar rápidamente las etiquetas de las series del gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: es
lastmod: 2026-07-20
og_description: Agrega etiquetas de gráfico circular en C# con Aspose.Words. Domina
  el cambio de etiquetas de gráficos circulares, muestra etiquetas de porcentaje y
  actualiza las etiquetas de series del gráfico en solo unos pocos pasos.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Agregar etiquetas de gráfico circular en C# – Tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Agregar etiquetas de gráfico circular en C# usando Aspose.Words – Guía completa
url: /es/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Añadir etiquetas a gráficos de pastel en C# con Aspose.Words – Guía completa

¿Necesitas **añadir etiquetas a un gráfico de pastel** en un documento Word usando C#? Con Aspose.Words puedes **cambiar las etiquetas de los gráficos de pastel** y **mostrar los porcentajes** directamente en el archivo, sin necesidad de ajustes manuales en Word.  

En este tutorial recorreremos paso a paso los pasos exactos para **mostrar etiquetas de porcentaje**, reposicionarlas e incluso **actualizar las etiquetas de serie del gráfico** para datos dinámicos. Al final tendrás un fragmento reutilizable que podrás insertar en cualquier proyecto .NET.

> **Vista previa rápida:** Después de seguir la guía, al abrir el `.docx` guardado verás un gráfico de pastel donde cada porción está etiquetada con su porcentaje, posicionado fuera de la porción para una máxima legibilidad.

---

## Lo que necesitarás

- **Aspose.Words for .NET** (la última versión a partir de 2026). Puedes obtenerlo desde NuGet: `Install-Package Aspose.Words`.
- Un **documento Word** que ya contenga un gráfico de pastel o de rosquilla (lo llamaremos `Chart.docx`).
- Familiaridad básica con **C#** y Visual Studio (o tu IDE favorito).

Eso es todo—sin bibliotecas adicionales, sin interop COM, solo código gestionado puro.

---

## Añadir etiquetas a gráficos de pastel – Implementación completa

A continuación tienes un programa de consola **completo y ejecutable** en C# que carga un documento, modifica el primer gráfico de pastel y guarda el resultado. Cada línea está comentada para que comprendas **por qué** hacemos lo que hacemos, no solo **qué** hacemos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Resultado esperado

Abre `ChartWithCustomLabels.docx` en Microsoft Word. Deberías ver el gráfico de pastel **con etiquetas de porcentaje posicionadas fuera de cada porción**. Las etiquetas se verán algo así como “35 %”, “20 %”, etc., haciendo que el gráfico sea instantáneamente comprensible.

---

## Cambiar etiquetas de gráficos de pastel: posicionamiento y formato

Si solo necesitas **cambiar las etiquetas de un gráfico de pastel** sin mostrar porcentajes, puedes ajustar la propiedad `Position` a una de las siguientes:

| Position Enum | Efecto visual |
|---------------|---------------|
| `InsideEnd`   | Las etiquetas quedan dentro de la porción, justo en el borde. |
| `Center`      | Las etiquetas aparecen en el centro de la porción (útil para pasteles pequeños). |
| `OutsideEnd`  | Las etiquetas están fuera de la porción, conectadas con una línea guía (nuestro valor predeterminado). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Consejo profesional:** `OutsideEnd` funciona mejor cuando el gráfico tiene muchas porciones; evita que el texto se superponga.

---

## Mostrar etiquetas de porcentaje en un gráfico de pastel

La propiedad `ShowPercentage` es una **bandera booleana**. Establecerla en `true` indica a Aspose.Words que calcule la contribución de cada porción basada en la fuente de datos subyacente.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

También puedes combinarla con `ShowValue` si necesitas tanto los números crudos **como** los porcentajes:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Cuando ambas banderas están activadas, la etiqueta se muestra como “45 % (120)”.

---

## Actualizar etiquetas de serie del gráfico para datos dinámicos

Con frecuencia generarás gráficos sobre la marcha—piensa en ventas mensuales o resultados de encuestas. Para **actualizar las etiquetas de serie del gráfico** programáticamente, modifica la colección `Series` antes de tocar las etiquetas de datos:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Este fragmento muestra cómo **actualizar las etiquetas de serie del gráfico** para cualquier serie, no solo la primera. Es útil cuando construyes informes que combinan datos reales y pronósticos.

---

## Casos límite y errores comunes

| Situación | Qué vigilar | Solución |
|-----------|-------------|----------|
| **El gráfico no es de pastel/rosquilla** | `Position` puede no tener efecto visual. | Verifica que `chart.Type` sea `ChartType.Pie` o `ChartType.Doughnut`. |
| **No se encontró ningún gráfico** | `GetChild` devuelve `null`. | Añade una cláusula de protección (ver código) y registra un mensaje útil. |
| **Versión antigua de Word** | Algunas funciones de etiqueta se ignoran. | Guarda como `.docx` (formato moderno) para garantizar soporte completo. |
| **Gran número de porciones** | Las etiquetas pueden superponerse incluso con `OutsideEnd`. | Considera reducir el número de porciones o aumentar el tamaño del gráfico. |

---

## Ejemplo completo (Copiar‑pegar)

A continuación tienes el **programa entero** que puedes copiar en un nuevo proyecto de consola. Solo reemplaza `YOUR_DIRECTORY` con la carpeta que contiene `Chart.docx`.



## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos en tus propios proyectos.

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}