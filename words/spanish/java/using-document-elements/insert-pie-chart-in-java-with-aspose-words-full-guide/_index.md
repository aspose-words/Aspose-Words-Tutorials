---
category: general
date: 2026-07-29
description: Inserte un gráfico circular usando Aspose.Words para Java y aprenda cómo
  generar un gráfico de rosquilla, formatear el gráfico circular, formatear el gráfico
  en Word y personalizar el tamaño del gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: es
lastmod: 2026-07-29
og_description: Inserte un gráfico circular con Aspose.Words para Java y aprenda rápidamente
  a generar un gráfico de rosquilla, formatear el gráfico circular, formatear el gráfico
  en Word y personalizar el tamaño del gráfico para documentos profesionales.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Insertar gráfico circular en Java – Tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Insertar gráfico circular en Java con Aspose.Words – Guía completa
url: /es/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar gráfico circular en Java con Aspose.Words – Guía completa

¿Alguna vez te has preguntado cómo **insertar un gráfico circular** en un documento Word desde código Java? No eres el único: muchos desarrolladores se topan con este obstáculo cuando necesitan una forma rápida y programática de visualizar datos. ¿La buena noticia? Con Aspose.Words para Java puedes hacerlo en unas pocas líneas y, de paso, también **generar un gráfico de rosquilla**, **formatear el gráfico circular**, **formatear el gráfico en Word** y **personalizar el tamaño del gráfico** para que coincida con tu marca.

En este tutorial recorreremos un ejemplo real que comienza creando un documento en blanco, inserta un gráfico circular, ajusta algunas propiedades visuales y, finalmente, guarda el archivo. Al terminar tendrás un fragmento reutilizable que puedes pegar en cualquier proyecto Java que necesite automatizar gráficos. Sin bibliotecas extra, sin manipular manualmente la interop de Office: solo Java limpio y compilado.

## Lo que necesitarás

- **Java 17** (o cualquier JDK reciente; la API es compatible con versiones anteriores)
- **Aspose.Words for Java** 22.12 o superior – puedes obtener el artefacto Maven o el .jar desde el sitio de Aspose.
- Un IDE modesto (IntelliJ IDEA, Eclipse, VS Code…) – cualquier cosa que te permita ejecutar un método `main`.
- Opcional: un archivo de licencia si no deseas la marca de agua de evaluación.

Si ya cuentas con todo esto, podemos pasar directamente al código.

## Paso 1: Insertar gráfico circular con Aspose.Words

Lo primero que hacemos es **insertar un gráfico circular** en un documento nuevo. Este paso prepara el escenario para todo lo demás, porque el objeto del gráfico nos da acceso a series, puntos de datos y ajustes visuales.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Por qué es importante:** `DocumentBuilder.insertChart` no solo crea el gráfico sino que también devuelve un objeto `Chart` que podemos manipular. Los argumentos de ancho y alto te permiten **personalizar el tamaño del gráfico** en el momento de la creación, de modo que no necesitas redimensionarlo después.

## Paso 2: Generar gráfico de rosquilla (opcional)

Si tu diseño requiere un agujero en el centro —piensa en un clásico gráfico de rosquilla— Aspose lo hace con una sola línea. La misma instancia `Chart` puede cambiarse de un gráfico circular normal a una rosquilla ajustando el tamaño del agujero.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Consejo:** El tamaño del agujero solo tiene efecto para `ChartType.DONUT`. Si mantienes el tipo como `PIE`, la llamada se ignora, así que siéntete libre de experimentar.

## Paso 3: Formatear las porciones del gráfico circular

Una buena visualización a menudo destaca una porción en particular. Aquí **formateamos el gráfico circular** explotando la primera porción 20 puntos hacia afuera. Esto atrae la mirada del lector al punto de datos más importante.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** Puedes iterar sobre `pieChart.getSeries()` si tienes varias series y establecer colores, bordes o etiquetas de datos individuales. Esa es la forma de **formatear el gráfico en Word** con un estilo rico.

## Paso 4: Añadir datos al gráfico

