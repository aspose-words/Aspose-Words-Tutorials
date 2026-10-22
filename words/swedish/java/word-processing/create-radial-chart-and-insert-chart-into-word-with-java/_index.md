---
category: general
date: 2026-09-27
description: Skapa ett radialdiagram i Java och infoga diagrammet i Word. Lär dig
  hur du ställer in diagrammets storlek, lägger till dataserier och genererar ett
  tomt Word‑dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: sv
lastmod: 2026-09-27
og_description: Skapa ett radialdiagram i Java, och sedan infoga diagrammet i Word.
  Den här guiden visar hur du ställer in diagrammets storlek, lägger till dataserier
  och skapar ett tomt Word‑dokument.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Skapa ett radiellt diagram och infoga diagrammet i Word med Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Skapa ett radialdiagram och infoga diagrammet i Word med Java
url: /sv/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa radial diagram och infoga diagram i Word med Java

Om du behöver **skapa radial diagram** i en Word‑fil med Java visar den här handledningen exakt hur du gör. Du kommer att se hur du **infogar diagram i Word**, ställer in diagrammets dimensioner och bygger ett **tomt Word‑dokument** från grunden.

Vi går igenom varje nödvändigt steg, från att initiera dokumentet till att lägga till en dataserie och spara den slutliga `.docx`. I slutet har du en fullt fungerande Word‑fil som innehåller ett radial diagram, och du förstår **hur man ställer in diagramstorlek** och **lägger till dataserie‑diagram** för framtida anpassningar.

## Förutsättningar

* Java 17 eller senare (koden kompileras med vilken modern JDK som helst)
* Aspose.Words for Java 24.9 eller nyare – metoden `setShowGraduations` finns endast från denna version
* En IDE eller byggverktyg (Maven/Gradle) som kan inkludera Aspose.Words‑JAR‑filen
* Grundläggande kunskap om Java‑syntax och Maven/Gradle‑beroendehantering

> **Proffstips:** Om du använder Maven, lägg till följande i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Steg 1: Skapa ett tomt Word‑dokument

Ett tomt dokument är duken där diagrammet kommer att placeras. Klassen `Document` representerar hela `.docx`‑filen.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Att skapa ett tomt dokument säkerställer att inget befintligt innehåll stör diagrammets layout.

## Steg 2: Initiera en DocumentBuilder

`DocumentBuilder` erbjuder bekväma metoder för att infoga objekt, text och andra element i dokumentet.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Buildern kommer senare att användas för att **infoga diagram i Word**.

## Steg 3: Bygg det radial diagrammet

Aspose.Words stödjer många diagramtyper; `ChartType.RADIAL` skapar ett radial (polärt) diagram.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Vid detta steg finns diagrammet men det har ingen data, storlek eller visuella alternativ.

## Steg 4: Lägg till en dataserie i diagrammet

Ett diagram utan dataserie är tomt. Metoden `add` tar ett serienamn och en array med värden.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Du kan lägga till flera serier genom att anropa `add` upprepade gånger. Detta uppfyller kravet **lägga till dataserie‑diagram**.

## Steg 5: Aktivera gradueringar (valfritt)

Gradueringar är de radiala rutnätslinjerna som förbättrar läsbarheten. De är endast tillgängliga från version 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Om du använder en äldre Aspose.Words‑version kommer den här raden att kasta ett undantag – kontrollera därför ditt biblioteks version först.

## Steg 6: Ställ in diagrammets dimensioner

Genom att kontrollera diagramstorleken kan du passa in det snyggt inom sidmarginalerna. Detta svarar på **hur man ställer in diagramstorlek**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Du kan justera bredd‑ och höjdpunkterna för att matcha dina layoutbehov. Kom ihåg att 1 punkt ≈ 1/72 tum.

## Steg 7: Infoga diagrammet i Word‑dokumentet

Nu är diagrammet redo att placeras. Metoden `insertChart` i `DocumentBuilder` hanterar infogningen.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Detta är kärnan i **infoga diagram i word**‑operationen.

## Steg 8: Spara dokumentet

Till sist skriver du dokumentet till disk. Filen kommer att innehålla det radial diagram du just skapat.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

När programmet körs får du `RadialChart.docx` i projektets arbetskatalog. När du öppnar filen i Microsoft Word visas ett radial diagram med tre datapunkter och synliga gradueringar.

### Förväntat resultat

* En Word‑fil med namnet `RadialChart.docx`
* I filen, en enda sida som innehåller ett radial diagram i storleken 400 × 300 punkter
* Diagrammet visar en serie med titeln **Series 1** och värdena **10, 20, 30**
* Gradueringar (radiala rutnätslinjer) är synliga runt diagrammet

## Vanliga variationer och kantfall

| Situation | Vad som ska ändras | Orsak |
|-----------|--------------------|-------|
| **Flera serier** | Anropa `chart.getSeries().add(...)` för varje serie | Möjliggör jämförande datavisualisering |
| **Olika diagramtyp** | Byt ut `ChartType.RADIAL` mot `ChartType.COLUMN` (eller någon annan) | Använd den diagramtyp som bäst representerar dina data |
| **Anpassade färger** | Access `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Förbättrar visuell profilering |
| **Äldre Aspose.Words‑version** | Utelämna raden `setShowGraduations` eller uppgradera biblioteket | Förhindrar `NoSuchMethodError` |
| **Spara till ett annat format** | Använd `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Skapar en PDF istället för en DOCX |

## Fullt körbart exempel

Nedan är det kompletta, självständiga Java‑programmet. Kopiera det till en fil med namnet `RadialChartExample.java`, lägg till Aspose.Words‑beroendet och kör det.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Slutsats

Du vet nu hur du **skapar radial diagram** programatiskt, **lägger till dataserie‑diagram**, styr **hur man ställer in diagramstorlek** och **infogar diagram i Word** samtidigt som du börjar från ett **tomt Word‑dokument**. Exemplet använder Aspose.Words for Java 24.9, men samma koncept gäller för andra diagrambibliotek som exponerar ett liknande API.

### Nästa steg

* Utforska andra diagramtyper (`ChartType.PIE`, `ChartType.LINE` osv.) – detta knyter tillbaka till det sekundära nyckelordet **infoga diagram i word**.
* Anpassa axelrubriker, förklaringar och färger så att de matchar dina varumärkesriktlinjer.
* Generera diagram dynamiskt från databassökningar eller CSV‑filer.
* Konvertera den resulterande `.docx` till PDF för distribution (`doc.save("output.pdf", SaveFormat.PDF)`).

Känn dig fri att experimentera med dimensioner, seriedata och stilalternativ för att skapa exakt den visualisering du behöver. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}