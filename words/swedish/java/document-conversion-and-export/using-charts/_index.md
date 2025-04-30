---
"description": "Lär dig hur du skapar och anpassar diagram i Aspose.Words för Java. Utforska diagramtyper, formatering och axelegenskaper för datavisualisering."
"linktitle": "Använda diagram"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda diagram i Aspose.Words för Java"
"url": "/sv/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda diagram i Aspose.Words för Java


## Introduktion till att använda diagram i Aspose.Words för Java

I den här handledningen utforskar vi hur man arbetar med diagram med Aspose.Words för Java. Du lär dig hur du skapar olika typer av diagram, anpassar axelegenskaper, formaterar dataetiketter och mer. Nu kör vi!

## Skapa ett linjediagram

För att skapa ett linjediagram, använd följande kod:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Ta bort standardgenererade serier.
chart.getSeries().clear();

// Lägga till en serie med data och dataetiketter.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Eller länka formatkod till en källcell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Skapa andra typer av diagram

Du kan skapa olika typer av diagram som kolumndiagram, ytdiagram, bubbeldiagram, punktdiagram och mer med liknande tekniker. Här är ett exempel på hur du infogar ett enkelt kolumndiagram:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Ta bort standardgenererade serier.
chart.getSeries().clear();

// Skapa kategorier och lägga till data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Anpassa axelegenskaper

Du kan anpassa axelegenskaper, till exempel ändra axeltyp, ange skalmarkeringar, formatera etiketter med mera. Här är ett exempel på hur du definierar XY-axelegenskaper:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Rensa standardserien och lägg till dina data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Ändra X-axeln till en kategori istället för ett datum.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Mätt i visningsenheter för Y-axeln (hundratal).
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

## Formatera dataetiketter

Du kan formatera dataetiketter med olika talformat. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Rensa standardserien och lägg till dina data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Ytterligare diagramanpassningar

Du kan ytterligare anpassa dina diagram genom att justera gränser, intervallenheter mellan etiketter, dölja diagramaxlar och mer. Utforska de medföljande kodavsnitten för att lära dig mer om dessa alternativ.

## Slutsats

den här handledningen har vi utforskat hur man arbetar med diagram med Aspose.Words för Java. Du har lärt dig hur du skapar olika typer av diagram, anpassar axelegenskaper, formaterar dataetiketter och mer. Aspose.Words för Java tillhandahåller kraftfulla verktyg för att lägga till visuella representationer av data i dina dokument, vilket förbättrar hur du presenterar information.

## Vanliga frågor

### Hur kan jag lägga till flera serier i ett diagram?

Du kan lägga till flera serier i ett diagram med hjälp av `chart.getSeries().add()` metod. Se till att ange serienamn, kategorier och datavärden.

### Hur kan jag formatera dataetiketter med anpassade nummerformat?

Du kan formatera dataetiketter genom att öppna `DataLabels` egenskaper för en serie och inställning av önskad formatkod med hjälp av `getNumberFormat().setFormatCode()`.

### Hur anpassar jag axelegenskaper i ett diagram?

Du kan anpassa axelegenskaper som typ, skalmarkeringar, etiketter med mera genom att öppna `ChartAxis` egenskaper som `setCategoryType()`, `setCrosses()`och `setMajorTickMark()`.

### Hur kan jag skapa andra typer av diagram, som punktdiagram eller ytdiagram?

Du kan skapa olika diagramtyper genom att ange lämpliga `ChartType` när du infogar diagrammet med hjälp av `builder.insertChart(ChartType.TYPE, width, height)`.

### Hur kan jag dölja en diagramaxel?

Du kan dölja en diagramaxel genom att ställa in `setHidden(true)` axelns egenskap.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}