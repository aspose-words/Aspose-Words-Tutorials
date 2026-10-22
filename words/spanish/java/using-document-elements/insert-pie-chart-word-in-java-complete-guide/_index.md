---
category: general
date: 2026-09-24
description: Insertar un gráfico circular en un DOCX usando Aspose.Words para Java.
  Aprende a establecer el tamaño del agujero, explotar una porción del pastel, resaltar
  una porción del gráfico circular y crear un gráfico DOCX sin esfuerzo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: es
lastmod: 2026-09-24
og_description: Inserte un gráfico de pastel en un DOCX con Aspose.Words para Java.
  Domine la configuración del tamaño del agujero, la explosión y el resaltado de porciones
  del gráfico de pastel, y cree un gráfico DOCX en minutos.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Insertar gráfico de pastel en Java – tutorial paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Insertar palabra de gráfico de pastel en Java – guía completa
url: /es/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar pie chart word en Java – guía completa

Si necesita **insert pie chart word** en un archivo DOCX, este tutorial le muestra exactamente cómo hacerlo con Aspose.Words for Java. Verá el flujo de trabajo completo, desde crear el documento hasta personalizar el gráfico para que la porción se explote, el tamaño del agujero se establezca en cero y la porción se resalte.

Trabajar con gráficos en documentos de Word a menudo parece una preocupación separada del procesamiento de texto regular, pero Aspose.Words unifica ambos. En los pasos siguientes también aprenderá a **create docx chart** archivos que están listos para abrirse en Microsoft Word, Google Docs o cualquier otro visor compatible con DOCX.

## Lo que lograrás

* **Insert pie chart word** en un documento en blanco  
* **Set hole size** para convertir el gráfico en un pastel completo (sin dona)  
* **Explode pie slice** para llamar la atención a un segmento específico  
* **Highlight pie chart slice** con formato personalizado  
* **Create docx chart** que pueda compartirse o editarse más adelante  

### Requisitos previos

* Java 17 o posterior (el código también se compila con Java 8)  
* Biblioteca Aspose.Words for Java (versión 23.9 o más reciente)  
* Un IDE o herramienta de compilación (Maven/Gradle) que pueda resolver la dependencia de Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Cómo insertar pie chart word en un DOCX usando Aspose.Words

El primer paso es crear un nuevo documento en blanco y obtener un `DocumentBuilder`. El builder le brinda acceso directo al flujo de contenido del documento, lo que hace trivial **insert pie chart word**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Por qué es importante
`Document` representa todo el archivo Word, mientras que `DocumentBuilder` es la API de alto nivel que le permite insertar párrafos, tablas y gráficos sin lidiar con XML de bajo nivel. Comenzar con un documento limpio garantiza que el gráfico que añada sea el único contenido, lo que es perfecto para aprender o para generar informes basados en plantillas.

## Establecer el tamaño del agujero para crear un pastel completo

Por defecto, Aspose.Words crea un gráfico de dona cuando solicita un gráfico de pastel. Para que el gráfico sea un círculo verdadero, debe **set hole size** a `0`. Esto elimina el agujero interno y produce una apariencia clásica de pastel.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Consejo práctico
Si más adelante decide cambiar a un gráfico de dona, simplemente cambie el valor `holeSize` a un porcentaje (p.ej., `30`). La misma API funciona para ambos tipos de gráficos.

## Explotar una porción del pastel para resaltar un segmento

Explotar una porción la hace sobresalir visualmente. La operación **explode pie slice** mueve la porción elegida hacia afuera en un porcentaje del radio del gráfico.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### ¿Por qué explotar?
Una porción explotada atrae la mirada del lector al punto de datos más importante—perfecto para paneles de control o resúmenes ejecutivos. El valor `20` significa el 20 % del radio; puede ajustarlo entre `0` (sin explosión) y `100` (totalmente separado).

## Resaltar una porción del gráfico circular con formato personalizado

Más allá de la explosión, podría querer **highlight pie chart slice** cambiando su color de relleno o borde. Mientras el código de demostración se centra en la explosión, puede ampliarlo de la siguiente manera:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Nota del experto
Cambiar el color de relleno de una porción específica requiere acceder al objeto `DataPoint`. Si tiene varias series, itere a través de `series.getDataPoints()` y aplique estilos de forma condicional.

## Guardar y verificar el gráfico docx creado

Finalmente, usted **create docx chart** guardando el `Document`. El archivo resultante puede abrirse en Microsoft Word para ver el gráfico circular formateado.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Resultado esperado
Abrir `PieChartFormatted.docx` muestra un solo gráfico circular:

* El gráfico ocupa un área de 400 × 300 pt.  
* El tamaño del agujero es `0`, por lo que el gráfico es un pastel completo.  
* La primera porción está explotada en un 20 % y coloreada de rojo (si añadió el formato opcional).  

Ahora tiene un **create docx chart** que puede distribuirse, incrustarse en correos electrónicos o editarse programáticamente.

---

## Variaciones comunes y casos límite

| Escenario | Cómo adaptar el código |
|----------|----------------------|
| **Multiple series** | Loop over `pieChart.getChart().getSeries()` and set `Explosion` or `FillColor` per series. |
| **Dynamic data** | Populate the series with values from a database or CSV before calling `setExplosion`. |
| **Different chart size** | Change the width/height arguments in `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | After saving the DOCX, call `doc.save("output.pdf")` to produce a PDF version of the same chart. |
| **Localization** | Use `DocumentBuilder.insertChart` with a locale‑specific number format for labels. |

### Consejo profesional
Siempre llame a `setHoleSize(0)` **después** de `insertChart`. Si lo establece antes de la inserción, Aspose.Words revertirá al tamaño de dona predeterminado una vez creado el gráfico.

---

## Resumen

Ahora sabe cómo **insert pie chart word** en un documento Word usando Java, cómo **set hole size** para un aspecto de pastel completo, cómo **explode pie slice** para llamar la atención, y cómo **highlight pie chart slice** con colores personalizados. El ejemplo completo también muestra cómo **create docx chart** archivos que están listos para distribución.

## Próximos pasos

* Explore otros tipos de gráficos (`BAR`, `LINE`, `SCATTER`) con `ChartType`.  
* Combine la generación de gráficos con combinación de correspondencia para producir informes personalizados.  
* Integre el DOCX generado en un servicio web que devuelva el archivo bajo demanda.  

Si encuentra problemas, recuerde verificar que está usando una versión compatible de Aspose.Words y que el directorio de salida exista y sea escribible.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Uso de la API de gráficos de Word](/words/english/net/programming-with-charts/)
- [Insertar un gráfico de burbujas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}