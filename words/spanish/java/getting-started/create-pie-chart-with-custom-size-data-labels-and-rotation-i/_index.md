---
category: general
date: 2026-11-22
description: Crea un gráfico de pastel en Java y aprende cómo establecer el tamaño
  del gráfico, agregar etiquetas de datos, mostrar porcentajes y rotar la primera
  porción para lograr un impacto visual claro.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: es
lastmod: 2026-11-22
og_description: Crear un gráfico circular en Java, luego establecer el tamaño del
  gráfico, mostrar los porcentajes en las etiquetas de datos y rotar la primera porción,
  todo en un único ejemplo ejecutable.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Crear gráfico de pastel con tamaño personalizado, etiquetas y rotación en
  Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Crear gráfico de pastel con tamaño personalizado, etiquetas de datos y rotación
  en Java
url: /es/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear gráfico de pastel con tamaño personalizado, etiquetas de datos y rotación en Java

Si necesitas **crear gráfico de pastel** en Java, esta guía te acompañará paso a paso en todo el proceso. Aprenderás cómo **establecer el tamaño del gráfico**, habilitar **mostrar porcentajes en el gráfico de pastel**, añadir **etiquetas de datos al gráfico de pastel**, y **rotar la porción del gráfico de pastel** para que la primera porción comience en un ángulo de 45 grados.

El ejemplo utiliza **Aspose.Slides for Java**, una biblioteca ampliamente usada para manipular archivos PowerPoint. Los mismos conceptos se aplican a otras bibliotecas de gráficos; simplemente reemplaza las llamadas a la API por sus equivalentes en tu toolkit.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o posterior instalado  
* Maven 3.8+ (o Gradle) para la gestión de dependencias  
* Un conocimiento básico de la sintaxis de Java  
* Acceso al binario de Aspose.Slides for Java (puedes obtener una prueba gratuita en el sitio oficial)

Añade la dependencia a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Crear gráfico de pastel – ejemplo completo

El siguiente programa crea una diapositiva de PowerPoint que contiene un gráfico de pastel con un tamaño personalizado, etiquetas de datos en porcentaje y una primera porción rotada.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Por qué cada paso es importante

| Paso | Propósito | Cómo se relaciona con las palabras clave |
|------|-----------|------------------------------------------|
| **Insertar gráfico** | **Crear gráfico de pastel** – el objeto central que renderizará la visualización. | Satisface directamente el requisito de *crear gráfico de pastel*. |
| **Establecer dimensiones** | La llamada `addChart(..., 400, 300)` demuestra **establecer el tamaño del gráfico**. | Controla el ancho (400 px) y la altura (300 px). |
| **Mostrar porcentajes** | `setShowPercentage(true)` hace que el gráfico **mostrar porcentajes en el gráfico de pastel** en cada porción. | Los usuarios a menudo necesitan porcentajes en lugar de valores crudos. |
| **Añadir etiquetas de datos** | La configuración `DataLabelFormat` agrega **etiquetas de datos al gráfico de pastel** con la visibilidad deseada. | Las etiquetas mejoran la legibilidad y son personalizables. |
| **Rotar porción** | `setFirstSliceAngle(45)` rota el gráfico para que la primera porción comience en un ángulo de 45 grados, cumpliendo **rotar la porción del gráfico de pastel**. | Mejora el énfasis visual de una porción en particular. |

## Desglose paso a paso

### 1. Insertar un gráfico de pastel y establecer el tamaño del gráfico

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*El método `addChart` crea el gráfico y simultáneamente **establece el tamaño del gráfico** a 400 × 300 puntos.*  
Si necesitas un tamaño diferente, ajusta los dos últimos argumentos.

### 2. Poblar el gráfico con datos

La demostración añade tres categorías y una sola serie. Sustituye los números codificados por datos provenientes de una base de datos, CSV o entrada del usuario según sea necesario.

### 3. Mostrar porcentajes en cada porción

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Habilitar `setShowPercentage(true)` asegura que el gráfico **mostrar porcentajes en el gráfico de pastel** calcule automáticamente la participación de cada porción del total.*

### 4. Añadir etiquetas de datos detalladas

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Puedes alternar otras opciones de etiqueta (`setShowValue`, `setShowSeriesName`, etc.) para adaptar la experiencia de **añadir etiquetas de datos al gráfico de pastel**.

### 5. Rotar la primera porción

```java
chart.setFirstSliceAngle(45);
```

*Llamar a `setFirstSliceAngle(45)` **rotar la porción del gráfico de pastel** para que el primer segmento comience en un ángulo de 45 grados, haciéndolo destacar.*

### 6. Guardar y ver el resultado

Al ejecutar el programa se genera `output/PieChartDemo.pptx`. Ábrelo en PowerPoint o cualquier visor compatible para ver el gráfico de pastel final:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Captura de pantalla de un gráfico de pastel creado con tamaño personalizado, etiquetas de porcentaje y una primera porción rotada"}

La imagen anterior muestra el resultado de **crear gráfico de pastel**, confirmando que el tamaño, las etiquetas, los porcentajes y la rotación se aplicaron correctamente.

## Variaciones comunes y casos límite

| Situación | Ajuste |
|-----------|--------|
| **Dimensiones de gráfico diferentes** | Cambia los parámetros de ancho/alto en `addChart`. |
| **Múltiples series** | Añade objetos `IChartSeries` adicionales; cada serie puede tener su propia configuración de etiquetas. |
| **Formato de etiqueta personalizado** | Usa `series.getDataLabelFormat().setNumberFormat("0.0%")` para controlar los decimales. |
| **Rotar a otro ángulo** | Pasa cualquier entero (0‑360) a `setFirstSliceAngle`. |
| **Exportar como imagen** | Después de guardar, llama a `chart.writeAsSvg(outPath)` o `chart.writeAsPng(outPath)` para obtener una versión rasterizada. |

> **Consejo profesional:** Si planeas generar muchos gráficos dentro de un bucle, reutiliza el mismo objeto `Presentation` y solo reemplaza los datos del gráfico. Esto reduce el consumo de memoria y acelera el procesamiento.

## Conclusión

Ahora sabes cómo **crear gráfico de pastel** en Java, **establecer el tamaño del gráfico**, habilitar **mostrar porcentajes en el gráfico de pastel**, **añadir etiquetas de datos al gráfico de pastel**, y **rotar la porción del gráfico de pastel** para un mejor énfasis visual. El ejemplo completo y ejecutable muestra cada paso, desde la inicialización hasta el guardado del archivo PowerPoint final.

### ¿Qué sigue?

* Explora otros tipos de gráficos (Barras, Líneas, Área) usando el mismo enumerado `ChartType`.  
* Combina varios gráficos en una sola diapositiva para crear paneles de control.  
* Exporta gráficos a PNG o SVG para utilizarlos en aplicaciones web.  

Siéntete libre de experimentar con colores, leyendas y efectos de animación; tus visualizaciones de datos solo están limitadas por la imaginación. ¡Feliz creación de gráficos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [cómo insertar gráfico de pastel en Word – añadir etiqueta de datos con porcentaje](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Cómo explotar una porción de pastel en Java – tutorial de gráficos Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Insertar gráfico de pastel en Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}