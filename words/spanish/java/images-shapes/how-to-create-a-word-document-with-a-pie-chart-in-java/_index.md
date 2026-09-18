---
category: general
date: 2026-09-18
description: Aprende a crear un documento de Word e insertar un gráfico circular usando
  Aspose.Words para Java. Incluye los pasos para rotar el gráfico circular y generar
  el archivo Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: es
lastmod: 2026-09-18
og_description: Crea un documento de Word e inserta un gráfico circular usando Java.
  Sigue esta guía para rotar el gráfico circular, separar las porciones y generar
  un archivo de Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Crea un documento de Word con un gráfico circular – guía paso a paso de
  Java
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Cómo crear un documento de Word con un gráfico circular en Java
url: /es/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word con un gráfico circular en Java

Si necesitas **crear un documento Word** que visualice datos, esta guía te muestra cómo hacerlo con Aspose.Words for Java. Aprenderás a insertar un gráfico circular, explotar una porción, rotar el gráfico y, finalmente, **generar un archivo Word** que podrás abrir en Microsoft Word.

Crear informes que combinen texto y gráficos no requiere una herramienta de diseño separada. Al final de este tutorial tendrás un programa completo y ejecutable que crea un archivo .docx que contiene un gráfico circular totalmente configurado.

## Requisitos previos

- Java 17 o posterior (el código también compila con Java 8+)
- Maven o Gradle para la gestión de dependencias
- Licencia de Aspose.Words for Java (la prueba gratuita funciona para este ejemplo)
- Familiaridad básica con la sintaxis de Java

## Paso 1: Configurar el proyecto Maven

Crea un nuevo proyecto Maven y agrega la dependencia de Aspose.Words en `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Consejo:** Mantén el número de versión actualizado; las versiones más recientes añaden mejoras en los tipos de gráficos y correcciones de errores.

## Paso 2: Crear un nuevo documento Word

La primera operación al **crear un documento Word** programáticamente es instanciar un objeto `Document`. Este objeto representa todo el archivo .docx en memoria.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

La clase `Document` es el punto de entrada para todas las funciones de procesamiento de Word. En este momento no se escribe ningún archivo en disco; todo ocurre en RAM hasta que llamas a `save`.

## Paso 3: Cómo insertar un gráfico circular

Un `DocumentBuilder` te permite añadir contenido al documento. Con `insertChart` puedes **insertar gráficos circulares** directamente.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` indica a Aspose.Words que cree un gráfico circular. Las dimensiones se expresan en puntos (1 pt ≈ 1/72 in). Después de esta llamada, el gráfico aparece en un nuevo párrafo.

## Paso 4: Poblar el gráfico con datos

Un gráfico circular necesita una serie de valores. Aquí añadimos tres categorías: “Apples”, “Bananas” y “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

El método `add` construye la serie y crea automáticamente las entradas de la leyenda. Puedes reutilizar este patrón para cualquier conjunto de datos numéricos.

## Paso 5: Resaltar la primera porción

Explotar una porción llama la atención sobre un valor concreto. La primera porción (índice 0) se explota en 20 puntos.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Establecer `explode` en la serie afecta a todo el gráfico, por lo que solo el primer punto de datos se desplaza.

## Paso 6: Cómo rotar un gráfico circular

Rotar el gráfico mejora el equilibrio visual, especialmente cuando la porción más grande no está en la parte superior. El método `setRotationAngle` espera grados.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Una rotación de 45° mueve el ángulo de inicio en sentido horario, facilitando la lectura del gráfico en muchos diseños.

## Paso 7: Guardar el documento y generar un archivo Word

Finalmente, escribe el documento en disco. Este paso **generará un archivo Word** que puede abrirse con Microsoft Word, LibreOffice o cualquier visor compatible.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

El método `save` detecta automáticamente la extensión .docx y escribe un paquete compatible con Word. La carpeta `output` debe existir o puedes crearla programáticamente.

### Resultado esperado

Después de ejecutar el programa, abre `output/PieChart.docx`. Deberías ver:

- Una sola página que contiene un gráfico circular de 400 × 300 pt.
- La porción “Apples” explotada hacia afuera en 20 pt.
- Todo el gráfico rotado 45° en sentido horario.
- Una leyenda que coincide con las tres categorías de fruta.

## Variaciones comunes y casos límite

### Insertar varios gráficos

Si necesitas más de un gráfico, llama a `builder.insertChart` nuevamente después de mover el cursor:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Cambiar los colores del gráfico

Puedes personalizar los colores de las porciones mediante la colección `getPoints()` de la serie:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Manejar conjuntos de datos grandes

Para conjuntos de datos con más de 10 porciones, considera usar un gráfico de rosquilla (`ChartType.DOUGHNUT`) para mantener la claridad visual.

## Conclusión

Ahora sabes cómo **crear un documento Word**, **insertar un gráfico circular**, **rotar el gráfico circular** y **generar un archivo Word** usando Aspose.Words for Java. La solución completa demuestra el flujo de trabajo completo, desde la inicialización del documento hasta la salida final del archivo, cubriendo tanto el “cómo” como el “por qué” de cada paso.

A continuación, explora temas relacionados como **cómo crear datos de gráfico circular** a partir de una base de datos, añadir etiquetas de datos o exportar el gráfico como imagen. Experimenta con diferentes tipos de gráficos (barras, líneas, rosquilla) para ampliar tu conjunto de herramientas de automatización de Word.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}