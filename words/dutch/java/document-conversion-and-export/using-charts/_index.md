---
date: 2026-02-16
description: Leer hoe u meerdere series aan grafieken kunt toevoegen in Aspose.Words
  voor Java, as‑tickmarks kunt wijzigen, een aangepast getalformaat kunt toepassen
  en Word‑documenten met grafieken kunt genereren met lijn‑ en kolomgrafieken.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Meerdere series toevoegen aan grafieken in Aspose.Words voor Java
url: /nl/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Meerdere series toevoegen aan grafieken in Aspose.Words voor Java

## Introductie tot het gebruik van grafieken in Aspose.Words voor Java

In deze tutorial leer je **hoe je meerdere series** aan een grafiek kunt toevoegen met Aspose.Words voor Java, waarom het aanpassen van as‑ticmarkeringen en het toepassen van een aangepast getalformaat belangrijk is, en hoe je een Word‑document met veel grafieken genereert. Of je nu een lijngrafiek nodig hebt voor financiële gegevens of een kolomgrafiek voor verkoopcijfers, de onderstaande stappen begeleiden je bij het programmatic maken, stijlen en fijn afstellen van grafieken.

## Snelle antwoorden
- **Hoe voeg ik meerdere series toe?** Gebruik `chart.getSeries().add(...)` voor elke serie die je wilt weergeven.  
- **Kan ik as‑ticmarkeringen wijzigen?** Ja – gebruik `setMajorTickMark()` en `setMinorTickMark()` op de as‑objecten.  
- **Welk formaat kan ik toepassen op gegevenslabels?** Elk Excel‑compatibel getalformaat, bv. `"$"#,##0.00` of `0.00%`.  
- **Welke grafiektype‑s worden ondersteund?** Lijn, kolom, gebied, bubbel, spreiding en nog veel meer via `ChartType`.  
- **Is een licentie vereist voor productie?** Een geldige Aspose.Words voor Java‑licentie is nodig voor volledige functionaliteit.

## Wat betekent “meerdere series toevoegen” in een grafiek?
Meerdere series toevoegen betekent dat je meer dan één gegevensset in hetzelfde grafiekgebied plaatst, zodat je verschillende categorieën of tijdsperioden naast‑elkaar kunt vergelijken. Elke serie verschijnt als een eigen lijn, kolom of markeringsset, waardoor lezers een rijkere visuele weergave krijgen.

## Waarom Aspose.Words voor Java gebruiken om Word‑documenten met grafieken te genereren?
- **Volledige controle** over grafiektype, lay‑out en styling zonder Word handmatig te openen.  
- **Programmatic generatie** past in geautomatiseerde rapportage‑pipelines.  
- **Cross‑platform** – werkt in elke Java‑compatibele omgeving.  
- **Rijke API** voor het aanpassen van assen, gegevenslabels en getalformaten.

## Voorvereisten
- Java Development Kit (JDK) 8 of hoger.  
- Aspose.Words voor Java‑bibliotheek toegevoegd aan je project (Maven/Gradle of JAR).  
- Een geldige Aspose‑licentie voor productie (optioneel voor evaluatie).

## Stapsgewijze handleiding

### Stap 1: Maak een lijngrafiek en **voeg meerdere series toe**
Hieronder staat de kerncode die een lijngrafiek maakt, de standaardserie verwijdert en vervolgens drie verschillende series met aangepaste gegevenslabels toevoegt.

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

> **Pro tip:** Roep `chart.getSeries().add(...)` zo vaak aan als nodig is om **meerdere series toe te voegen** – elke aanroep creëert een nieuwe lijn (of kolom, enz.) in dezelfde grafiek.

### Stap 2: **Maak een kolomgrafiek** (create column chart java)
Het volgende fragment laat zien hoe je een eenvoudige kolomgrafiek invoegt, wat handig is voor het naast‑elkaar vergelijken van categorieën.

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

### Stap 3: **Wijzig as‑ticmarkeringen** (change axis tick marks)
Het aanpassen van de X‑ en Y‑as verbetert de leesbaarheid. De onderstaande code demonstreert hoe je ticmarkeringen wijzigt, de volgorde omkeert en aangepaste kruispunten instelt.

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

### Stap 4: **Pas een aangepast getalformaat toe** (apply custom number format)
Je kunt as‑getallen of gegevenslabels opmaken met elk patroon dat door Excel wordt ondersteund. Hieronder staat een beknopt voorbeeld dat de Y‑as formatteert met een duizendtallen‑scheidingsteken.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Stap 5: Genereer het uiteindelijke Word‑document (generate chart word document)
Na het configureren van series, assen en labels roep je simpelweg `doc.save(...)` aan zoals in de bovenstaande fragmenten. Het resulterende `.docx`‑bestand bevat volledig functionele grafieken die in Microsoft Word geopend en bewerkt kunnen worden.

## Veelvoorkomende use‑cases
- **Financiële dashboards** – lijngrafieken met meerdere series voor omzet, kosten en winst.  
- **Verkooprapporten** – kolomgrafieken die kwartaalverkoop per regio vergelijken.  
- **Projecttracking** – gebieds‑ of spreidingsgrafieken die voortgang in de tijd visualiseren.  

## Aanvullende grafiek‑aanpassingen
Naast de basis kun je grenzen aanpassen, assen verbergen (`axis.setHidden(true)`), kleuren wijzigen, legenda’s toevoegen en meer. Raadpleeg de Aspose.Words voor Java API‑referentie voor de volledige lijst met opties.

## Conclusie
In deze gids hebben we behandeld hoe je **meerdere series** aan grafieken kunt toevoegen, zowel lijn‑ als kolomgrafieken maakt, **as‑ticmarkeringen wijzigt**, **aangepaste getalformaten toepast**, en uiteindelijk **een Word‑document met veel grafieken genereert**. Met Aspose.Words voor Java heb je een krachtige, code‑first manier om professionele datavisualisaties direct in je documenten te embedden.

## Veelgestelde vragen

**Q: Hoe kan ik meerdere series aan een grafiek toevoegen?**  
A: Roep `chart.getSeries().add()` aan voor elke serie die je wilt weergeven. Elke aanroep creëert een nieuwe gegevensset die verschijnt als een eigen lijn, kolom of markeringsgroep.

**Q: Hoe formatteer ik gegevenslabels met een aangepast getalformaat?**  
A: Toegang tot het `DataLabels`‑object van de serie en gebruik `getNumberFormat().setFormatCode("jouw patroon")`. Je kunt het formaat ook koppelen aan een broncel met `isLinkedToSource(true)`.

**Q: Hoe kan ik as‑ticmarkeringen wijzigen?**  
A: Gebruik `setMajorTickMark()` en `setMinorTickMark()` op `ChartAxis`. Opties omvatten `CROSS`, `INSIDE`, `OUTSIDE` en `NONE`.

**Q: Kan ik andere grafiektype‑s maken, zoals spreidings‑ of gebiedsgrafieken?**  
A: Ja – specificeer het gewenste `ChartType` (bijv. `ChartType.SCATTER`, `ChartType.AREA`) bij het aanroepen van `builder.insertChart(...)`.

**Q: Hoe verberg ik een as die ik niet nodig heb?**  
A: Roep `axis.setHidden(true)` aan op de `ChartAxis` die je wilt verbergen.

---

**Laatst bijgewerkt:** 2026-02-16  
**Getest met:** Aspose.Words voor Java 24.11  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}