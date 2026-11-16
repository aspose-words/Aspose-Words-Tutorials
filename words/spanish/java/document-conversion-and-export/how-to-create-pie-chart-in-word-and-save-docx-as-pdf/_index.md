---
category: general
date: 2026-11-15
description: Aprende cómo crear un gráfico circular en un documento de Word y guardar
  el docx como PDF usando Java. Esta guía también cubre la conversión de Word a PDF
  y cómo añadir un gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: es
lastmod: 2026-11-15
og_description: Crea un gráfico de pastel en un archivo Word y guarda el docx como
  PDF con Java. Sigue este tutorial paso a paso para convertir Word a PDF y añadir
  gráficos.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Crear un gráfico circular en Word y guardar el docx como PDF – Guía de Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Cómo crear un gráfico circular en Word y guardar el docx como PDF
url: /es/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico circular en Word y guardar docx como PDF

Si necesitas **crear un gráfico circular** dentro de un documento Word y luego **guardar docx como PDF**, este tutorial te muestra exactamente cómo. Verás un ejemplo completo y ejecutable que convierte un archivo .docx a PDF mientras inserta un gráfico circular, de modo que puedas responder “cómo agregar un gráfico” sin buscar fragmentos dispersos.

En esta guía aprenderás a:

* Cargar un *.docx* existente (o comenzar desde cero)  
* Usar Aspose.Words for Java para **crear un gráfico circular** y rellenar datos  
* **Guardar docx como PDF** con el gráfico renderizado correctamente  
* Entender los matices de **convertir Word a PDF** cuando hay gráficos involucrados  

Los pasos funcionan con Aspose.Words 2024‑x.x y Java 17, pero los conceptos se aplican a cualquier biblioteca que soporte la manipulación de gráficos en Word.

## Prerequisites

Antes de comenzar, asegúrate de tener:

| Requirement | Why it matters |
|-------------|----------------|
| Java 17 (o posterior) | Requerido por el último JAR de Aspose.Words |
| Herramienta de compilación Maven o Gradle | Simplifica la gestión de dependencias |
| Aspose.Words for Java (última versión) | Proporciona las clases `Document`, `Chart` y `ChartType` |
| Un archivo de entrada **.docx** (o un documento en blanco) | El gráfico se insertará en este archivo |

Añade la dependencia de Aspose.Words a tu `pom.xml` (Maven) o `build.gradle` (Gradle). Ejemplo para Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Step 1: Load the Word document (or create a new one)

El primer paso es obtener una instancia de `Document`. Si ya tienes una plantilla, pasa su ruta; de lo contrario, crea un documento vacío.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*¿Por qué este paso?* El objeto `Document` es el contenedor de todo el contenido de Word, incluidos los gráficos. Cargar un archivo existente te permite conservar el texto y los estilos circundantes mientras añades un nuevo elemento visual.

## Step 2: **Create pie chart** – the core of “how to create chart”

Ahora instanciamos un objeto `Chart` con `ChartType.PIE`. Esto crea automáticamente un marcador de posición para un gráfico circular que luego podrás rellenar con datos.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE` indica a Aspose.Words que use una plantilla de gráfico circular. El gráfico se agrega al cuerpo del documento, por lo que aparece donde lo necesites. Esto satisface el requisito de “cómo agregar un gráfico” en una sola llamada.

## Step 3: Populate the chart – answering “how to add chart” with data

Un gráfico circular no tiene sentido sin datos de series. Usa la colección `Series` para añadir categorías y valores.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: Cada llamada a `add` crea una porción del círculo. El primer argumento es la etiqueta, el segundo es el valor numérico. Puedes reemplazarlos con datos dinámicos provenientes de una base de datos o un archivo CSV.

### Optional: Customize appearance (not required but useful)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Estos ajustes ilustran cómo puedes **crear un gráfico** con un aspecto profesional, sin salir del código Java.

## Step 4: **Save docx as PDF** – the final part of “convert word to pdf”

Una vez insertado el gráfico, exporta el documento a PDF. Aspose.Words renderiza el gráfico como un vector, preservando la calidad.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: El método `save` convierte automáticamente el archivo Word a PDF, manejando la rasterización del gráfico, la incrustación de fuentes y el diseño de página. Esto cumple el objetivo de **guardar docx como PDF** y demuestra una forma fiable de **convertir Word a PDF** cuando hay gráficos presentes.

### Expected output

Ejecutar el programa produce `output.pdf` que contiene:

* El contenido original de `input.docx` (si lo hay)  
* Un gráfico circular completamente renderizado titulado *Sales Distribution Q1*  
* Porcentajes de porción precisos que coinciden con los datos (40 %, 30 %, 30 %)

Abre el PDF en cualquier visor y deberías ver un gráfico circular nítido, idéntico al que verías en el archivo Word.

## Common pitfalls and how to avoid them

| Issue | Cause | Fix |
|-------|-------|-----|
| Chart appears blank in PDF | Font or chart rendering settings missing | Asegúrate de estar usando la última versión de Aspose.Words; incluye las bibliotecas de renderizado necesarias. |
| Data values are rounded incorrectly | Using integer values with large numbers | Proporciona valores `double` o escala los números antes de añadirlos a la serie. |
| Output PDF is huge | Images embedded at high DPI | Configura `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` si también incrustas imágenes. |
| “convert word to pdf” throws `UnsupportedOperationException` | Using an older Java version (< 11) | Actualiza a Java 17 o posterior, que Aspose.Words 24.x requiere. |

## Pro tip: Re‑use the chart creation logic

Si necesitas añadir varios gráficos al mismo documento, extrae el código de creación de gráficos a un método auxiliar:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Ahora puedes llamar `doc.getFirstSection().getBody().appendChild(createPieChart(...));` para cada conjunto de datos, manteniendo tu código DRY (Don’t Repeat Yourself).

## Conclusion

Ahora sabes cómo **crear un gráfico circular** dentro de un documento Word, rellenarlo con datos y **guardar docx como PDF** usando Java. Este ejemplo de extremo a extremo cubre todo el flujo de trabajo de **convertir Word a PDF**, responde a **cómo agregar un gráfico** y demuestra **cómo crear un gráfico** programáticamente.  

A partir de aquí podrías explorar:

* Añadir gráficos de barras o líneas (`ChartType.BAR`, `ChartType.LINE`) – otro escenario de **cómo crear un gráfico**.  
* Exportar a otros formatos como PNG o HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Generar dinámicamente el documento de entrada con tablas o marcadores de posición antes de insertar los gráficos.

Siéntete libre de experimentar con diferentes conjuntos de datos, opciones de estilo o incluso incrustar varios gráficos por página. ¡Feliz codificación!

## What Should You Learn Next?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo insertar un gráfico circular en un documento Word usando Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Cómo guardar Word como PDF y crear PDF accesible en Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Cómo crear un gráfico en Word con Java y Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}