Un gráfico sin datos es solo una forma decorativa. Alimentémoslo con un conjunto de datos sencillo —por ejemplo, cifras de ventas trimestrales.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Por qué lo hacemos:** Al añadir explícitamente objetos `ChartPoint` garantizamos que el gráfico refleje nuestra lógica de negocio. Las llamadas `setShowCategoryName` y `setShowValue` forman parte del **formateo del gráfico circular** para mostrar tanto etiquetas como valores.

## Paso 5: Ajustar la apariencia (personalizar tamaño y estilo del gráfico)

Más allá de las dimensiones iniciales, quizá quieras afinar la leyenda, el título o incluso la fuente usada en las etiquetas de datos. Todo esto forma parte de **personalizar el tamaño del gráfico** y del formato general.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Caso límite:** Si más adelante decides exportar el documento a PDF, los datos vectoriales del gráfico permanecen nítidos porque el tamaño está definido en puntos, no en píxeles. Eso es una ventaja para **formatear el gráfico en Word** y los formatos posteriores.

## Paso 6: Guardar y visualizar el documento

El paso final es tan sencillo como llamar a `doc.save`. Esto escribe un archivo `.docx` que puedes abrir en Microsoft Word, LibreOffice o cualquier visor que soporte el formato OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Resultado:** Abre `PieChart.docx` y verás un gráfico circular (o rosquilla) de tamaño adecuado con una porción explotada, un título y una leyenda, todo generado sin tocar la interfaz de usuario.

### Resultado esperado

| Elemento | Lo que verás |
|----------|--------------|
| Tipo de gráfico | Gráfico circular (o rosquilla si `holeSize` > 0) |
| Explosión de porción | Primera porción desplazada 20 pts |
| Leyenda | Posicionada a la derecha |
| Título | “Distribución de ventas trimestrales” en negrita 14 pt |
| Etiquetas de datos | Nombre de categoría y valor mostrados en cada porción |
| Documento | Un archivo Word `.docx` estándar listo para compartir |

## Preguntas frecuentes y trampas comunes

- **¿Necesito una licencia?**  
  La versión de evaluación funciona bien para pruebas, pero añade una marca de agua. Coloca tu archivo `aspose.words.lic` en el classpath para obtener una salida limpia.

- **¿Puedo usar esto con Maven?**  
  Por supuesto. Añade la siguiente dependencia a tu `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **¿Qué pasa si tengo más de una serie?**  
  Recorre `pieChart.getSeries()` y aplica `setExplosion`, `setFillColor` u otro formato por serie. Esa es la forma de **formatear el gráfico circular** para datos multidimensionales.

- **¿El gráfico es editable en Word después de generarse?**  
  Sí—una vez guardado, puedes abrir el documento y ajustar manualmente colores, fuentes o incluso convertir el gráfico circular en un gráfico de barras si lo necesitas.

## Conclusión

Acabamos de **insertar un gráfico circular** en un documento Word usando Aspose.Words para Java, mostramos cómo **generar un gráfico de rosquilla**, demostramos varias formas de **formatear el gráfico circular**, cubrimos buenas prácticas de **formatear el gráfico en Word** y aprendimos a **personalizar el tamaño del gráfico** para lograr un aspecto pulido. El ejemplo completo y ejecutable anterior puede incorporarse a cualquier proyecto Java, dándote automatización de gráficos al instante sin la sobrecarga de la interop COM o instalaciones de Office.

¿Qué sigue? Prueba cambiar la fuente de datos por una base de datos en vivo, añade colores condicionales según umbrales o exporta el mismo documento a PDF para un informe listo para imprimir. Cada uno de esos pasos se basa en la base que hemos establecido, por lo que la transición será fluida.

Si encuentras algún obstáculo o tienes ideas para mejoras adicionales—quizá un gráfico de barras apiladas o una línea—deja un comentario abajo. ¡Feliz creación de gráficos!

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Formatear número de etiqueta de datos en un gráfico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formato numérico para eje en un gráfico](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}