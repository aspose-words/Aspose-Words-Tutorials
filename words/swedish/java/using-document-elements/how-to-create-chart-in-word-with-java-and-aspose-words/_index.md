---
category: general
date: 2026-09-24
description: Lär dig hur du skapar ett diagram i Word med Java, infogar ett radialdiagram
  och sparar dokumentet som docx med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: sv
lastmod: 2026-09-24
og_description: Skapa diagram i Word med Java och Aspose.Words. Denna handledning
  visar hur du lägger till ett radardiagram, anpassar data och sparar dokumentet som
  docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Skapa diagram i Word med Java – steg‑för‑steg guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Hur man skapar diagram i Word med Java och Aspose.Words
url: /sv/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du diagramm i Word med Java och Aspose.Words

Om du behöver **create chart in Word** från en Java‑applikation, guidar den här handledningen dig genom hela processen. Du kommer att se hur du lägger till ett radiellt diagram, eventuellt fyller i dess serier, och slutligen **save document as docx** med Aspose.Words for Java‑biblioteket.

Att generera visuella data i en Word‑fil är ett vanligt krav för rapportering, fakturering eller automatiserad dokumentgenerering. I slutet av den här handledningen kommer du att kunna skapa **create word document java**‑projekt som **add chart to Word**‑filer utan någon manuell redigering.

## Förutsättningar

* Java Development Kit (JDK) 8 eller nyare.
* Maven eller Gradle för beroendehantering.
* En IDE som IntelliJ IDEA, Eclipse eller VS Code.
* En giltig Aspose.Words for Java‑licens (gratis provversion fungerar för utveckling).

Dessa verktyg utgör grunden för kodexemplen som följer.

## Steg 1: Ställ in Maven‑projektet

Skapa ett nytt Maven‑projekt (eller uppdatera ett befintligt) och lägg till Aspose.Words‑beroendet i din `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Att köra `mvn clean install` laddar ner biblioteket och gör klasser som `Document`, `DocumentBuilder` och `ChartType` tillgängliga på classpath.

> **Pro tip:** Håll biblioteksversionen uppdaterad. Nya versioner lägger till diagramtyper och förbättrar renderingsprestanda.

## Steg 2: Skapa ett nytt Word‑dokument

Det första programatiska steget för att **create chart in Word** är att instansiera ett tomt `Document`. Detta objekt representerar hela `.docx`‑paketet.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fungerar som en markör; den känner till den aktuella infogningspunkten och erbjuder metoder för text, tabeller och diagram. Vid detta tillfälle har du **created word document java**‑stil – en ren canvas redo för innehåll.

## Steg 3: Infoga ett radiellt diagram

Aspose.Words stöder många diagramtyper. För att **insert radial chart**, anropa `insertChart` med `ChartType.RADIAL`. Metoden kräver också bredd och höjd i punkter (1 punkt ≈ 1/72 tum).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Det returnerade `Shape`‑objektet innehåller det underliggande diagramobjektet. Diagrammet renderar automatiskt graderingar för en 24,9°‑layout, vilket är standard för radiella diagram i Word.

### Varför använda ett radiellt diagram?

Ett radiellt diagram visualiserar data som omsluter en cirkel, vilket gör det idealiskt för att visa cykliska mönster (t.ex. månatlig försäljning, klockans mätvärden). Samma API kan infoga stapel-, paj- eller linjediagram, men den radiella typen ger ett distinkt utseende utan extra stilkod.

## Steg 4: (Valfritt) Fyll diagrammets seriedata

Om du vill att diagrammet ska visa verkliga värden måste du lägga till serier och punkter. Följande kodsnutt lägger till en enda serie med tre datapunkter:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Du kan upprepa `add`‑anropen för så många punkter som behövs. Aspose.Words uppdaterar automatiskt den visuella representationen, så du ser de radiella segmenten anpassas till de nya värdena.

> **Common question:** *Vad händer om jag behöver binda data från en databas?*  
> Hämta raderna, loopa igenom dem och anropa `series.getDataPoints().add(value, label)` inom loopen. API:et är trådsäkert och fungerar med vilken `ResultSet` du än tillhandahåller.

## Steg 5: Spara dokumentet som DOCX

När diagrammet är klart är sista steget att **save document as docx**. `save`‑metoden bestämmer utdataformatet från filändelsen.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Den genererade filen innehåller ett fullt funktionellt radiellt diagram som kan öppnas i Microsoft Word, LibreOffice eller någon visare som stödjer DOCX‑formatet. Eftersom vi använde `.docx`‑ändelsen sparar Word filen i Open XML‑formatet, vilket är den moderna standarden för Word‑dokument.

### Verifiera resultatet

Öppna `RadialChartDemo.docx` i Word:

1. Du bör se en enda sida med ett centrerat radiellt diagram.
2. Om du har lagt till seriedata visar diagrammet fyra segment märkta Q1‑Q4.
3. Högerklicka på diagrammet → **Edit Data** för att bekräfta den underliggande datatabellen.

Om diagrammet visas tomt, dubbelkolla att du anropade `chart.getChart()` innan du lade till serier, och säkerställ att DocumentBuilder‑markören är placerad där du vill ha diagrammet.

## Steg 6: Avancerade tips för att arbeta med diagram

| Tip | Why it matters |
|-----|----------------|
| **Ställ in diagramstil** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Förbättrar visuell konsistens utan att manuellt formatera varje element. |
| **Ändra storlek efter infogning** – `chart.setWidth(500); chart.setHeight(350);` | Gör det möjligt att finjustera diagrammets storlek baserat på sidlayout. |
| **Lägg till en titel** – `chart.getChart().getTitle().setText("Revenue Overview");` | Ger kontext till läsare som ser dokumentet utan omgivande text. |
| **Exportera till PDF** – `doc.save("RadialChartDemo.pdf");` | Användbart när du behöver en icke‑redigerbar version för distribution. |
| **Licenshantering** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Förhindrar utvärderingsvattenstämpeln i produktionsbyggnader. |

Dessa förbättringar är valfria men visar hur du kan ytterligare anpassa diagrammet efter att du har lärt dig att **add chart to Word**.

## Slutsats

Du har nu ett komplett, självständigt exempel som visar hur du **create chart in Word** med Java, **insert radial chart**, valfritt fyller det med data, och **save document as docx**. Samma mönster fungerar för andra diagramtyper, så du kan utöka den här handledningen till stapel-, linje- eller pajdiagram vid behov.

Nästa steg kan du utforska:

* **create word document java**‑projekt som kombinerar tabeller, bilder och flera diagram.
* Använda **save document as docx** tillsammans med **save document as pdf** för flermålsrapportering.
* Lägga till dynamisk data från REST‑API:er eller databaser till dina diagram.

Känn dig fri att experimentera med stilalternativen, diagramdimensionerna och datakällorna. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Skapa tomt Word‑dokument med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Skapa Word‑dokument Java – Lägg till rektangel‑form med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}