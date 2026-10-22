---
category: general
date: 2026-10-07
description: Aprende a crear un gráfico circular en Word, agregar series de datos
  y guardar el gráfico como PNG usando Java. Sigue la guía paso a paso para obtener
  resultados rápidos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: es
lastmod: 2026-10-07
og_description: 'Crear un gráfico circular en Word rápidamente: este tutorial muestra
  cómo añadir series de datos, generar el gráfico y guardar el gráfico de Word como
  una imagen (PNG). Sigue el ejemplo de código completo.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Crear un gráfico circular en Word y exportarlo como PNG – guía
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Cómo crear un gráfico circular en Word y guardarlo como PNG
url: /es/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico de pastel en Word y guardarlo como PNG

Si necesitas **crear gráficos de pastel** dentro de un archivo Microsoft Word, esta guía te muestra exactamente cómo hacerlo con Java. También aprenderás cómo **agregar series de datos** al gráfico y **guardar el gráfico como PNG** para que la visualización pueda reutilizarse fuera de Word.

Generar un gráfico directamente en un documento te ahorra exportar datos a una herramienta gráfica separada. Al final de este tutorial tendrás un archivo Word completamente funcional que contiene un gráfico de pastel y una imagen PNG correspondiente en el disco.

## Requisitos previos

* Java 17 o posterior instalado.
* El **GroupDocs.Viewer for Java** (o una biblioteca compatible que proporcione las clases `Document`, `Chart`, `ChartType` y `ImageSaveOptions`).
* Un proyecto Maven o Gradle donde puedas agregar la dependencia de la biblioteca.
* Un documento Word de entrada (`input.docx`) ubicado en una carpeta a la que puedas referenciar desde el código.

Si estás usando Maven, agrega la dependencia (reemplaza `VERSION` con la última versión):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Cómo crear un gráfico de pastel en Word

El núcleo de la solución gira en torno a tres acciones:

1. Cargar el archivo `.docx` de origen.
2. **Agregar series de datos** a un nuevo objeto `Chart` de tipo `PIE`.
3. **Guardar el gráfico como PNG** para obtener un archivo de imagen junto al documento Word.

A continuación, cada paso se explica en detalle, seguido del código Java exacto que necesitas.

### Paso 1: Cargar el documento de origen

Debes abrir el archivo Word que alojará el gráfico. La clase `Document` lee el contenido `.docx` en memoria.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Por qué es importante*: Cargar el documento crea un modelo mutable. Todas las operaciones de gráfico posteriores modifican esta representación en memoria, que luego persistes de nuevo en el disco.

### Paso 2: Agregar series de datos al gráfico

Crear un **gráfico de pastel** comienza con una instancia de `Chart`. El constructor recibe el `Document` padre y el tipo de gráfico (`ChartType.PIE`). Después de que el objeto chart exista, lo rellenas con valores numéricos y etiquetas opcionales.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Por qué es importante*: El método `add` **agrega series de datos** al gráfico. Cada entrada en `values` se convierte en una porción del pastel, mientras que `categories` proporcionan las etiquetas de la leyenda. Puedes suministrar cualquier número de puntos; la biblioteca calculará automáticamente los ángulos de las porciones.

### Paso 3: Guardar el gráfico como PNG

Una vez que el gráfico forma parte del documento, puedes exportar la representación visual. El método `save` del objeto chart subyacente escribe un archivo PNG en el sistema de archivos.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Por qué es importante*: Guardar el gráfico como PNG te brinda una imagen raster que puede incrustarse en páginas web, correos electrónicos o informes sin requerir el archivo Word original. El objeto `ImageSaveOptions` te permite controlar el formato, la resolución y otras configuraciones de exportación.

## Generar gráfico de pastel en Word – personalizando la apariencia

Más allá de los pasos básicos, podrías querer personalizar colores, títulos o etiquetas de datos. La mayoría de las bibliotecas exponen un objeto `ChartOptions` o similar. Aquí tienes un ejemplo rápido que agrega un título y cambia los colores de las porciones:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Estas personalizaciones son opcionales pero ilustran cómo puedes **generar un gráfico de pastel en Word** que coincida con tu marca.

## Guardar gráfico de Word como imagen – enfoques alternativos

Si solo necesitas la imagen y no el gráfico dentro del documento, puedes omitir la inserción de la forma del gráfico en el archivo Word y llamar directamente al método `save` después de crear el gráfico. El código permanece igual; simplemente omites los pasos que agregan el gráfico al cuerpo del documento.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Esta técnica es útil cuando generas muchos gráficos en un proceso por lotes y solo te importa la salida PNG.

## Ejemplo completo ejecutable

Copia la siguiente clase en tu proyecto, ajusta las rutas de archivo y ejecútala. El programa:

1. Cargar `input.docx`.
2. **Crear un gráfico de pastel**, **agregar series de datos** y incrustarlo en el documento.
3. **Guardar el gráfico como PNG** (`radial.png`).
4. Persistir el archivo Word modificado como `output.docx`.



## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Crear gráfico de dispersión en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}