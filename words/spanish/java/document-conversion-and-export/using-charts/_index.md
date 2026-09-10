---
date: 2025-12-13
description: Aprenda a crear un gráfico de columnas y a dar formato a las etiquetas
  de datos del gráfico con Aspose.Words para Java. Explore cómo agregar múltiples
  series, cambiar el tipo de eje y ocultar el eje del gráfico.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Cómo crear un gráfico de columnas usando Aspose.Words para Java
url: /es/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un gráfico de columnas usando Aspose.Words para Java

En este tutorial usted **creará un gráfico de columnas** visualizaciones directamente dentro de documentos Word usando Aspose.Words for Java. Recorreremos la creación de diferentes tipos de gráficos, la adición de múltiples series, el formato de etiquetas de datos del gráfico, el cambio del tipo de eje e incluso ocultar un eje del gráfico cuando necesite una apariencia más limpia. Al final tendrá un enfoque sólido y listo para producción para incrustar gráficos enriquecidos en sus documentos.

## Respuestas rápidas
- **¿Cuál es la clase principal para crear un gráfico?** `DocumentBuilder` con `insertChart`.
- **¿Qué método agrega una nueva serie?** `chart.getSeries().add(...)`.
- **¿Cómo formateo las etiquetas de datos del gráfico?** Use `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **¿Puedo ocultar un eje?** Sí, llame a `setHidden(true)` en el objeto del eje.
- **¿Necesito una licencia para Aspose.Words?** Se requiere una licencia para uso en producción; hay una prueba gratuita disponible.

## Qué es un gráfico de columnas y por qué usarlo

Un gráfico de columnas muestra datos categóricos como barras verticales, lo que lo hace ideal para comparar valores entre grupos (ventas por región, gastos mensuales, etc.). En aplicaciones Java, generar un gráfico de columnas con Aspose.Words le permite incrustar estas visualizaciones directamente en archivos Word / DOCX sin necesidad de Excel ni herramientas externas.

## Cómo crear un gráfico de columnas

A continuación se muestra un ejemplo sencillo que crea un gráfico de columnas simple. El código es idéntico al fragmento original; solo hemos añadido comentarios explicativos para facilitar su comprensión.

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

### Añadir múltiples series

Puede **añadir múltiples series** a un gráfico de columnas llamando a `chart.getSeries().add(...)` repetidamente, como se muestra arriba. Cada serie puede tener su propio conjunto de categorías y valores, lo que le permite comparar varios conjuntos de datos lado a lado.

## Cómo crear un gráfico de líneas con etiquetas de datos personalizadas

Si necesita un gráfico de líneas en lugar de un gráfico de columnas, se aplica el mismo patrón. Este ejemplo también demuestra **formatear las etiquetas de datos del gráfico** con diferentes formatos numéricos.

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

### Añadir etiquetas de datos

La llamada `series1.hasDataLabels(true)` **añade etiquetas de datos** a la serie, mientras que `setShowValue(true)` hace que los valores reales sean visibles en el gráfico.

## Cómo cambiar el tipo de eje y personalizar las propiedades del eje

Cambiar el tipo de eje (p. ej., de fecha a categoría) le permite controlar cómo se trazan los puntos de datos. Este fragmento también muestra cómo **ocultar el eje del gráfico** si prefiere un diseño minimalista.

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

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Cambiar el tipo de eje

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **cambia el tipo de eje** de un eje basado en fechas a uno categórico, dándole control total sobre la ubicación de las etiquetas.

## Cómo formatear las etiquetas de datos del gráfico (formatos numéricos)

Puede aplicar formato numérico directamente al eje o a las etiquetas de datos. Este ejemplo formatea los números del eje Y con un separador de miles.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Personalizaciones adicionales del gráfico

Más allá de lo básico, puede ajustar los límites, establecer unidades de intervalo entre etiquetas, ocultar ejes específicos y más. Consulte la documentación de la API de Aspose.Words for Java para obtener una lista completa de propiedades.

## Preguntas frecuentes

**Q: ¿Cómo puedo añadir múltiples series a un gráfico?**  
**A:** Use `chart.getSeries().add()` para cada serie que desee mostrar. Cada llamada puede proporcionar un nombre único, una matriz de categorías y una matriz de valores.

**Q: ¿Cómo formateo las etiquetas de datos del gráfico con formatos numéricos personalizados?**  
**A:** Acceda al objeto `DataLabels` de una serie y llame a `getNumberFormat().setFormatCode("su formato")`. También puede vincular el formato a una celda de origen con `isLinkedToSource(true)`.

**Q: ¿Cómo puedo ocultar un eje del gráfico?**  
**A:** Llame a `setHidden(true)` en el `ChartAxis` que desea ocultar (p. ej., `chart.getAxisY().setHidden(true)`).

**Q: ¿Cuál es la mejor manera de cambiar el tipo de eje?**  
**A:** Use `setCategoryType(AxisCategoryType.CATEGORY)` para ejes categóricos o `AxisCategoryType.DATE` para ejes de fecha.

**Q: ¿Cómo añado etiquetas de datos a una serie?**  
**A:** Habilítelas con `series.hasDataLabels(true)` y luego configure la visibilidad usando `series.getDataLabels().setShowValue(true)`.

## Conclusión

Hemos cubierto todo lo que necesita para **crear visualizaciones de gráficos de columnas** con Aspose.Words for Java, desde insertar gráficos básicos y añadir múltiples series, hasta formatear las etiquetas de datos del gráfico, cambiar el tipo de eje y ocultar ejes del gráfico para una apariencia limpia. Incorpore estas técnicas en sus flujos de trabajo de informes o generación de documentos para ofrecer documentos Word profesionales y basados en datos.

---

**Última actualización:** 2025-12-13  
**Probado con:** Aspose.Words for Java 24.12 (última)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}