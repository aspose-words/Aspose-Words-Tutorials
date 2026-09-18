---
category: general
date: 2026-09-18
description: Aprende cómo crear un gráfico radial en un documento de Word usando Java,
  agregar etiquetas de datos al gráfico e insertar datos de series con un ejemplo
  de código completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: es
lastmod: 2026-09-18
og_description: Crear un gráfico radial en un documento de Word usando Java, añadir
  etiquetas de datos al gráfico e insertar datos de series en un único tutorial.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Crear gráfico radial en Word con Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Cómo crear un gráfico radial en un documento de Word con Java
url: /es/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico radial en un documento Word con Java

Si necesitas crear un gráfico radial en un documento Word, esta guía te muestra los pasos exactos. También aprenderás cómo agregar etiquetas de datos al gráfico e insertar datos de series para que el gráfico esté listo para su presentación.

Generar un gráfico programáticamente elimina el trabajo manual de formato y garantiza la consistencia en los informes. El tutorial asume que tienes conocimientos básicos de Java y una versión reciente de la biblioteca Aspose.Words for Java instalada.

## Lo que necesitarás

* Java 17 o superior  
* Aspose.Words for Java (versión 23.12 o posterior)  
* Un IDE o herramienta de compilación que pueda resolver dependencias Maven/Gradle  

Tener estos requisitos instalados te permite ejecutar el ejemplo sin configuración adicional.

## Cómo crear un gráfico radial en un documento Word

El primer paso es crear un archivo Word en blanco que alojará el gráfico. Un documento vacío proporciona un lienzo limpio y evita estilos no deseados.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo el archivo .docx, mientras que `DocumentBuilder` suministra métodos para insertar elementos como párrafos, tablas y gráficos.

## Cómo insertar el gráfico

A continuación insertas el propio gráfico. El método `insertChart` crea un objeto de gráfico y lo coloca en la posición actual del cursor del builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Un gráfico polar representa los puntos de datos alrededor de un eje central, lo que es ideal para mostrar información cíclica. Las dimensiones se expresan en puntos (1 pt ≈ 1/72 pulgada).

## Agregar datos de series al gráfico

Un gráfico sin datos de series está vacío. Puedes agregar una serie manualmente o enlazarla a una fuente de datos. El ejemplo a continuación agrega una única serie con tres puntos de datos.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` recibe un nombre de serie, una lista de etiquetas de categoría y una lista de valores numéricos correspondientes. Puedes repetir este bloque para agregar series adicionales (`addSeriesData`).

## Agregar etiquetas de datos al gráfico para la primera serie

Las etiquetas de datos hacen que el gráfico sea legible sin pasar el cursor sobre los puntos. La siguiente línea activa las etiquetas de valor para la primera serie.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Configurar `showValue` a `true` muestra el valor de cada punto directamente en el gráfico. También puedes habilitar nombres de categoría, porcentajes o líneas guía mediante el mismo objeto `DataLabelFormat`.

## Guardar el archivo Word

Una vez configurado el gráfico, escribe el documento en disco. Elige una ubicación a la que tu aplicación pueda acceder.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

El archivo `RadialChart.docx` ahora contiene un gráfico radial totalmente funcional con etiquetas de datos.

## Ejemplo completo

A continuación se muestra un programa autocontenido que puedes copiar, compilar y ejecutar. Demuestra el flujo de trabajo completo, desde crear un documento Word en blanco hasta guardar un gráfico radial con etiquetas de datos.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Resultado esperado**

Al abrir `output/RadialChart.docx` en Microsoft Word, verás un gráfico radial titulado *Quarterly Sales*. Cada punto muestra su valor numérico (p. ej., “15000”) junto al marcador.

## Variaciones comunes y casos límite

| Situación | Cambio recomendado |
|-----------|--------------------|
| Necesitas un tipo de gráfico diferente | Reemplaza `ChartType.POLAR` por cualquier otro valor del enum `ChartType` (p. ej., `ChartType.COLUMN`). |
| El gráfico debe usar un rango de Excel externo | Usa `chart.setDataRange("Sheet1!A1:B5")` después de crear el gráfico y cargar el libro de trabajo. |
| Quieres ocultar la leyenda | `chart.getLegend().setVisible(false);` |
| El documento debe guardarse como PDF | Llama a `doc.save("RadialChart.pdf");` – Aspose.Words convierte automáticamente el gráfico. |

Estos ajustes mantienen la lógica central intacta mientras adaptan la salida a requisitos específicos.

## Consejos profesionales

* **Reutiliza el builder** – Puedes insertar varios gráficos en el mismo documento llamando a `builder.insertChart` repetidamente.  
* **Rendimiento** – Al generar muchos gráficos, crea una única instancia de `DocumentBuilder` y reutilízala para reducir la sobrecarga de asignación de objetos.  
* **Estilizado** – La apariencia del gráfico (colores, grosor de línea) se controla mediante los métodos del objeto `Chart` como `getSeries().get(i).getFormat()`. Experimenta con estas configuraciones para que coincidan con la identidad corporativa.

## Conclusión

Ahora sabes cómo crear un gráfico radial en un documento Word con Java, agregar datos de series y etiquetas de datos antes de guardar el archivo. El ejemplo completo puede ampliarse para manejar series adicionales, estilos personalizados o formatos de salida alternativos.

Explora temas relacionados como **cómo insertar un gráfico** desde fuentes de datos externas, **crear documentos Word en blanco** con plantillas predefinidas y **agregar datos de series** dinámicamente desde bases de datos. Experimenta con diferentes tipos de gráficos para descubrir cuál comunica mejor tus datos.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Crear documento Word Java – Agregar forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Establecer opciones predeterminadas para etiquetas de datos en un gráfico](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}