---
"description": "Leer hoe u grafieken maakt en aanpast in Aspose.Words voor Java. Ontdek grafiektypen, opmaak en aseigenschappen voor datavisualisatie."
"linktitle": "Grafieken gebruiken"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Grafieken gebruiken in Aspose.Words voor Java"
"url": "/nl/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Grafieken gebruiken in Aspose.Words voor Java


## Inleiding tot het gebruik van grafieken in Aspose.Words voor Java

In deze tutorial onderzoeken we hoe je met grafieken kunt werken met Aspose.Words voor Java. Je leert hoe je verschillende soorten grafieken maakt, aseigenschappen aanpast, gegevenslabels opmaakt en meer. Laten we beginnen!

## Een lijndiagram maken

Gebruik de volgende code om een lijndiagram te maken:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Verwijder standaard gegenereerde series.
chart.getSeries().clear();

// Een reeks met gegevens en gegevenslabels toevoegen.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Of koppel opmaakcode aan een broncel.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Andere typen grafieken maken

Met vergelijkbare technieken kun je verschillende soorten diagrammen maken, zoals kolom-, vlak-, bubbel-, spreidingsdiagrammen en meer. Hier is een voorbeeld van het invoegen van een eenvoudig kolomdiagram:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Verwijder standaard gegenereerde series.
chart.getSeries().clear();

// Categorieën maken en gegevens toevoegen.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## As-eigenschappen aanpassen

U kunt aseigenschappen aanpassen, zoals het astype wijzigen, maatstreepjes plaatsen, labels opmaken en meer. Hier is een voorbeeld van het definiëren van XY-aseigenschappen:

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
xAxis.setCrossesAt(3.0); // Gemeten in weergave-eenheden van de Y-as (honderden).
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

U kunt gegevenslabels opmaken met verschillende getalnotaties. Hier is een voorbeeld:

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

U kunt uw diagrammen verder personaliseren door grenzen, intervaleenheden tussen labels aan te passen, diagramassen te verbergen en meer. Bekijk de meegeleverde codefragmenten voor meer informatie over deze opties.

## Conclusie

In deze tutorial hebben we onderzocht hoe je met grafieken kunt werken met Aspose.Words voor Java. Je hebt geleerd hoe je verschillende soorten grafieken kunt maken, aseigenschappen kunt aanpassen, gegevenslabels kunt opmaken en meer. Aspose.Words voor Java biedt krachtige tools waarmee je visuele weergaven van gegevens aan je documenten kunt toevoegen, waardoor je informatie beter kunt presenteren.

## Veelgestelde vragen

### Hoe kan ik meerdere reeksen aan een grafiek toevoegen?

U kunt meerdere reeksen aan een grafiek toevoegen met behulp van de `chart.getSeries().add()` methode. Zorg ervoor dat u de reeksnaam, categorieën en gegevenswaarden opgeeft.

### Hoe kan ik gegevenslabels opmaken met aangepaste getalnotaties?

U kunt gegevenslabels opmaken door toegang te krijgen tot de `DataLabels` eigenschappen van een reeks en het instellen van de gewenste opmaakcode met behulp van `getNumberFormat().setFormatCode()`.

### Hoe pas ik aseigenschappen in een grafiek aan?

U kunt aseigenschappen zoals type, maatstreepjes, labels en meer aanpassen via de `ChartAxis` eigenschappen zoals `setCategoryType()`, `setCrosses()`, En `setMajorTickMark()`.

### Hoe kan ik andere typen diagrammen maken, zoals spreidings- of vlakdiagrammen?

kunt verschillende grafiektypen maken door de juiste `ChartType` bij het invoegen van de grafiek met behulp van `builder.insertChart(ChartType.TYPE, width, height)`.

### Hoe kan ik een grafiekas verbergen?

U kunt een grafiekas verbergen door de `setHidden(true)` eigenschap van de as.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}