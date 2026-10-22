---
category: general
date: 2026-10-13
description: Cómo formatear un gráfico en Word con C# aplicando un formato numérico
  personalizado, como moneda, a los ejes del gráfico. Se incluye un ejemplo de código
  paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: es
lastmod: 2026-10-13
og_description: Cómo formatear un gráfico en Word con C# te permite aplicar un formato
  numérico personalizado a los ejes del gráfico, asegurando que los valores aparezcan
  como moneda, porcentajes o cualquier patrón que necesites. Sigue la guía paso a
  paso.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Cómo formatear un gráfico en Word con C# – formatos de número personalizados
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Cómo formatear un gráfico en Word con C# y formatos numéricos personalizados
url: /es/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo dar formato a un gráfico en Word con C# y formatos numéricos personalizados

Dar formato a un gráfico en Word con C# es un requisito común cuando necesitas presentar datos de forma profesional. Esta guía muestra cómo aplicar un formato numérico personalizado al eje de un gráfico usando **Aspose.Words for .NET**, de modo que los valores aparezcan exactamente como esperas.

Aprenderás a cargar un archivo DOCX, localizar el primer gráfico, leer el formato actual y luego establecer un nuevo patrón, como moneda con dos decimales. El tutorial también cubre cómo cambiar el formato del eje del gráfico para series adicionales y cómo restablecer el formato si es necesario.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior instalado  
* Un proyecto de Visual Studio 2022 (o cualquier IDE que soporte .NET)  
* El paquete NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Un documento de Word (`input.docx`) que contenga al menos un gráfico

Puedes agregar el paquete con el siguiente comando:

```bash
dotnet add package Aspose.Words
```

## Cómo dar formato a un gráfico en Word usando Aspose.Words

El siguiente programa completo demuestra cada paso necesario para **dar formato al eje** de un gráfico. Guarda el archivo como `Program.cs` y ejecútalo desde la línea de comandos o tu IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Explicación de cada paso

| Paso | Por qué es importante | Código clave |
|------|-----------------------|--------------|
| **Cargar el documento** | Necesita un objeto `Document` para trabajar con el archivo Word. | `new Document("input.docx")` |
| **Obtener el gráfico** | Los objetos `Chart` se almacenan como nodos `Shape`; el casting le permite usar APIs específicas de gráficos. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Acceder a los valores X** | El formato del eje se aplica a la colección de valores de una serie de datos. | `chart.ChartData.Series[0].XValues` |
| **Leer el formato actual** | Conocer el `FormatCode` existente le ayuda a decidir si reemplazarlo o ampliarlo. | `xValues.FormatCode` |
| **Establecer formato personalizado** | La propiedad `FormatCode` acepta cualquier patrón compatible con Excel, lo que permite moneda, porcentajes, fechas, etc. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Guardar el documento** | Persistir los cambios escribe el nuevo formato del eje de vuelta al archivo DOCX. | `doc.Save("output_formatted.docx")` |

Ejecutar el programa genera `output_formatted.docx`. Ábrelo en Word y verás los valores del eje X del gráfico mostrados como **$1,234.00**, **$2,345.00**, … en lugar de números simples.

## Aplicar formato numérico personalizado al eje del gráfico

Si necesitas **aplicar un formato numérico personalizado** al eje Y o a series adicionales, el proceso es idéntico; solo apunta a una colección diferente:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Consejo profesional:** Usa comillas dobles dentro de la cadena de formato para incrustar caracteres literales (p. ej., `"$"` para moneda). Escapa las comillas como se muestra arriba.

## Formato numérico personalizado en Word – manejo de la configuración regional de Word

Word respeta la configuración regional del documento al interpretar los formatos numéricos. Si el documento usa una configuración regional distinta a EE. UU., puede que necesites ajustar la cadena de formato:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Probar el formato en un documento con la configuración de idioma alemán confirma que los valores aparecen como **€ 1.234,00**.

## Cómo establecer propiedades del gráfico mediante código

Más allá del formato del eje, a menudo deseas **establecer** títulos, leyendas o etiquetas de datos del gráfico. Aquí tienes un fragmento rápido que muestra cómo establecer el título del gráfico después de haber formateado el eje:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Combinar esto con el formato numérico personalizado te brinda un gráfico completamente pulido listo para los informes.

## Cambiar el formato del eje del gráfico dinámicamente según la entrada del usuario

En aplicaciones del mundo real podrías permitir que los usuarios elijan un formato en tiempo de ejecución. El siguiente método encapsula la lógica de formateo:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Puedes llamar a `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` para moneda o `SetAxisFormat(chart, 0, "0%")` para porcentajes. Este enfoque mantiene tu código principal limpio y soporta futuras extensiones.

## Casos límite y errores comunes

| Situación | Qué observar | Solución sugerida |
|-----------|--------------|-------------------|
| El documento no contiene **ningún gráfico** | `GetChild` devuelve `null`, lo que provoca una excepción de conversión. | Verifique `null` antes de convertir (ver ejemplo). |
| Múltiples gráficos en el mismo documento | El código siempre toma el primer gráfico (`índice 0`). | Recorra `doc.GetChildNodes(NodeType.Shape, true)` y filtre por `ShapeType.Chart`. |
| Series **sin valores X** (p. ej., gráficos de pastel) | Acceder a `XValues` puede lanzar `ArgumentOutOfRangeException`. | Verifique que `Series[i].XValues` no esté vacío antes de formatear. |
| Desajuste de configuración regional | El símbolo de moneda puede aparecer incorrectamente. | Establezca explícitamente `xValues.FormatCode` con los símbolos de configuración regional apropiados. |

## Resultado esperado

Después de ejecutar el programa de ejemplo, abre **output_formatted.docx**. El eje X del gráfico debe mostrar los números en el formato personalizado elegido. Para el ejemplo de moneda, las etiquetas del eje se ven así:

```
$1,000.00
$2,000.00
$3,000.00
```

Si aplicaste el formato de porcentaje a los valores Y, las etiquetas del eje Y aparecen como:

```
10%
20%
30%
```

## Conclusión

Este tutorial te mostró **cómo dar formato a un gráfico** en Word con C# mediante **la aplicación de un formato numérico personalizado** a los valores del eje. Ahora dispones de un patrón reutilizable para establecer moneda, porcentajes o cualquier otro patrón numérico, así como de orientación para manejar configuraciones regionales, series múltiples y entrada dinámica del usuario.

A continuación, podrías explorar **cómo establecer** títulos, etiquetas de datos o incluso exportar el gráfico como imagen usando `ChartRenderer`. esos temas se basan directamente en los conceptos cubiertos aquí y te ayudarán a crear soluciones de informes totalmente automatizadas.

---

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Formato numérico para el eje en un gráfico](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Formato del número de etiqueta de datos en un gráfico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formato del eje X secundario y establecer unidades de visualización en miles en gráficos de líneas de Word usando Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}