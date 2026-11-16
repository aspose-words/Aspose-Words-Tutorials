---
category: general
date: 2026-11-15
description: Aprenda cómo agregar un gráfico circular a un documento de Word con Aspose.Words
  para Java. Incluye conversión a rosquilla, porción explotada y muestra de código
  completa.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: es
lastmod: 2026-11-15
og_description: Agrega un gráfico circular a un documento de Word usando Aspose.Words
  para Java. Este tutorial muestra cómo separar una porción y convertir el gráfico
  en un gráfico de rosquilla.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Añade un gráfico circular a un documento de Word con Java – guía paso a
  paso
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Cómo agregar un gráfico circular a un documento de Word usando Java
url: /es/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar un gráfico circular a un documento Word – guía completa de Java

Si necesitas **agregar un gráfico circular a un documento Word** de forma programática, este tutorial te muestra exactamente cómo hacerlo con Aspose.Words for Java. Verás el flujo completo: cargar un DOCX, crear un gráfico circular, explotar la primera porción y convertir el gráfico en un donut estableciendo el tamaño del agujero.

La guía también cubre variaciones comunes—como agregar varias series, personalizar colores y manejar documentos que ya contienen gráficos—para que puedas adaptar el código a proyectos del mundo real, como informes automatizados o presentaciones dinámicas.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o posterior (el código también compila con JDK 11+)
* Maven 3.6+ o Gradle para la gestión de dependencias
* Una licencia de Aspose.Words for Java (la prueba gratuita funciona para pruebas)
* Un conocimiento básico de la sintaxis de Java y la estructura de proyectos Maven

## Paso 1: Configurar el proyecto Maven e importar Aspose.Words

Crea un nuevo proyecto Maven (o añádelo a uno existente) e incluye la dependencia de Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Consejo profesional:** Si usas Gradle, la entrada equivalente es `implementation 'com.aspose:aspose-words:24.9'`.

La dependencia incorpora las clases `Document`, `Chart` y `ChartType` que necesitarás para manipular gráficos.

## Paso 2: Cargar el documento objetivo

Puedes comenzar a partir de un archivo `.docx` existente o crear un documento en blanco nuevo. El ejemplo a continuación carga una plantilla llamada `input.docx` ubicada en la carpeta `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Si el archivo no existe, Aspose.Words creará automáticamente un documento vacío nuevo cuando llames a `new Document()` sin especificar un nombre de archivo.

## Paso 3: Crear un gráfico circular e insertarlo en el documento

Aspose.Words trata un gráfico como una forma que puede colocarse dondequiera que aparezca un párrafo. El siguiente código crea un **gráfico circular**, agrega una única serie de datos e inserta el gráfico después del primer párrafo.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Por qué este paso es importante:**  
* `ChartType.PIE` indica a Aspose.Words que renderice un gráfico circular tradicional.  
* Añadir una serie con etiquetas de categoría y valores numéricos rellena automáticamente las porciones.  
* Insertar el gráfico como hijo de un `Paragraph` mantiene intacto el flujo del documento.

## Paso 4: Explotar la primera porción para resaltarla

Una *porción explotada* llama la atención sobre un punto de datos concreto. La API expone `setExplode(boolean)` en un objeto `ChartSeries`. Configurarlo en la primera serie (índice 0) hace que la primera porción sobresalga.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Pregunta frecuente:** *¿Qué pasa si tengo varias series?*  
> Puedes apuntar a una serie específica por su índice, por ejemplo, `pieChart.getSeries().get(1).setExplode(true)` para la segunda serie.

## Paso 5: Convertir el gráfico circular en un donut estableciendo el tamaño del agujero

Un gráfico donut es esencialmente un gráfico circular con un centro hueco. Aspose.Words te permite definir el tamaño del agujero como un porcentaje del radio del gráfico.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

El método `setHoleSize` acepta valores desde **0** (gráfico circular normal) hasta **100** (completamente vacío). Un valor alrededor de **30‑40** produce un donut visualmente equilibrado.

## Paso 6: Guardar y verificar el resultado

Después de todas las modificaciones, guarda el documento. La siguiente línea escribe el archivo en la carpeta `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Resultado esperado

Abre `final-pie-doughnut.docx` en Microsoft Word:

* Aparece un gráfico donut donde estaba el primer párrafo.  
* La porción “Apples” está explotada (ligeramente separada del resto).  
* El gráfico muestra cuatro porciones etiquetadas *Apples*, *Bananas*, *Cherries*, *Dates* con los porcentajes que proporcionaste.

Si prefieres salida en PDF, cambia el `SaveFormat` a `SaveFormat.PDF`.

## Manejo de casos límite y variaciones

### Agregar varias series

Si necesitas varias series (p. ej., donut apilado), añádelas secuencialmente:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Colores personalizados

Puedes asignar un color a cada porción mediante `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Trabajar con un gráfico existente

Si el documento ya contiene un gráfico y solo deseas modificarlo, localiza la forma del gráfico:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Manejo de licencia

Aspose.Words requiere una licencia para uso en producción. Coloca tu archivo `Aspose.Words.lic` en el classpath y cárgalo al iniciar la aplicación:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

No establecer una licencia añadirá una marca de agua al documento generado.

## Ejemplo completo y ejecutable

A continuación se muestra la clase Java completa que incorpora cada paso descrito. Cópiala en `src/main/java/com/example/AddPieChart.java` y ejecuta `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Ejecutar el programa genera el gráfico donut descrito anteriormente. Ajusta `categories`, `values` o `holeSize` según tus datos.

## Conclusión

Ahora sabes cómo **agregar un gráfico circular a un documento Word** usando Java y Aspose.Words. El tutorial cubrió la carga de un documento, la creación de un gráfico circular, la explosión de una porción, la transformación del gráfico en un donut y el manejo de variaciones comunes como múltiples series, colores personalizados y gráficos existentes. Con esta base puedes crear herramientas de informes automatizados, generar presentaciones dinámicas o incrustar visualizaciones ricas directamente en archivos Word.

### Qué explorar a continuación

* **add bar chart to Word document** – pasos similares pero usando `ChartType.BAR`.  
* **customize chart legends and titles** – usa `pieChart.getTitle().setText("...")` y `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **export the Word document as PDF** – cambia el `SaveFormat` a `PDF` para archivos listos para distribución.  
* **populate chart data from a database** – reemplaza los arreglos estáticos con resultados de consultas JDBC.

¡Siéntete libre de experimentar con diferentes tipos de gráficos, fuentes de datos y opciones de estilo! Feliz codificación.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}