---
category: general
date: 2026-08-07
description: Cómo explotar una porción de pastel en Java usando Aspose.Words. Aprende
  a agregar líneas guía al pastel, crear un gráfico de Word y personalizar las porciones
  del gráfico de pastel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: es
lastmod: 2026-08-07
og_description: Cómo separar una porción de pastel en Java con Aspose.Words. Esta
  guía le muestra cómo agregar líneas de guía al pastel, crear gráficos en Word y
  personalizar las porciones del gráfico de pastel para lograr un impacto visual claro.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Cómo explotar una porción de pastel en Java – Guía de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Cómo separar una porción de pastel en Java – tutorial de gráficos Aspose.Words
url: /es/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo explotar una porción de pastel en Java – Tutorial de gráficos Aspose.Words

Si necesitas saber **cómo explotar una porción de pastel** en un documento Word usando Java, este tutorial te cubre. También te mostraremos **cómo agregar líneas guía al pastel** en los gráficos, **java create word chart** objects, y **personalizar las porciones del gráfico de pastel** para un resultado pulido. Al final de esta guía tendrás un ejemplo completo y ejecutable que podrás insertar en cualquier proyecto Java.

![Cómo explotar una porción de pastel en Java – gráfico Aspose.Words](/images/pie-chart-exploded.png)

## Requisitos previos

* Java Development Kit (JDK) 8 o superior.
* Maven o Gradle para la gestión de dependencias.
* Una licencia de Aspose.Words for Java (la evaluación gratuita funciona para propósitos de aprendizaje).
* Familiaridad básica con la sintaxis de Java y conceptos orientados a objetos.

> **Consejo profesional:** Aunque Aspose.Words ofrece una prueba gratuita, comprar una licencia elimina la marca de agua de evaluación de los documentos generados.

## Qué cubre este tutorial

* Crear un nuevo documento Word desde cero.  
* Insertar un **pie chart** usando `DocumentBuilder`.  
* **Explotar una porción de pastel** para resaltar un punto de datos.  
* **Agregar líneas guía al pastel** para un etiquetado más claro.  
* Personalizar la apariencia de la porción, como colores y bordes.  
* Guardar el documento en disco y verificar el resultado.

---

## Cómo explotar una porción de pastel con Aspose.Words en Java

La primera paso es configurar el objeto del gráfico y explotar la porción deseada. Aspose.Words expone el gráfico a través de la clase `Shape`, y cada porción es un `ChartPoint`. Al establecer la propiedad `Explosion` controlas qué tan lejos se desplaza la porción hacia afuera.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Por qué funciona:**  
`setExplosion(20)` indica al motor del gráfico que desplace la porción 20 puntos desde el centro del gráfico. El valor es relativo; números mayores crean un efecto más dramático. Puedes explotar cualquier porción cambiando el índice (`get(1)`, `get(2)`, …).

## Agregar líneas guía al pastel para etiquetas más claras

Las líneas guía conectan la etiqueta de una porción con su borde, lo cual es especialmente útil cuando las porciones están explotadas o cuando el gráfico contiene muchas secciones pequeñas. La llamada `setLeaderLines(true)` habilita esta característica para toda la serie.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Por qué necesitas líneas guía:**  
Cuando una porción está explotada, la etiqueta predeterminada puede superponerse con otros elementos. Las líneas guía mantienen la etiqueta legible al dibujar una línea corta desde la porción hasta el cuadro de texto.

## Java create Word chart – insertando series de datos

Un gráfico sin datos no es muy útil. Debes poblar la serie con categorías y valores. A continuación agregamos tres categorías que representan la cuota de mercado.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Explicación:**  
`ChartSeries` contiene tanto las categorías (los nombres de las porciones) como los valores numéricos. Habilitar `ShowCategoryName` y `ShowPercentage` hace que el gráfico sea autoexplicativo, lo que combina bien con las líneas guía que agregamos anteriormente.

## Personalizar las porciones del gráfico de pastel más allá de la explosión

Más allá de explotar una porción, a menudo deseas ajustar colores, bordes o incluso ocultar una porción por completo. El siguiente fragmento demuestra tres personalizaciones comunes:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Por qué personalizar las porciones:**  
Los colores personalizados hacen que el gráfico se alinee con la identidad corporativa, mientras que los bordes mejoran la legibilidad en páginas impresas. Ocultar una porción es útil cuando deseas mantener intacto el modelo de datos pero omitir temporalmente una categoría de la salida visual.

## Guardar el documento y verificar el resultado

Finalmente, escribe el documento en disco. Puedes abrir el `.docx` generado en Microsoft Word, LibreOffice o cualquier visor que soporte el formato.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Salida esperada:**  
Al abrir `PieChartDemo.docx`, verás un gráfico de pastel donde la primera porción (Product A) está explotada hacia afuera, las líneas guía apuntan de cada porción a su etiqueta, y las porciones aparecen en los colores personalizados verde, azul y naranja. La porción oculta (Product C) no será visible, pero los porcentajes seguirán sumando 100 % porque los datos permanecen en la serie del gráfico.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar, pegar y ejecutar después de agregar la dependencia de Aspose.Words a tu proyecto.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dependencia (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cómo cargar documentos Word con Aspose.Words Java: Guía completa](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}