---
date: 2026-02-16
description: Aprenda cómo agregar múltiples series a los gráficos en Aspose.Words
  para Java, cambiar las marcas de graduación del eje, aplicar un formato numérico
  personalizado y generar documentos de Word con gráficos de líneas y columnas.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Agregar varias series a los gráficos en Aspose.Words para Java
url: /es/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar Múltiples Series a Gráficos en Aspose.Words para Java

## Introducción al Uso de Gráficos en Aspose.Words para Java

En este tutorial aprenderá **cómo agregar múltiples series** a un gráfico usando Aspose.Words para Java, por qué personalizar las marcas de graduación del eje y aplicar un formato numérico personalizado es importante, y cómo generar un documento Word con gráficos. Ya sea que necesite un gráfico de líneas para datos financieros o un gráfico de columnas para cifras de ventas, los pasos a continuación lo guiarán en la creación, el estilo y el ajuste fino de los gráficos de forma programática.

## Respuestas Rápidas
- **¿Cómo agrego múltiples series?** Use `chart.getSeries().add(...)` para cada serie que desee mostrar.  
- **¿Puedo cambiar las marcas de graduación del eje?** Sí – use `setMajorTickMark()` y `setMinorTickMark()` en los objetos del eje.  
- **¿Qué formato puedo aplicar a las etiquetas de datos?** Cualquier formato numérico compatible con Excel, por ejemplo, `"$"#,##0.00` o `0.00%`.  
- **¿Qué tipos de gráficos son compatibles?** Línea, columna, área, burbuja, dispersión y muchos más mediante `ChartType`.  
- **¿Se requiere una licencia para producción?** Se necesita una licencia válida de Aspose.Words para Java para la funcionalidad completa.

## ¿Qué significa “agregar múltiples series” en un gráfico?
Agregar múltiples series significa insertar más de un conjunto de datos en la misma área del gráfico, lo que le permite comparar diferentes categorías o períodos de tiempo lado a lado. Cada serie aparece como su propia línea, columna o conjunto de marcadores, ofreciendo a los lectores una historia visual más rica.

## ¿Por qué usar Aspose.Words para Java para generar documentos Word con gráficos?
- **Control total** sobre el tipo de gráfico, diseño y estilo sin abrir Word manualmente.  
- **Generación programática** se adapta a canalizaciones de informes automatizados.  
- **Multiplataforma** – funciona en cualquier entorno compatible con Java.  
- **API rica** para personalizar ejes, etiquetas de datos y formatos numéricos.

## Requisitos Previos
- Java Development Kit (JDK) 8 o superior.  
- Biblioteca Aspose.Words para Java añadida a su proyecto (Maven/Gradle o JAR).  
- Licencia válida de Aspose para producción (opcional para evaluación).

## Guía Paso a Paso

### Paso 1: Crear un gráfico de líneas y **agregar múltiples series**
A continuación se muestra el código principal que crea un gráfico de líneas, elimina las series predeterminadas y luego agrega tres series distintas con etiquetas de datos personalizadas.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

**Consejo profesional:** Llame a `chart.getSeries().add(...)` tantas veces como sea necesario para **agregar múltiples series** – cada llamada crea una nueva línea (o columna, etc.) en el mismo gráfico.

### Paso 2: **Crear un gráfico de columnas** (create column chart java)
El siguiente fragmento muestra cómo insertar un gráfico de columnas simple, útil para comparar categorías lado a lado.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Paso 3: **Cambiar las marcas de graduación del eje** (change axis tick marks)
Personalizar los ejes X y Y mejora la legibilidad. El siguiente código muestra cómo cambiar las marcas de graduación, invertir el orden y establecer puntos de cruce personalizados.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Paso 4: **Aplicar un formato numérico personalizado** (apply custom number format)
Puede formatear los números del eje o las etiquetas de datos con cualquier patrón compatible con Excel. A continuación se muestra un ejemplo conciso que formatea el eje Y con un patrón de separador de miles.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Paso 5: Generar el documento Word final (generate chart word document)
Después de configurar series, ejes y etiquetas, simplemente llame a `doc.save(...)` como se muestra en los fragmentos anteriores. El archivo `.docx` resultante contiene gráficos totalmente funcionales que pueden abrirse y editarse en Microsoft Word.

## Casos de Uso Comunes
- **Paneles financieros** – gráficos de líneas con múltiples series para ingresos, gastos y beneficio.  
- **Informes de ventas** – gráficos de columnas que comparan ventas trimestrales por regiones.  
- **Seguimiento de proyectos** – gráficos de área o de dispersión que visualizan el progreso a lo largo del tiempo.  

## Personalizaciones Adicionales de Gráficos
Más allá de lo básico, puede ajustar límites, ocultar ejes (`axis.setHidden(true)`), cambiar colores, agregar leyendas y más. Consulte la referencia de la API de Aspose.Words para Java para la lista completa de opciones.

## Conclusión
En esta guía cubrimos cómo **agregar múltiples series** a los gráficos, crear tanto gráficos de líneas como de columnas, **cambiar las marcas de graduación del eje**, **aplicar formatos numéricos personalizados**, y finalmente **generar un documento Word con gráficos**. Con Aspose.Words para Java dispone de una forma poderosa, basada en código, para incrustar visualizaciones de datos profesionales directamente en sus documentos.

## Preguntas Frecuentes

**P: ¿Cómo puedo agregar múltiples series a un gráfico?**  
R: Llame a `chart.getSeries().add()` para cada serie que desee mostrar. Cada llamada crea un nuevo conjunto de datos que aparece como su propia línea, columna o grupo de marcadores.

**P: ¿Cómo formateo las etiquetas de datos con un formato numérico personalizado?**  
R: Acceda al objeto `DataLabels` de la serie y use `getNumberFormat().setFormatCode("su patrón")`. También puede vincular el formato a una celda fuente con `isLinkedToSource(true)`.

**P: ¿Cómo puedo cambiar las marcas de graduación del eje?**  
R: Use `setMajorTickMark()` y `setMinorTickMark()` en `ChartAxis`. Las opciones incluyen `CROSS`, `INSIDE`, `OUTSIDE` y `NONE`.

**P: ¿Puedo crear otros tipos de gráficos como de dispersión o de área?**  
R: Sí – especifique el `ChartType` deseado (por ejemplo, `ChartType.SCATTER`, `ChartType.AREA`) al llamar a `builder.insertChart(...)`.

**P: ¿Cómo oculto un eje que no necesito?**  
R: Llame a `axis.setHidden(true)` en el `ChartAxis` que desea ocultar.

---

**Última actualización:** 2026-02-16  
**Probado con:** Aspose.Words para Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}