---
title: Uso de gráficos en Aspose.Words para Java
linktitle: Uso de gráficos
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a crear y personalizar gráficos en Aspose.Words para Java. Explore los tipos de gráficos, el formato y las propiedades de los ejes para la visualización de datos.
weight: 12
url: /es/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uso de gráficos en Aspose.Words para Java


## Introducción al uso de gráficos en Aspose.Words para Java

En este tutorial, exploraremos cómo trabajar con gráficos utilizando Aspose.Words para Java. Aprenderá a crear varios tipos de gráficos, personalizar propiedades de ejes, dar formato a etiquetas de datos y más. ¡Vamos a profundizar!

## Creación de un gráfico de líneas

Para crear un gráfico de líneas, utilice el siguiente código:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Eliminar la serie generada por defecto.
chart.getSeries().clear();

// Agregar una serie con datos y etiquetas de datos.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// O vincular el código de formato a una celda de origen.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Creación de otros tipos de gráficos

Puede crear distintos tipos de gráficos, como gráficos de columnas, de áreas, de burbujas, de dispersión y otros, utilizando técnicas similares. A continuación, se muestra un ejemplo de inserción de un gráfico de columnas simple:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Eliminar la serie generada por defecto.
chart.getSeries().clear();

// Creando categorías y añadiendo datos.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Personalización de las propiedades de los ejes

Puede personalizar las propiedades de los ejes, como cambiar el tipo de eje, establecer marcas de graduación, dar formato a las etiquetas y más. A continuación, se muestra un ejemplo de cómo definir las propiedades del eje XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Borre la serie predeterminada y agregue sus datos.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Cambie el eje X para que sea una categoría en lugar de una fecha.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //Medido en unidades de visualización del eje Y (centenas).
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

## Formato de etiquetas de datos

Puede formatear las etiquetas de datos con distintos formatos de números. A continuación, se muestra un ejemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Borre la serie predeterminada y agregue sus datos.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Personalizaciones adicionales de gráficos

Puede personalizar aún más sus gráficos ajustando los límites, las unidades de intervalo entre las etiquetas, ocultando los ejes del gráfico y más. Explore los fragmentos de código proporcionados para obtener más información sobre estas opciones.

## Conclusión

En este tutorial, hemos explorado cómo trabajar con gráficos utilizando Aspose.Words para Java. Aprendió a crear varios tipos de gráficos, personalizar propiedades de ejes, dar formato a etiquetas de datos y más. Aspose.Words para Java proporciona herramientas poderosas para agregar representaciones visuales de datos a sus documentos, mejorando la forma en que presenta la información.

## Preguntas frecuentes

### ¿Cómo puedo agregar varias series a un gráfico?

 Puede agregar varias series a un gráfico utilizando el`chart.getSeries().add()` método. Asegúrese de especificar el nombre de la serie, las categorías y los valores de los datos.

### ¿Cómo puedo formatear etiquetas de datos con formatos numéricos personalizados?

Puede formatear las etiquetas de datos accediendo a`DataLabels` Propiedades de una serie y configuración del código de formato deseado mediante`getNumberFormat().setFormatCode()`.

### ¿Cómo personalizo las propiedades del eje en un gráfico?

 Puede personalizar las propiedades del eje, como el tipo, las marcas de graduación, las etiquetas y más, accediendo a`ChartAxis` Propiedades como`setCategoryType()`, `setCrosses()` , y`setMajorTickMark()`.

### ¿Cómo puedo crear otros tipos de gráficos como gráficos de dispersión o de área?

 Puede crear varios tipos de gráficos especificando los elementos apropiados.`ChartType` al insertar el gráfico utilizando`builder.insertChart(ChartType.TYPE, width, height)`.

### ¿Cómo puedo ocultar un eje de gráfico?

 Puede ocultar un eje de gráfico configurando el`setHidden(true)` propiedad del eje.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
