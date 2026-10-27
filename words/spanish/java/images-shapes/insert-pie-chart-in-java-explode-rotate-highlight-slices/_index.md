---
category: general
date: 2026-07-20
description: Inserta un gráfico de pastel en Java con una guía paso a paso. Aprende
  cómo separar una porción, cómo rotar el gráfico de pastel, resaltar una porción
  del gráfico y personalizar la porción del gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: es
lastmod: 2026-07-20
og_description: Inserta un gráfico circular en Java y domina cómo separar una porción,
  cómo rotar el gráfico circular, resaltar una porción del gráfico circular y personalizar
  la porción del gráfico circular para obtener informes visuales pulidos.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Insertar gráfico circular en Java – Explotar, rotar y resaltar
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Insertar gráfico de pastel en Java – Explotar, rotar y resaltar porciones
url: /es/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar gráfico circular en Java – Explotar, Rotar y Resaltar Segmentos

¿Alguna vez necesitaste **insertar un gráfico circular** en un informe Java pero no estabas seguro de cómo hacer que una sola porción sobresalga? No eres el único. Ya sea que estés construyendo un panel de control, generando una factura o simplemente visualizando los resultados de una encuesta, un gráfico circular bien diseñado puede convertir números crudos en una visión instantáneamente comprensible.

En este tutorial verás un ejemplo completo, listo para ejecutar, que muestra cómo **insertar un gráfico circular**, **cómo explotar una porción**, **cómo rotar un gráfico circular**, e incluso **resaltar una porción del gráfico circular** con colores personalizados. Al final tendrás un fragmento reutilizable que puedes insertar en cualquier proyecto Java que use la popular biblioteca *JFreeChart* (o cualquier API similar).

## Requisitos previos

- Java 17 o posterior (el código compila con versiones anteriores, pero usaremos la sintaxis moderna `var` por brevedad).  
- Maven o Gradle para obtener la dependencia `org.jfree:jfreechart`.  
- Una comprensión básica de clases Java y del concepto de un constructor de gráficos.  

Si nunca has añadido una biblioteca a un proyecto Maven, simplemente inserta esto en tu `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Eso es todo—no se requiere configuración adicional.

## Paso 1: Insertar gráfico circular – Crear el Builder y el objeto Chart

Lo primero: necesitamos un *builder* (piénsalo como una fábrica) que sepa cómo producir gráficos. En JFreeChart, el `ChartFactory` realiza el trabajo pesado.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

¿Por qué empezamos con el conjunto de datos? Porque el gráfico en sí es solo una capa visual alrededor de los números. Al **insertar un gráfico circular** aquí ya tenemos un lienzo de 400 × 300 (el tamaño se aplicará más tarde cuando lo rendericemos a una imagen).

## Paso 2: Cómo explotar una porción – Enfatizar el primer segmento

Ahora que el gráfico existe, hagamos que la primera porción destaque. Explotar una porción la aleja ligeramente del círculo, atrayendo la mirada del lector.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Observa que usamos la frase **how to explode slice** en el nombre del método; eso deja la intención perfectamente clara. El método `setExplodePercent` recibe una clave (la etiqueta de la porción) y un porcentaje, por lo que puedes ajustar la distancia de “explosión” según sea necesario.

## Paso 3: Cómo rotar un gráfico circular – Cambiar el ángulo de inicio

Un gráfico circular predeterminado comienza en la posición de las 12 en punto. A veces deseas que la primera porción empiece en otro lugar—quizá para alinearla con un mock‑up de diseño o para coincidir con otro gráfico.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Llamar a `rotateChart(chart, 45)` rota todo el gráfico circular de modo que la porción “Apples” comience a 45 grados, exactamente lo que solicita el requisito **how to rotate pie chart**.

## Paso 4: Resaltar una porción del gráfico circular – Colores y etiquetas personalizados

Más allá de explotar, podrías querer dar a una porción un color único o una etiqueta en negrita para realmente **highlight pie chart slice**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Aquí hemos **customize pie chart slice** modificando su pintura y estilo de etiqueta. Siéntete libre de cambiar el color o la fuente para que coincidan con la paleta de tu marca.

## Paso 5: Renderizar el gráfico a una imagen (Opcional pero útil)

La mayoría de las aplicaciones del mundo real necesitan el gráfico como PNG, JPEG o incluso PDF. A continuación se muestra una forma rápida de escribir el gráfico a un archivo.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Ejecutar todo el flujo producirá un PNG de 400 × 300 que se verá algo así:

![Insert pie chart example](image.png){: alt="Ejemplo de inserción de gráfico circular que muestra una porción explotada y rotada"}

## Ejemplo completo funcionando

Juntando todo, aquí tienes un método `main` que puedes copiar y pegar en una nueva clase Java y ejecutar:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Salida esperada

Ejecutar el programa crea un archivo llamado **fruit-pie.png**. Ábrelo y verás:

- Un gráfico circular de 400 × 300 titulado “Fruit Distribution”.  
- La porción “Apples” explotada hacia afuera en un 15 %.  
- Todo el gráfico rotado de modo que “Apples” comience en la posición de 45 grados.  
- La explotada

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Insertar gráfico de dispersión](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Insertar gráfico de áreas](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}