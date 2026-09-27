---
category: general
date: 2026-09-27
description: Aprende cómo insertar un gráfico circular en un documento de Word con
  Java, crear un gráfico circular en Word y mostrar los porcentajes en el gráfico
  para una visión clara de los datos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: es
lastmod: 2026-09-27
og_description: Cómo insertar un gráfico circular en un documento de Word con Java.
  Esta guía te muestra cómo crear un gráfico circular en Word, mostrar porcentajes
  en el gráfico circular y añadir líneas guía.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Cómo insertar un gráfico circular en un documento de Word usando Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Cómo insertar un gráfico de pastel en un documento de Word usando Java
url: /es/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar un gráfico circular en un documento Word usando Java

Si necesitas **cómo insertar un gráfico circular** en un archivo Word, esta guía te lleva a través del proceso completo. Verás cómo **crear un gráfico circular en Word**, mostrar porcentajes en cada porción y agregar líneas guía para un aspecto pulido.

La automatización de Word a menudo parece pesada, pero con Aspose.Words para Java puedes generar documentos totalmente formateados de forma programática. Al final de este tutorial tendrás un fragmento de Java ejecutable que produce un documento Word que contiene un gráfico circular con estilo.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- Java 17 o posterior instalado
- Maven o Gradle para gestionar dependencias
- Aspose.Words para Java (versión 23.11 o más reciente) añadido a tu proyecto
- Familiaridad básica con la sintaxis de Java

No necesitas experiencia previa con APIs de gráficos; los pasos a continuación cubren todo, desde la configuración del proyecto hasta el resultado final.

## Paso 1: Configurar la dependencia de Maven

Agrega la biblioteca Aspose.Words a tu `pom.xml`. Esta única dependencia te brinda acceso a `Document`, `DocumentBuilder` y clases de gráficos.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Si usas Gradle, el equivalente es:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Consejo profesional:** Usa la versión estable más reciente para beneficiarte de correcciones de errores y nuevas funciones de gráficos.

## Paso 2: Crear un nuevo documento y un builder

El objeto `Document` representa el archivo Word, mientras que `DocumentBuilder` te permite insertar contenido. Esta es la base para **agregar gráfico al documento Word**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

El builder está ahora listo para colocar objetos en cualquier parte del documento.

## Paso 3: Insertar un gráfico circular

Aspose.Words admite varios tipos de gráficos; elegimos `ChartType.PIE`. El tamaño se expresa en puntos (1 punto = 1/72 de pulgada).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

En esta etapa el gráfico contiene una serie de datos predeterminada con valores de marcador de posición. Puedes reemplazar esos valores más adelante si lo deseas.

## Paso 4: Acceder a la serie del gráfico

Un gráfico circular tiene una única serie que contiene los valores de las porciones. Recupera esa serie para aplicar formato.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Paso 5: Explotar la primera porción

Explotar una porción llama la atención sobre un punto de datos particular. Es una pista visual común cuando deseas resaltar una métrica clave.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Paso 6: Mostrar porcentajes en cada porción

Mostrar porcentajes directamente en el gráfico mejora la comprensión de los datos. Esto satisface el requisito de **mostrar porcentajes en el gráfico circular**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Paso 7: Agregar líneas guía para etiquetas más claras

Las líneas guía conectan las etiquetas de las porciones con sus secciones correspondientes, eliminando ambigüedades. Esto cumple con **cómo agregar líneas guía**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Paso 8: Guardar el documento

Finalmente, escribe el documento en disco. Puedes elegir cualquier carpeta a la que tengas permiso de escritura.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Al ejecutar el programa se crea `output/PieFormatted.docx`. Abre el archivo en Microsoft Word y verás un gráfico circular donde:

- La primera porción está explotada.
- Cada porción muestra su valor porcentual.
- Las líneas guía apuntan desde los porcentajes a las porciones correspondientes.

### Resultado esperado

![Gráfico circular formateado en Word](/images/pie-formatted.png){: .center-image alt="Gráfico circular formateado insertado en un documento Word"}

La captura de pantalla (el texto alternativo utiliza la palabra clave principal) ilustra la apariencia final: un gráfico circular limpio y basado en datos, listo para informes, propuestas o paneles de control.

## Variaciones comunes y casos límite

### Cambiar valores de las porciones

Si necesitas datos personalizados, reemplaza los valores predeterminados de la serie:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Series múltiples (gráfico de dona)

Aunque un gráfico circular simple tiene una serie, Aspose.Words también admite gráficos de dona con series múltiples. Cambia `ChartType.PIE` a `ChartType.DONUT` y repite los pasos de configuración de series.

### Exportar a PDF

Si tu flujo de trabajo posterior requiere PDF, llama a `doc.save("output/PieFormatted.pdf");` después de construir el gráfico. El diseño visual permanece idéntico.

## Listado completo del código fuente

A continuación tienes el archivo Java completo y autocontenido que puedes copiar y pegar en tu IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Compila y ejecuta el programa con `mvn compile exec:java -Dexec.mainClass=PieChartExample` (o el comando equivalente de Gradle). El archivo Word generado contendrá el gráfico circular totalmente formateado.

## Conclusión

Ahora sabes **cómo insertar un gráfico circular** en un documento Word usando Java, **cómo crear un gráfico circular en Word**, **cómo mostrar porcentajes en el gráfico circular** y **cómo agregar gráfico al documento Word** con líneas guía. El ejemplo completo demuestra cada paso, explica por qué el código está escrito de esa manera y ofrece consejos para la personalización.

A continuación, podrías explorar:

- Añadir etiquetas de datos con fuentes personalizadas (**variaciones de mostrar porcentajes en el gráfico circular**)
- Combinar varios gráficos en un solo documento (**caso de uso de agregar gráfico al documento Word**)
- Automatizar la generación de informes con tablas y gráficos juntos

¡Siéntete libre de experimentar con colores, orden de las porciones o exportar a PDF! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ocultar eje del gráfico en un documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Crear un gráfico de líneas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}