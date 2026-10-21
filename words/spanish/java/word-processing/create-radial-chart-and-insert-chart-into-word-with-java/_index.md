---
category: general
date: 2026-09-27
description: Crear un gráfico radial en Java e insertarlo en Word. Aprende cómo establecer
  el tamaño del gráfico, agregar series de datos y generar un documento Word en blanco.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: es
lastmod: 2026-09-27
og_description: Crear un gráfico radial en Java, luego insertar el gráfico en Word.
  Esta guía muestra cómo establecer el tamaño del gráfico, agregar series de datos
  y crear un documento de Word en blanco.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Crear gráfico radial e insertar el gráfico en Word con Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Crear un gráfico radial e insertarlo en Word con Java
url: /es/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un gráfico radial e insertar el gráfico en Word con Java

Si necesitas **crear un gráfico radial** en un archivo Word usando Java, este tutorial te muestra exactamente cómo. Verás cómo **insertar el gráfico en Word**, establecer las dimensiones del gráfico y crear un **documento Word en blanco** desde cero.

Recorreremos cada paso necesario, desde inicializar el documento hasta agregar una serie de datos y guardar el `.docx` final. Al final tendrás un archivo Word totalmente funcional que contiene un gráfico radial, y comprenderás **cómo establecer el tamaño del gráfico** y **agregar serie de datos al gráfico** para futuras personalizaciones.

## Requisitos previos

* Java 17 o posterior (el código se compila con cualquier JDK moderno)
* Aspose.Words for Java 24.9 o más reciente – el método `setShowGraduations` solo está disponible a partir de esta versión
* Un IDE o herramienta de compilación (Maven/Gradle) que pueda incluir el JAR de Aspose.Words
* Familiaridad básica con la sintaxis de Java y la gestión de dependencias de Maven/Gradle

> **Consejo profesional:** Si estás usando Maven, agrega lo siguiente a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Paso 1: Crear un documento Word en blanco

Un documento en blanco es el lienzo donde se colocará el gráfico. La clase `Document` representa todo el archivo `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Crear un documento en blanco garantiza que no haya contenido preexistente que interfiera con el diseño del gráfico.

## Paso 2: Inicializar un DocumentBuilder

`DocumentBuilder` proporciona métodos convenientes para insertar objetos, texto y otros elementos en el documento.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

El constructor se usará más adelante para **insertar el gráfico en Word**.

## Paso 3: Construir el gráfico radial

Aspose.Words admite muchos tipos de gráficos; `ChartType.RADIAL` crea un gráfico radial (polar).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

En este punto el gráfico existe pero no tiene datos, tamaño ni opciones visuales.

## Paso 4: Agregar una serie de datos al gráfico

Un gráfico sin una serie de datos está vacío. El método `add` recibe un nombre de serie y una matriz de valores.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Puedes agregar múltiples series llamando a `add` repetidamente. Esto satisface el requisito de **agregar serie de datos al gráfico**.

## Paso 5: Habilitar graduaciones (opcional)

Las graduaciones son las líneas de cuadrícula radiales que mejoran la legibilidad. Solo están disponibles a partir de la versión 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Si utilizas una versión anterior de Aspose.Words, esta línea lanzará una excepción; por lo tanto, verifica primero la versión de tu biblioteca.

## Paso 6: Establecer las dimensiones del gráfico

Controlar el tamaño del gráfico te permite ajustarlo adecuadamente dentro de los márgenes de la página. Esto aborda **cómo establecer el tamaño del gráfico**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Puedes ajustar los valores de ancho y alto para que coincidan con tus necesidades de diseño. Recuerda que 1 punto ≈ 1/72 pulgada.

## Paso 7: Insertar el gráfico en el documento Word

Ahora el gráfico está listo para ser colocado. El método `insertChart` de `DocumentBuilder` se encarga de la inserción.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Este es el núcleo de la operación de **insertar gráfico en Word**.

## Paso 8: Guardar el documento

Finalmente, escribe el documento en disco. El archivo contendrá el gráfico radial que acabas de crear.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Ejecutar el programa genera `RadialChart.docx` en el directorio de trabajo del proyecto. Al abrir el archivo en Microsoft Word se muestra un gráfico radial con tres puntos de datos y graduaciones visibles.

### Resultado esperado

* Un archivo Word llamado `RadialChart.docx`
* Dentro del archivo, una sola página que contiene un gráfico radial de tamaño 400 × 300 puntos
* El gráfico muestra una serie titulada **Series 1** con valores **10, 20, 30**
* Las graduaciones (líneas de cuadrícula radiales) son visibles alrededor del gráfico

## Variaciones comunes y casos límite

| Situación | Qué cambiar | Razón |
|-----------|----------------|--------|
| **Multiple series** | Call `chart.getSeries().add(...)` for each series | Permite la visualización comparativa de datos |
| **Different chart type** | Replace `ChartType.RADIAL` with `ChartType.COLUMN` (or any other) | Usa el tipo de gráfico que mejor represente tus datos |
| **Custom colors** | Access `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Mejora la identidad visual |
| **Older Aspose.Words version** | Omit the `setShowGraduations` line or upgrade the library | Previene `NoSuchMethodError` |
| **Saving to a different format** | Use `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Genera un PDF en lugar de un DOCX |

## Ejemplo completo ejecutable

A continuación se muestra el programa Java completo y autónomo. Cópialo en un archivo llamado `RadialChartExample.java`, agrega la dependencia de Aspose.Words y ejecútalo.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Conclusión

Ahora sabes cómo **crear un gráfico radial** programáticamente, **agregar serie de datos al gráfico**, controlar **cómo establecer el tamaño del gráfico**, y **insertar el gráfico en Word** partiendo de un **documento Word en blanco**. El ejemplo usa Aspose.Words for Java 24.9, pero los mismos conceptos se aplican a otras bibliotecas de gráficos que exponen una API similar.

### Próximos pasos

* Explora otros tipos de gráficos (`ChartType.PIE`, `ChartType.LINE`, etc.) – esto vuelve a la palabra clave secundaria **insertar gráfico en Word**.
* Personaliza las etiquetas de los ejes, leyendas y colores para que coincidan con las directrices de tu marca.
* Genera gráficos dinámicamente a partir de consultas a bases de datos o archivos CSV.
* Convierte el `.docx` resultante a PDF para su distribución (`doc.save("output.pdf", SaveFormat.PDF)`).

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Crear documento Word Java – Agregar forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insertar gráfico de áreas en un documento Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}