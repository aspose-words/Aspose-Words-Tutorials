---
date: 2025-12-13
description: Leer hoe u een kolomgrafiek maakt en de gegevenslabels van de grafiek
  opmaakt met Aspose.Words voor Java. Ontdek hoe u meerdere series toevoegt, het asstype
  wijzigt en de grafiekas verbergt.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Hoe een kolomgrafiek maken met Aspose.Words voor Java
url: /nl/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een kolomdiagram maken met Aspose.Words voor Java

In deze tutorial **create column chart** visualisaties direct in Word / DOCX‑bestanden met Aspose.Words voor Java. We lopen door het maken van verschillende diagramtypen, het toevoegen van meerdere series, het opmaken van diagramdataclabels, het wijzigen van het as‑type, en zelfs het verbergen van een diagramas wanneer je een schonere weergave nodig hebt. Aan het einde heb je een solide, productie‑klare aanpak voor het insluiten van rijke diagrammen in je documenten.

## Snelle antwoorden
- **Wat is de primaire klasse om een diagram te bouwen?** `DocumentBuilder` with `insertChart`.
- **Welke methode voegt een nieuwe serie toe?** `chart.getSeries().add(...)`.
- **Hoe format ik diagramdataclabels?** Use `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Kan ik een as verbergen?** Yes, call `setHidden(true)` on the axis object.
- **Heb ik een licentie nodig voor Aspose.Words?** Een licentie is vereist voor productiegebruik; een gratis proefversie is beschikbaar.

## Wat is een kolomdiagram en waarom gebruiken?

Een kolomdiagram toont categorische gegevens als verticale balken, waardoor het ideaal is om waarden over groepen te vergelijken (verkoop per regio, maandelijkse uitgaven, enz.). In Java‑applicaties maakt het genereren van een kolomdiagram met Aspose.Words het mogelijk om deze visualisaties direct in Word / DOCX‑bestanden in te sluiten zonder Excel of externe tools te hoeven gebruiken.

## Hoe een kolomdiagram maken

Hieronder staat een eenvoudig voorbeeld dat een simpel kolomdiagram maakt. De code is identiek aan het oorspronkelijke fragment – we hebben alleen verklarende opmerkingen toegevoegd om het makkelijker te volgen.

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

### Meerdere series toevoegen

Je kunt **add multiple series** aan een kolomdiagram toevoegen door herhaaldelijk `chart.getSeries().add(...)` aan te roepen, zoals hierboven getoond. Elke serie kan zijn eigen set categorieën en waarden hebben, waardoor je verschillende datasets naast elkaar kunt vergelijken.

## Hoe een lijndiagram maken met aangepaste datalabels

Als je een lijndiagram nodig hebt in plaats van een kolomdiagram, geldt hetzelfde patroon. Dit voorbeeld toont ook **format chart data labels** met verschillende getalformaten.

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

### Dataplabels toevoegen

De aanroep `series1.hasDataLabels(true)` **adds data labels** aan de serie, terwijl `setShowValue(true)` de daadwerkelijke waarden zichtbaar maakt op het diagram.

## Hoe het as‑type wijzigen en as‑eigenschappen aanpassen

Het wijzigen van het as‑type (bijv. van datum naar categorie) stelt je in staat te bepalen hoe datapunten worden weergegeven. Deze code laat ook zien hoe je **hide chart axis** kunt verbergen als je een minimalistisch ontwerp verkiest.

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

### As‑type wijzigen

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **changes axis type** van een datumgebaseerde as naar een categorische, waardoor je volledige controle krijgt over de plaatsing van labels.

## Hoe diagramdataclabels opmaken (getalformaten)

Je kunt getalopmaak direct toepassen op de as of datalabels. Dit voorbeeld formatteert de Y‑as‑getallen met een duizendtalseparator.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Extra diagramaanpassingen

Naast de basis kun je grenzen aanpassen, intervaleenheden tussen labels instellen, specifieke assen verbergen, en meer. Raadpleeg de Aspose.Words for Java API‑documentatie voor een volledige lijst van eigenschappen.

## Veelgestelde vragen

**Q: Hoe kan ik meerdere series aan een diagram toevoegen?**  
A: Gebruik `chart.getSeries().add()` voor elke serie die je wilt weergeven. Elke aanroep kan een unieke naam, categorie‑array en waardearray leveren.

**Q: Hoe format ik diagramdataclabels met aangepaste getalformaten?**  
A: Toegang tot het `DataLabels`‑object van een serie en roep `getNumberFormat().setFormatCode("your format")` aan. Je kunt het formaat ook koppelen aan een broncel met `isLinkedToSource(true)`.

**Q: Hoe kan ik een diagramas verbergen?**  
A: Roep `setHidden(true)` aan op de `ChartAxis` die je wilt verbergen (bijv. `chart.getAxisY().setHidden(true)`).

**Q: Wat is de beste manier om het as‑type te wijzigen?**  
A: Gebruik `setCategoryType(AxisCategoryType.CATEGORY)` voor categorische assen of `AxisCategoryType.DATE` voor datumassen.

**Q: Hoe voeg ik datalabels toe aan een serie?**  
A: Schakel ze in met `series.hasDataLabels(true)` en configureer vervolgens de zichtbaarheid met `series.getDataLabels().setShowValue(true)`.

## Conclusie

We hebben alles behandeld wat je nodig hebt om **create column chart** visualisaties te maken met Aspose.Words voor Java — van het invoegen van basisdiagrammen en het toevoegen van meerdere series, tot het opmaken van diagramdataclabels, het wijzigen van het as‑type, en het verbergen van diagramassen voor een nette uitstraling. Integreer deze technieken in je rapportage‑ of documentgeneratie‑pijplijnen om professionele, data‑gedreven Word‑documenten te leveren.

---

**Last Updated:** 2025-12-13  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}