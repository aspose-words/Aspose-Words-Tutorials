---
category: general
date: 2026-11-25
description: Aprende a crear un gráfico circular en Java, insertar el gráfico circular
  en un documento de Word, separar una porción del gráfico y cambiar la orientación
  del gráfico con ejemplos de código claros.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: es
lastmod: 2026-11-25
og_description: Crear un gráfico circular en Java, insertar el gráfico circular en
  un documento, separar una porción del gráfico y cambiar la orientación del gráfico
  con código paso a paso.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Crear un gráfico de pastel en Java – insertar, explotar una porción y rotar
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Cómo crear un gráfico circular, insertarlo y personalizar la orientación en
  Java
url: /es/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico circular, insertarlo y personalizar la orientación en Java

Si necesitas **crear un gráfico circular** dentro de un documento Word, esta guía te muestra exactamente cómo hacerlo. Verás cómo **insertar un gráfico circular**, explotar una porción para enfatizarla y **cambiar la orientación del gráfico** con una simple rotación.

El tutorial cubre todo lo que necesitas — desde configurar la biblioteca Aspose.Words for Java hasta generar un archivo final `.docx` que muestra un gráfico circular rotado y explotado. No se requiere documentación externa; simplemente sigue los pasos y ejecuta el código.

## Requisitos previos

* Java 17 o una versión más reciente instalada.
* Maven o Gradle para gestionar dependencias.
* Una licencia válida de Aspose.Words for Java (o usar el modo de evaluación gratuito).

Agrega la dependencia de Aspose.Words a tu `pom.xml` (Maven) o `build.gradle` (Gradle). Ejemplo para Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Consejo profesional:** Mantén la versión de la biblioteca actualizada; la última versión (24.10 al momento de escribir) incluye correcciones de errores para la renderización de gráficos.

## Paso 1: Crear un gráfico circular e insertarlo en el documento

El primer paso es **crear objetos de gráfico circular** e incrustarlos en un archivo Word. El código a continuación crea un documento sencillo, agrega un marcador de posición para el gráfico e inserta un gráfico circular de tamaño 400 × 300 píxeles.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Por qué es importante:** `builder.insertChart` crea un marcador de posición para el gráfico que Aspose.Words convierte automáticamente a un gráfico OOXML cuando se guarda el documento. El argumento `ChartType.PIE` indica a la biblioteca que renderice un gráfico circular, cumpliendo con el requisito de **insertar un gráfico circular**.

## Paso 2: Explotar una porción del gráfico circular para resaltar un segmento

Explotar una porción llama la atención sobre un punto de datos particular. La siguiente línea explota la primera porción (índice 0) en 10 puntos:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Puedes cambiar el índice para apuntar a una porción diferente, o ajustar la distancia de explosión para un efecto más sutil. Explotar una porción es la forma estándar de **explotar una porción del gráfico circular** en Aspose.Words.

## Paso 3: Cambiar la orientación del gráfico rotándolo

Rotar el gráfico brinda una nueva perspectiva visual. Usa `setRotationAngle` para rotar todo el gráfico en sentido horario (el ángulo se mide en grados).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

La llamada anterior satisface los requisitos de **rotar el gráfico circular** y **cambiar la orientación del gráfico**. Se acepta cualquier ángulo entre 0 y 360 grados.

## Ejemplo completo ejecutable

Uniendo todo, aquí tienes un programa completo y autónomo que crea un gráfico circular, explota una porción y rota el gráfico. Ejecútalo desde tu IDE o desde la línea de comandos con `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Resultado esperado

* Aparece un archivo llamado **CreatePieChartDemo.docx** en el directorio de trabajo.
* Al abrir el archivo en Microsoft Word se muestra un gráfico circular de 400 × 300 píxeles.
* La primera porción (Q1) se desplaza hacia afuera en 10 puntos, creando un efecto de **explotar una porción del gráfico circular**.
* Todo el gráfico está inclinado 45 grados, demostrando **cambiar la orientación del gráfico** y **rotar el gráfico circular**.

## Variaciones comunes y casos límite

| Situación | Cómo adaptar el código |
|-----------|------------------------|
| **Tamaño de gráfico diferente** | Cambiar los argumentos `400, 300` en `insertChart`. |
| **Múltiples series** | Agregar más objetos `ChartSeries` a `chart.getSeries()`. |
| **Explotar una porción diferente** | Usar `setExplode(sliceIndex, distance)` con el `sliceIndex` deseado. |
| **No se necesita rotación** | Omitir la llamada `setRotationAngle` o establecer el ángulo a `0`. |
| **Exportar a PDF en lugar de DOCX** | Después de crear el documento, llamar a `doc.save("output.pdf")` con el formato PDF. |

> **Cuidado:** Usar una distancia de explosión negativa lanza `IllegalArgumentException`. Siempre proporciona un valor no negativo.

## Consejo de rendimiento

Si generas muchos gráficos en un bucle, reutiliza un único `DocumentBuilder` y llama a `insertChart` solo en cada iteración. Esto reduce el consumo de memoria y acelera el procesamiento.

## Conclusión

Ahora sabes cómo **crear un gráfico circular**, **insertar un gráfico circular**, **explotar una porción del gráfico circular** y **rotar un gráfico circular** usando Aspose.Words for Java. El ejemplo completo muestra el flujo de trabajo completo — desde inicializar el documento hasta guardar un archivo que visualiza un gráfico circular rotado y explotado.

A continuación, podrías explorar **cambiar la orientación del gráfico** más a fondo aplicando efectos 3‑D, o experimentar con otros tipos de gráficos como **Bar** o **Line**. Los mismos patrones de API se aplican, por lo que ampliar este tutorial es sencillo.

¡Siéntete libre de modificar los datos, el índice de la porción o el ángulo de rotación para adaptarlos a tus necesidades de informes, y comparte tus resultados con la comunidad!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo insertar un gráfico circular en un documento Word usando Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Cómo explotar una porción del gráfico circular en Java – tutorial de gráficos Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}