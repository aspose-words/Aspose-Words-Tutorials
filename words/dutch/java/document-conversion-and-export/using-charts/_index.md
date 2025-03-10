---
title: Grafieken gebruiken in Aspose.Words voor Java
linktitle: Grafieken gebruiken
second_title: Aspose.Words Java Documentverwerkings-API
description: Leer hoe u grafieken maakt en aanpast in Aspose.Words voor Java. Ontdek grafiektypen, opmaak en aseigenschappen voor datavisualisatie.
weight: 12
url: /nl/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grafieken gebruiken in Aspose.Words voor Java


## Inleiding tot het gebruik van grafieken in Aspose.Words voor Java

In deze tutorial gaan we onderzoeken hoe je met grafieken kunt werken met Aspose.Words voor Java. Je leert hoe je verschillende soorten grafieken kunt maken, aseigenschappen kunt aanpassen, gegevenslabels kunt opmaken en meer. Laten we erin duiken!

## Een lijndiagram maken

Gebruik de volgende code om een lijndiagram te maken:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Standaard gegenereerde series verwijderen.
chart.getSeries().clear();

// Een serie met gegevens en gegevenslabels toevoegen.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Of koppel de opmaakcode aan een broncel.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Andere soorten grafieken maken

U kunt verschillende typen grafieken maken, zoals kolom-, vlak-, bubbel-, spreidings- en meerdiagrammen met vergelijkbare technieken. Hier is een voorbeeld van het invoegen van een eenvoudig kolomdiagram:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Standaard gegenereerde series verwijderen.
chart.getSeries().clear();

// Categorieën maken en gegevens toevoegen.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## As-eigenschappen aanpassen

U kunt aseigenschappen aanpassen, zoals het astype wijzigen, maatstreepjes instellen, labels opmaken en meer. Hier is een voorbeeld van het definiëren van XY-aseigenschappen:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Wis de standaardreeks en voeg uw gegevens toe.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Wijzig de X-as zodat deze een categorie weergeeft in plaats van een datum.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //Gemeten in weergave-eenheden van de Y-as (honderden).
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

## Gegevenslabels opmaken

U kunt gegevenslabels opmaken met verschillende getalformaten. Hier is een voorbeeld:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Wis de standaardreeks en voeg uw gegevens toe.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Extra grafiekaanpassingen

U kunt uw diagrammen verder aanpassen door grenzen, intervaleenheden tussen labels aan te passen, diagramassen te verbergen en meer. Bekijk de meegeleverde codefragmenten om meer te weten te komen over deze opties.

## Conclusie

In deze tutorial hebben we onderzocht hoe u met diagrammen kunt werken met Aspose.Words voor Java. U hebt geleerd hoe u verschillende typen diagrammen kunt maken, aseigenschappen kunt aanpassen, gegevenslabels kunt opmaken en meer. Aspose.Words voor Java biedt krachtige tools voor het toevoegen van visuele representaties van gegevens aan uw documenten, waardoor u de manier waarop u informatie presenteert, kunt verbeteren.

## Veelgestelde vragen

### Hoe kan ik meerdere reeksen aan een grafiek toevoegen?

 U kunt meerdere reeksen aan een grafiek toevoegen met behulp van de`chart.getSeries().add()` methode. Zorg ervoor dat u de serienaam, categorieën en gegevenswaarden opgeeft.

### Hoe kan ik gegevenslabels opmaken met aangepaste getalnotaties?

 kunt gegevenslabels opmaken door toegang te krijgen tot de`DataLabels` eigenschappen van een reeks en het instellen van de gewenste opmaakcode met behulp van`getNumberFormat().setFormatCode()`.

### Hoe pas ik aseigenschappen in een grafiek aan?

 U kunt aseigenschappen zoals type, maatstreepjes, labels en meer aanpassen via de`ChartAxis` eigenschappen zoals`setCategoryType()`, `setCrosses()` , En`setMajorTickMark()`.

### Hoe kan ik andere soorten diagrammen maken, zoals spreidings- of vlakdiagrammen?

 U kunt verschillende grafiektypen maken door de juiste`ChartType` bij het invoegen van de grafiek met behulp van`builder.insertChart(ChartType.TYPE, width, height)`.

### Hoe kan ik een grafiekas verbergen?

 U kunt een grafiekas verbergen door de`setHidden(true)` Eigenschap van de as.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
