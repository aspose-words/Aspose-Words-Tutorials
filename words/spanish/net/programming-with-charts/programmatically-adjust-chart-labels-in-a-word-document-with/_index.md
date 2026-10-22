---
category: general
date: 2026-10-13
description: Aprende a ajustar programáticamente las etiquetas de los gráficos en
  un documento de Word usando C#. Esta guía cubre la manipulación de gráficos de Aspose.Words
  y la alineación de etiquetas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: es
lastmod: 2026-10-13
og_description: Ajusta programáticamente las etiquetas de los gráficos en un documento
  de Word usando C#. Sigue este tutorial completo para cambiar la ubicación de las
  etiquetas, la alineación y más.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Ajustar programáticamente las etiquetas de gráficos en Word – Guía paso
  a paso en C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Ajustar programáticamente las etiquetas del gráfico en un documento de Word
  con C#
url: /es/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajustar programáticamente las etiquetas de un gráfico en un documento Word con C#

Si necesitas **ajustar programáticamente las etiquetas de un gráfico** en un documento Word, esta guía te muestra exactamente cómo hacerlo con C#. Ya sea que estés generando informes, automatizando paneles o personalizando plantillas, verás un ejemplo completo y ejecutable que cambia la posición y alineación de las etiquetas de un gráfico dentro de un archivo .docx.

También aprenderás a usar técnicas de **manipulación de gráficos con Aspose.Words**, manejar series múltiples y evitar errores comunes al trabajar con objetos **C# chart data label**.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 (o posterior) instalado  
* Visual Studio 2022 (o cualquier IDE de C#)  
* El paquete NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Un documento Word (`input.docx`) que contenga al menos un gráfico  

Estos elementos son necesarios para el **ejemplo de gráfico en documento Word** que modificaremos.

## Paso 1: Configurar el proyecto e importar espacios de nombres

Crea un nuevo proyecto de consola y agrega las directivas `using` necesarias. Esto prepara el entorno para **ajustar programáticamente las etiquetas de un gráfico**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*¿Por qué este paso?*  
Cargar el documento te da acceso al árbol interno del **ejemplo de gráfico en documento Word**, donde los gráficos se almacenan como nodos de forma.

## Paso 2: Ubicar la primera forma de gráfico

Los gráficos se almacenan como nodos `Shape`. El siguiente código recupera el primer gráfico del documento, que es el objetivo de nuestros ajustes de etiquetas.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*¿Por qué este paso?*  
El método `GetChild` busca recursivamente (`true`) y devuelve el primer nodo de tipo `Shape`. Convertirlo a `Chart` nos permite trabajar con la API específica del gráfico.

## Paso 3: Acceder a la etiqueta de datos que deseas modificar

Cada serie en un gráfico tiene una colección de etiquetas de datos. Para un gráfico simple, la primera etiqueta suele ser suficiente. El código a continuación muestra cómo llegar a ella.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*¿Por qué este paso?*  
`ChartSeries` representa una serie de puntos. `DataLabelCollection` contiene las etiquetas de esa serie, lo que permite un control preciso sobre la posición y alineación.

## Paso 4: Cambiar la posición y alineación de la etiqueta

Ahora **ajustamos programáticamente las etiquetas del gráfico** estableciendo la posición, alineación horizontal y alineación vertical. Estas propiedades corresponden a las opciones que ves en la interfaz de Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*¿Por qué estas configuraciones?*  

* `OutsideEnd` coloca la etiqueta justo fuera del extremo de cada barra o columna, mejorando la legibilidad.  
* `HorizontalAlignment.Center` mantiene el texto centrado sobre el punto, mientras que `VerticalAlignment.Top` alinea el borde superior de la etiqueta con el punto de datos, evitando solapamientos con otros elementos.

### Consejo profesional
Si un gráfico tiene varias series, recorre `chart.Series` y aplica las mismas configuraciones a cada `DataLabelCollection`. Así garantizas una apariencia coherente en todo el gráfico.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Paso 5: Guardar el documento modificado

Después de ajustar las etiquetas, persiste los cambios en un nuevo archivo. Esto completa el proceso de **modificar la posición de la etiqueta del gráfico**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Al abrir `output.docx`, verás que cada etiqueta del gráfico se ha movido al extremo externo de su punto de datos, centrada horizontalmente y alineada en la parte superior verticalmente.

## Casos límite y variaciones

| Situación | Qué observar | Enfoque recomendado |
|-----------|--------------|---------------------|
| **Múltiples gráficos** en el mismo documento | `GetChild` solo devuelve el primer gráfico. | Usa `doc.GetChildNodes(NodeType.Shape, true)` para iterar sobre todas las formas de gráfico. |
| **Series sin etiquetas de datos** | `DataLabelCollection` puede estar vacía. | Verifica `series.HasDataLabels` antes de acceder a la colección. |
| **Tipos de gráfico diferentes** (circular, línea, dispersión) | No todos los valores de `DataLabelPosition` son válidos. | Usa `DataLabelPosition.Auto` para gráficos que deciden la mejor posición automáticamente. |
| **Localización** | Las constantes de alineación son independientes del idioma, pero el texto renderizado puede necesitar soporte de derecha a izquierda. | Establece `dataLabel.TextDirection` si necesitas idiomas RTL. |

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar, pegar y ejecutar. Sustituye `YOUR_DIRECTORY` por una ruta de carpeta real.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Resultado esperado:** Al abrir `output.docx` se muestra cada etiqueta del gráfico posicionada fuera del punto de datos, centrada horizontalmente y alineada en la parte superior—exactamente el efecto de **ajustar programáticamente las etiquetas de un gráfico** que has programado.

## Conclusión

Ahora sabes cómo **ajustar programáticamente las etiquetas de un gráfico** en un documento Word usando C#. El tutorial cubrió:

* Cargar un documento con **manipulación de gráficos de Aspose.Words**  
* Acceder a una **C# chart data label**  
* Cambiar la **posición y alineación de la etiqueta del gráfico**  
* Guardar el archivo y manejar casos límite comunes  

Desde aquí puedes explorar escenarios más avanzados, como personalizar fuentes de etiquetas, añadir formato condicional o actualizar varios gráficos en un proceso por lotes. Experimenta con las diferentes opciones de `DataLabelPosition` para encontrar el estilo que mejor se adapte a tus informes.

---

*¿Listo para mejorar tu canal de generación automática de informes? Prueba a añadir formatos numéricos personalizados a las etiquetas o exportar el gráfico como imagen para usarlo en PDFs.*


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye código completo y ejemplos funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}