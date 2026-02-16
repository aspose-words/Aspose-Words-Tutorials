---
date: 2026-02-16
description: Lär dig hur du lägger till flera serier i diagram i Aspose.Words för
  Java, ändrar axelns tick‑märken, tillämpar anpassat talformat och genererar Word‑dokument
  med diagram med linje‑ och stapeldiagram.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Lägg till flera serier i diagram i Aspose.Words för Java
url: /sv/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till flera serier i diagram i Aspose.Words för Java

## Introduktion till att använda diagram i Aspose.Words för Java

## Snabba svar
- **Hur lägger jag till flera serier?** Använd `chart.getSeries().add(...)` för varje serie du vill visa.  
- **Kan jag ändra axelns streckmarkeringar?** Ja – använd `setMajorTickMark()` och `setMinorTickMark()` på axelobjekten.  
- **Vilket format kan jag använda för datamärkningarna?** Alla Excel‑kompatibla talformat, t.ex. `"$"#,##0.00` eller `0.00%`.  
- **Vilka diagramtyper stöds?** Linje, stapel, område, bubbla, spridning och många fler via `ChartType`.  
- **Krävs en licens för produktion?** En giltig Aspose.Words for Java-licens behövs för full funktionalitet.

## Vad betyder “add multiple series” i ett diagram?
Att lägga till flera serier innebär att infoga mer än en dataset i samma diagramområde, vilket gör att du kan jämföra olika kategorier eller tidsperioder sida‑vid‑sida. Varje serie visas som sin egen linje, stapel eller marköruppsättning, vilket ger läsarna en rikare visuell berättelse.

## Varför använda Aspose.Words for Java för att generera diagram‑Word‑dokument?
- **Full kontroll** över diagramtyp, layout och stil utan att öppna Word manuellt.  
- **Programmatisk generering** passar in i automatiserade rapporteringspipeline.  
- **Cross‑platform** – fungerar i alla Java‑kompatibla miljöer.  
- **Rik API** för anpassning av axlar, datamärkningar och talformat.

## Förutsättningar
- Java Development Kit (JDK) 8 eller högre.  
- Aspose.Words for Java‑biblioteket tillagt i ditt projekt (Maven/Gradle eller JAR).  
- En giltig Aspose‑licens för produktion (valfritt för utvärdering).

## Steg‑för‑steg guide

### Steg 1: Skapa ett linjediagram och **lägga till flera serier**
Nedan är kärnkoden som skapar ett linjediagram, rensar standardserien och sedan lägger till tre distinkta serier med anpassade datamärkningar.

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

> **Proffstips:** Anropa `chart.getSeries().add(...)` så många gånger som behövs för att **lägga till flera serier** – varje anrop skapar en ny linje (eller stapel, etc.) i samma diagram.

### Steg 2: **Skapa ett stapeldiagram** (create column chart java)
Nästa kodsnutt visar hur man infogar ett enkelt stapeldiagram, vilket är användbart för att jämföra kategorier sida‑vid‑sida.

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

### Steg 3: **Ändra axelns streckmarkeringar** (change axis tick marks)
Anpassning av X‑ och Y‑axeln förbättrar läsbarheten. Följande kod demonstrerar hur man ändrar streckmarkeringar, vänder ordning och sätter anpassade korsningspunkter.

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

### Steg 4: **Applicera ett anpassat talformat** (apply custom number format)
Du kan formatera axelns tal eller datamärkningar med vilket mönster som helst som stöds av Excel. Nedan är ett kort exempel som formaterar Y‑axeln med ett tusentalsavgränsarmönster.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Steg 5: Generera det slutgiltiga Word‑dokumentet (generate chart word document)
Efter att ha konfigurerat serier, axlar och etiketter, anropa helt enkelt `doc.save(...)` som visas i kodsnuttarna ovan. Den resulterande `.docx`‑filen innehåller fullt funktionella diagram som kan öppnas och redigeras i Microsoft Word.

## Vanliga användningsfall
- **Finansiella instrumentpaneler** – linjediagram med flera serier för intäkter, kostnader och vinst.  
- **Försäljningsrapporter** – stapeldiagram som jämför kvartalsförsäljning över regioner.  
- **Projektuppföljning** – område‑ eller spridningsdiagram som visualiserar framsteg över tid.  

## Ytterligare diagramanpassningar
Utöver grunderna kan du justera gränser, dölja axlar (`axis.setHidden(true)`), ändra färger, lägga till förklaringar och mer. Se Aspose.Words for Java API‑referensen för den fullständiga listan av alternativ.

## Slutsats
I den här guiden gick vi igenom hur man **lägger till flera serier** i diagram, skapar både linje‑ och stapeldiagram, **ändrar axelns streckmarkeringar**, **applikerar anpassade talformat**, och slutligen **genererar ett diagram‑rikt Word‑dokument**. Med Aspose.Words for Java har du ett kraftfullt, kod‑först sätt att bädda in professionella datavisualiseringar direkt i dina dokument.

## Vanliga frågor

**Q: Hur kan jag lägga till flera serier i ett diagram?**  
A: Anropa `chart.getSeries().add()` för varje serie du vill visa. Varje anrop skapar en ny datamängd som visas som sin egen linje, stapel eller markörgrupp.

**Q: Hur formaterar jag datamärkningar med ett anpassat talformat?**  
A: Få åtkomst till seriens `DataLabels`‑objekt och använd `getNumberFormat().setFormatCode("your pattern")`. Du kan också länka formatet till en källcell med `isLinkedToSource(true)`.

**Q: Hur kan jag ändra axelns streckmarkeringar?**  
A: Använd `setMajorTickMark()` och `setMinorTickMark()` på `ChartAxis`. Alternativen inkluderar `CROSS`, `INSIDE`, `OUTSIDE` och `NONE`.

**Q: Kan jag skapa andra diagramtyper som spridnings‑ eller områdesdiagram?**  
A: Ja – specificera önskad `ChartType` (t.ex. `ChartType.SCATTER`, `ChartType.AREA`) när du anropar `builder.insertChart(...)`.

**Q: Hur döljer jag en axel jag inte behöver?**  
A: Anropa `axis.setHidden(true)` på den `ChartAxis` du vill dölja.

---

**Senast uppdaterad:** 2026-02-16  
**Testad med:** Aspose.Words for Java 24.11  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}