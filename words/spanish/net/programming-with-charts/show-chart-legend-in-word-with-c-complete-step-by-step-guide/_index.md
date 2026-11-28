---
category: general
date: 2026-06-02
description: Mostrar la leyenda del gráfico en un documento de Word usando C#. Aprende
  a agregar la leyenda, aplicar un estilo de gráfico predefinido y personalizar los
  elementos visuales del gráfico de Word en minutos.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: es
og_description: Mostrar la leyenda del gráfico en un documento de Word al instante.
  Esta guía te guía paso a paso para agregar una leyenda, aplicar un estilo de gráfico
  predefinido y manejar casos especiales.
og_title: Mostrar la leyenda del gráfico en Word – Tutorial completo de C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Mostrar la leyenda del gráfico en Word con C# – Guía completa paso a paso
url: /es/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mostrar la leyenda del gráfico en Word con C# – Guía completa paso a paso

¿Alguna vez te has preguntado **cómo agregar una leyenda** a un gráfico que está dentro de un documento de Word? No eres el único. En muchos informes, una leyenda ausente hace que los datos parezcan crípticos, y corregirlo no debería ser un dolor de cabeza.  

En este tutorial **mostraremos la leyenda del gráfico** en un archivo de Word usando Aspose.Words for .NET, aplicaremos un estilo de gráfico predefinido y nos aseguraremos de que la leyenda aparezca exactamente donde la necesites. Al final tendrás un ejemplo listo para ejecutar que podrás insertar en cualquier proyecto C#.

## Qué cubre esta guía

Recorreremos todo el flujo de trabajo:

1. Cargar un *.docx* existente que ya contiene un gráfico.  
2. Obtener el primer gráfico (o cualquier gráfico que apunte).  
3. **Aplicar un estilo de gráfico predefinido** para darle al visual un aspecto profesional.  
4. **Mostrar la leyenda del gráfico**, posicionarla a la derecha y manejar casos especiales como los gráficos de cascada.  
5. Guardar el documento modificado.

Sin herramientas externas, sin manipular manualmente la interfaz—solo código puro. El único requisito previo es una referencia al paquete NuGet Aspose.Words (versión 23.10 o posterior) y una comprensión básica de C#.

---

## Requisitos previos

- .NET 6.0 o posterior (el ejemplo también funciona con .NET Framework 4.7.2).  
- Biblioteca Aspose.Words for .NET instalada (`Install-Package Aspose.Words`).  
- Un archivo de Word (`input.docx`) que ya contiene al menos un gráfico.  
- Visual Studio, Rider o cualquier IDE que prefieras.

---

## Paso 1: Configurar el proyecto y cargar el documento

Primero, crea una aplicación de consola (o integra el código en un proyecto existente). Añade las directivas `using` y carga el archivo `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Por qué es importante:** Cargar el documento es la base. Sin una instancia de `Document` no puedes acceder a los objetos de gráfico que expone Aspose.Words.

---

## Paso 2: Obtener el gráfico objetivo

Los gráficos se almacenan como nodos dentro del árbol del documento. El método `GetChild` realiza una búsqueda profunda, permitiéndonos obtener el primer gráfico sin importar dónde se encuentre (encabezado, cuerpo, pie de página, etc.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Consejo:** Si tienes varios gráficos, cambia el índice `0` a `1`, `2`, … o itera a través de `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Paso 3: Aplicar un estilo visual predefinido

Un gráfico atractivo suele comenzar con un estilo. Aspose.Words incluye docenas de estilos incorporados; `ChartStyle.Style12` es una opción limpia y moderna.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Cómo funciona:** La propiedad `Style` se corresponde con los estilos de gráfico de Word incorporados que ves en la interfaz. Elegir un preajuste te ahorra configurar manualmente colores, fuentes y marcadores.

---

## Paso 4: Habilitar la leyenda y posicionarla

Ahora, la estrella del espectáculo—**mostrar la leyenda del gráfico**. Activamos la leyenda y luego la anclamos al lado derecho del gráfico.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **¿Por qué a la derecha?** Colocar la leyenda a la derecha mantiene el área de datos amplia, lo que es especialmente útil para gráficos de barras o columnas.

