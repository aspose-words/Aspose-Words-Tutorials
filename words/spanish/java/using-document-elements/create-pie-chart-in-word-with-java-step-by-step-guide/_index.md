---
category: general
date: 2026-08-14
description: Crear un gráfico circular en Word con Java usando Aspose.Words. Aprende
  cómo agregar datos de serie al gráfico y rotar la porción del gráfico circular en
  solo unas pocas líneas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: es
lastmod: 2026-08-14
og_description: Crear gráfico circular en Word con Java usando Aspose.Words. Este
  tutorial muestra cómo agregar datos de serie al gráfico y rotar rápidamente una
  porción del gráfico circular.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Crear gráfico de pastel en Word con Java – guía completa de codificación
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Crear gráfico de pastel en Word con Java – guía paso a paso
url: /es/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear gráfico circular en Word con Java – guía paso a paso

Si necesitas **crear un gráfico circular en Word** de forma programática, esta guía te muestra exactamente cómo hacerlo con Java y Aspose.Words. Aprenderás el flujo de trabajo completo, desde insertar el gráfico hasta agregar puntos de datos y rotar la primera porción.

Generar un gráfico directamente en un archivo `.docx` elimina el paso manual de copiar‑pegar y te permite automatizar informes, facturas o paneles de control. A lo largo del camino también cubriremos **cómo agregar datos de serie al gráfico** y cómo **rotar la porción del gráfico circular** para un mejor énfasis visual.

## Crear gráfico circular en Word – visión general

Aspose.Words for Java ofrece una API fluida `DocumentBuilder` que puede insertar un objeto de gráfico en un documento Word. El tipo de gráfico que elijas determina el diseño predeterminado, y puedes personalizar las series, colores, ángulos e incluso cambiar a una forma de rosquilla con una sola llamada de método.

### ¿Por qué usar Aspose.Words?

* **No Microsoft Office required** – la biblioteca funciona en cualquier servidor o entorno CI.  
* **Full .docx fidelity** – el gráfico generado se ve idéntico al creado manualmente en Word.  
* **Single‑file dependency** – solo agrega el JAR y estarás listo para usar.

## Cómo agregar datos de serie al gráfico

Un gráfico sin datos es solo un marcador de posición. El objeto `Chart` expone una colección `Series`; cada serie contiene una lista de valores numéricos que se asignan a porciones (para un gráfico circular) o puntos (para una línea). Agregar datos es sencillo:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**What the code does:**  
* `chart.getSeries()` returns a `List<ChartSeries>`.  
* `get(0)` selects the first series because a pie chart contains only one series by definition.  
* `add(double)` appends a data point. The values are automatically converted to percentages that sum to 100 % when the chart renders.

> **Pro tip:** If your data source contains more than three categories, keep adding values in the same way. Aspose.Words will automatically create additional slices.

**Qué hace el código:**  
* `chart.getSeries()` devuelve una `List<ChartSeries>`.  
* `get(0)` selecciona la primera serie porque un gráfico circular contiene solo una serie por definición.  
* `add(double)` agrega un punto de datos. Los valores se convierten automáticamente a porcentajes que suman 100 % al renderizar el gráfico.

> **Pro tip:** Si tu fuente de datos contiene más de tres categorías, sigue agregando valores de la misma manera. Aspose.Words creará automáticamente porciones adicionales.

## Rotar la porción del gráfico circular

A veces deseas que una porción específica comience en un ángulo determinado para que el segmento más importante mire al espectador. El método `setFirstSliceAngle(double)` rota todo el gráfico, moviendo efectivamente el inicio de la primera porción:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

El ángulo se mide en grados en sentido horario desde el eje vertical. Configurarlo a `0` (valor predeterminado) coloca la primera porción en la parte superior. Ajusta el valor para resaltar una porción o para cumplir con una guía de diseño.

> **Common question:** *Does rotating affect the data order?*  
> No. The data order stays the same; only the visual starting position changes.

> **Pregunta frecuente:** *¿La rotación afecta el orden de los datos?*  
> No. El orden de los datos se mantiene; solo cambia la posición inicial visual.

## Ejemplo completo en Java

A continuación se muestra un programa completo, listo para ejecutar, que crea un documento Word con un gráfico circular, agrega datos de serie, rota la porción y guarda el archivo. Todas las importaciones necesarias están listadas, para que puedas copiar el código en cualquier IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Resultado esperado

* Aparece un archivo llamado **PieChart.docx** en la carpeta `output`.  
* Al abrir el archivo en Microsoft Word se muestra un gráfico circular colorido con tres porciones (40 %, 30 %, 30 %).  
* El gráfico está rotado 45° en sentido horario, de modo que la primera porción comienza ligeramente a la derecha del eje vertical.

## Errores comunes y buenas prácticas

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **El gráfico aparece en blanco** | El documento se guardó antes de que el gráfico se renderizara completamente. | Llama a `doc.save()` **después** de todas las modificaciones del gráfico. |
| **Los valores de las porciones no suman 100 %** | Agregar números sin representar porcentajes puede provocar un escalado inesperado. | Proporciona valores que representen lógicamente porciones de un todo, o permite que Aspose.Words calcule los porcentajes automáticamente. |
| **La rotación no tiene efecto** | Usar `ChartType.DOUGHNUT` sin establecer `holeSize` puede ocultar el efecto de rotación. | Mantén el gráfico como `PIE` o ajusta `holeSize` después de establecer el ángulo. |
| **Errores de ruta de archivo** | Las rutas relativas pueden resolverse de manera diferente en Windows vs. Linux. | Usa `Paths.get("output", "PieChart.docx").toString()` o una ruta absoluta para código de producción. |

### Consejos para uso en producción

* **Reuse the `DocumentBuilder`** – puedes insertar varios gráficos en el mismo documento llamando a `insertChart` repetidamente.  
* **Styling** – usa `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` para mostrar los porcentajes directamente en el gráfico.  
* **Performance** – genera el gráfico una vez y clónalo (`chart.deepClone()`) si necesitas gráficos idénticos en varios lugares.

## Rotar la porción del gráfico circular – escenarios avanzados

* **Dynamic angle** – calcula el ángulo basado en los datos (p.ej., haz que la porción más grande comience en la parte superior).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Multiple series** – aunque un gráfico circular normalmente tiene una serie, Aspose.Words te permite agregar más para gráficos circulares apilados. La rotación aún se aplica solo a la primera serie.

## Conclusión

Ahora sabes cómo **crear un gráfico circular en Word** usando Java, cómo **agregar datos de serie al gráfico**, y cómo **rotar la porción del gráfico circular** para un énfasis visual. El ejemplo completo demuestra todo el flujo de trabajo—desde la inicialización del documento hasta guardar el archivo final `.docx`—para que puedas integrar la generación de gráficos en cualquier canal de informes automatizado.

### ¿Qué sigue?

* Explora otros tipos de gráficos (`ChartType.BAR`, `ChartType.LINE`) para ampliar tu conjunto de herramientas de automatización.  
* Combina la generación de gráficos con **mail merge** para producir informes personalizados para cada destinatario.  
* Sumérgete en la **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) para que coincida con la identidad corporativa.

¡Siéntete libre de experimentar con diferentes conjuntos de datos, ángulos y estilos de gráficos. Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cómo convertir Word a PDF usando Aspose.Words para Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}