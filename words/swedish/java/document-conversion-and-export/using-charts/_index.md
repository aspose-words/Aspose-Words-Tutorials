---
date: 2025-12-13
description: Lär dig hur du skapar stapeldiagram och formaterar diagrammets datamärkningar
  med Aspose.Words för Java. Utforska hur du lägger till flera serier, ändrar axeltyp
  och döljer diagramaxeln.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Hur man skapar stapeldiagram med Aspose.Words för Java
url: /sv/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du stapeldiagram med Aspose.Words för Java

I den här handledningen kommer du **skapa stapeldiagram**‑visualiseringar direkt i Word‑dokument med Aspose.Words för Java. Vi går igenom hur du skapar olika diagramtyper, lägger till flera serier, formaterar diagrammets datalabels, ändrar axeltyp och även döljer en diagramaxel när du vill ha ett renare utseende. I slutet har du en solid, produktionsklar metod för att bädda in rika diagram i dina dokument.

## Snabba svar
- **Vad är den primära klassen för att bygga ett diagram?** `DocumentBuilder` med `insertChart`.
- **Vilken metod lägger till en ny serie?** `chart.getSeries().add(...)`.
- **Hur formaterar jag diagrammets datalabels?** Använd `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Kan jag dölja en axel?** Ja, anropa `setHidden(true)` på axelobjektet.
- **Behöver jag en licens för Aspose.Words?** En licens krävs för produktionsanvändning; en gratis provversion finns tillgänglig.

## Vad är ett stapeldiagram och varför använda det?

Ett stapeldiagram visar kategorisk data som vertikala staplar, vilket gör det idealiskt för att jämföra värden mellan grupper (försäljning per region, månatliga utgifter osv.). I Java‑applikationer gör generering av ett stapeldiagram med Aspose.Words det möjligt att bädda in dessa visualiseringar direkt i Word / DOCX‑filer utan att behöva Excel eller externa verktyg.

## Så skapar du ett stapeldiagram

Nedan följer ett enkelt exempel som skapar ett enkelt stapeldiagram. Koden är identisk med originalsnutten – vi har bara lagt till förklarande kommentarer för att göra den lättare att följa.

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

### Lägg till flera serier

Du kan **lägga till flera serier** i ett stapeldiagram genom att anropa `chart.getSeries().add(...)` upprepade gånger, som visas ovan. Varje serie kan ha sin egen uppsättning kategorier och värden, vilket gör att du kan jämföra flera dataset sida‑vid‑sida.

## Så skapar du ett linjediagram med anpassade datalabels

Om du behöver ett linjediagram istället för ett stapeldiagram gäller samma mönster. Detta exempel visar också hur du **formaterar diagrammets datalabels** med olika talformat.

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

### Lägg till datalabels

Anropet `series1.hasDataLabels(true)` **lägger till datalabels** till serien, medan `setShowValue(true)` gör de faktiska värdena synliga i diagrammet.

## Så ändrar du axeltyp och anpassar axelns egenskaper

Att ändra axeltypen (t.ex. från datum till kategori) låter dig styra hur datapunkter plottas. Denna kodsnutt visar också hur du **döljer diagramaxeln** om du föredrar en minimalistisk design.

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

### Ändra axeltyp

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **ändrar axeltypen** från en datumbaserad axel till en kategorisk, vilket ger dig full kontroll över placeringen av etiketter.

## Så formaterar du diagrammets datalabels (talformat)

Du kan applicera talformat direkt på axeln eller datalabels. Detta exempel formaterar Y‑axelns siffror med ett tusentalsavgränsare.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Ytterligare diagramanpassningar

Utöver grunderna kan du justera gränser, sätta intervallenheter mellan etiketter, dölja specifika axlar och mer. Se Aspose.Words för Java API‑dokumentationen för en fullständig lista över egenskaper.

## Vanliga frågor

**Q: Hur kan jag lägga till flera serier i ett diagram?**  
A: Använd `chart.getSeries().add()` för varje serie du vill visa. Varje anrop kan ange ett unikt namn, en kategori‑array och en värde‑array.

**Q: Hur formaterar jag diagrammets datalabels med anpassade talformat?**  
A: Få åtkomst till en series `DataLabels`‑objekt och anropa `getNumberFormat().setFormatCode("your format")`. Du kan också länka formatet till en källcell med `isLinkedToSource(true)`.

**Q: Hur kan jag dölja en diagramaxel?**  
A: Anropa `setHidden(true)` på den `ChartAxis` du vill dölja (t.ex. `chart.getAxisY().setHidden(true)`).

**Q: Vad är det bästa sättet att ändra axeltyp?**  
A: Använd `setCategoryType(AxisCategoryType.CATEGORY)` för kategoriska axlar eller `AxisCategoryType.DATE` för datumaxlar.

**Q: Hur lägger jag till datalabels i en serie?**  
A: Aktivera dem med `series.hasDataLabels(true)` och konfigurera sedan synligheten med `series.getDataLabels().setShowValue(true)`.

## Slutsats

Vi har gått igenom allt du behöver för att **skapa stapeldiagram**‑visualiseringar med Aspose.Words för Java – från att infoga grundläggande diagram och lägga till flera serier, till att formatera diagrammets datalabels, ändra axeltyp och dölja diagramaxlar för ett rent utseende. Integrera dessa tekniker i dina rapporterings‑ eller dokumentgenereringsprocesser för att leverera professionella, datadrivna Word‑dokument.

---

**Senast uppdaterad:** 2025-12-13  
**Testad med:** Aspose.Words for Java 24.12 (senaste)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}