---

## Paso 5: Manejar gráficos de cascada (caso especial)

Los gráficos de cascada se comportan de forma un poco diferente; la leyenda puede estar oculta por defecto. La siguiente cláusula de protección garantiza que la leyenda sea visible cuando el tipo de gráfico es Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Nota de caso límite:** Algunas versiones antiguas de Word ignoran `HasLegend` para los gráficos de cascada, por lo que establecer explícitamente `Legend.Show` garantiza la visibilidad.

---

## Paso 6: Guardar el documento modificado

Finalmente, escribe los cambios de vuelta al disco. Puedes sobrescribir el archivo original o crear uno nuevo.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Ejecutar el programa generará `output.docx` con una leyenda visible a la derecha, con el estilo `Style12`. Abre el archivo en Word para verificar el resultado.

---

## Ejemplo completo (todos los pasos combinados)

A continuación se muestra el código completo, listo para ejecutar. Copia y pega en `Program.cs` (o cualquier archivo C#) y ajusta las rutas de los archivos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Salida esperada:** Al abrir `output.docx` se muestra el gráfico original con una leyenda alineada a la derecha, con el estilo moderno `Style12`. Todas las series de datos están claramente etiquetadas, lo que hace que el gráfico sea instantáneamente comprensible.

---

## Preguntas frecuentes (FAQ)

### ¿Cómo agregar una leyenda a un gráfico específico (no al primero)?

Reemplaza el índice `0` en `GetChild(NodeType.Chart, 0, true)` con la posición basada en cero de tu gráfico objetivo, o recorre todos los nodos de gráficos:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### ¿Puedo colocar la leyenda en la parte inferior en lugar de a la derecha?

Claro. Simplemente cambia el enum `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### ¿Qué pasa si el gráfico ya tiene una leyenda pero quiero ocultarla?

Establece `HasLegend` a `false`:

```csharp
chart.HasLegend = false;
```

### ¿Esto funciona con Word 2010, 2016 y versiones posteriores?

Sí. Aspose.Words abstrae la versión subyacente de Word, por lo que el mismo código funciona en todos los archivos .docx modernos.

---

## Consejos profesionales y errores comunes

- **Consejo profesional:** Después de aplicar un estilo, aún puedes ajustar elementos individuales (colores, etiquetas de datos) a través de la colección `Chart.Series`. El estilo te brinda una base sólida.
- **Cuidado con:** Si el gráfico está dentro de una celda de tabla, la leyenda puede aparecer apretada. Considera aumentar el tamaño del gráfico (`chart.Width`, `chart.Height`) antes de posicionar la leyenda.
- **Nota de rendimiento:** Cargar documentos grandes (cientos de MB) puede consumir mucha memoria. Usa `LoadOptions` con `LoadFormat.Docx` para reducir la sobrecarga si solo necesitas manipular gráficos.

---

## Próximos pasos

Ahora que sabes **cómo agregar una leyenda** y **aplicar un estilo de gráfico predefinido** en Word, podrías explorar:

- **Colores personalizados del gráfico** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Formato de etiquetas de datos** (`chart.Series[i].HasDataLabel = true`).  
- **Exportar el gráfico como imagen** (`chart.ToImage()`), útil para incrustar en otro lugar.  

Cada uno de estos temas se basa en el mismo modelo de objetos, por lo que encontrarás la curva de aprendizaje suave.

---

## Conclusión

Acabamos de demostrar una solución limpia, de extremo a extremo, para **mostrar la leyenda del gráfico** en un documento de Word usando C#. Al cargar el documento, obtener el gráfico, aplicar un estilo predefinido, habilitar la leyenda y manejar las particularidades de los gráficos Waterfall, obtienes un gráfico pulido listo para cualquier informe empresarial.  

Siéntete libre de experimentar con otros valores de `ChartStyle` o posiciones de la leyenda—tus visualizaciones de datos merecen la mejor presentación. Si encuentras algún problema, deja un comentario abajo; ¡feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de columnas en un documento Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Ocultar eje del gráfico en un documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Usar la API de gráficos de Word](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}