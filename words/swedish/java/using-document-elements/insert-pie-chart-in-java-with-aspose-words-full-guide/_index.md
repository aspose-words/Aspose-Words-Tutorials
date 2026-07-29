---
category: general
date: 2026-07-29
description: Infoga ett cirkeldiagram med Aspose.Words för Java och lär dig hur du
  skapar ett donutdiagram, formaterar cirkeldiagram, formaterar diagram i Word och
  anpassar diagrammets storlek.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: sv
lastmod: 2026-07-29
og_description: Infoga cirkeldiagram med Aspose.Words för Java och lär dig snabbt
  att skapa ringdiagram, formatera cirkeldiagram, formatera diagram i Word och anpassa
  diagramstorlek för professionella dokument.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Infoga cirkeldiagram i Java – Komplett Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Infoga cirkeldiagram i Java med Aspose.Words – Fullständig guide
url: /sv/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga pajdiagram i Java med Aspose.Words – Komplett guide

Har du någonsin undrat hur man **insert pie chart** i ett Word‑dokument från Java‑kod? Du är inte ensam—många utvecklare stöter på detta hinder när de behöver ett snabbt, programatiskt sätt att visualisera data. Den goda nyheten? Med Aspose.Words for Java kan du göra det på bara några rader, och samtidigt **generate doughnut chart**, **format pie chart**, **format chart Word** och **customize chart size** så att det matchar ditt varumärke.

I den här handledningen går vi igenom ett verkligt exempel som börjar med att skapa ett tomt dokument, lägger in ett pajdiagram, justerar några visuella egenskaper och slutligen sparar filen. När du är klar har du ett återanvändbart kodsnutt som du kan klistra in i vilket Java‑projekt som helst som behöver diagram‑automation. Inga extra bibliotek, ingen manuell hantering av Office‑interop—bara ren, kompilerad Java.

## Vad du behöver

- **Java 17** (eller någon nyare JDK; API‑et är bakåtkompatibelt)
- **Aspose.Words for Java** 22.12 eller nyare – du kan hämta Maven‑artefakten eller .jar‑filen från Aspose‑sidan.
- En enkel IDE (IntelliJ IDEA, Eclipse, VS Code…) – vad som helst som låter dig köra en `main`‑metod.
- Valfritt: en licensfil om du inte vill ha utvärderingsvattenstämpeln.

Om du har allt detta kan vi hoppa rakt in i koden.

## Steg 1: Infoga pajdiagram med Aspose.Words

Det första vi gör är att **insert pie chart** i ett nytt dokument. Detta steg lägger grunden för allt annat, eftersom diagramobjektet ger oss åtkomst till serier, datapunkter och visuella justeringar.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Varför detta är viktigt:** `DocumentBuilder.insertChart` skapar inte bara diagrammet utan returnerar också ett `Chart`‑objekt som vi kan manipulera. Argumenten för bredd och höjd låter dig **customize chart size** redan vid skapandet, så du behöver inte ändra storlek senare.

## Steg 2: Generera donut‑diagram (valfritt)

Om din design kräver ett hål i mitten—tänk på ett klassiskt donut‑diagram—gör Aspose det med en enda rad kod. Samma `Chart`‑instans kan bytas från ett vanligt pajdiagram till ett donut‑diagram genom att justera hålstorleken.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tips:** Hålstorleken har bara effekt för `ChartType.DONUT`. Om du behåller typen som `PIE` ignoreras anropet, så experimentera gärna.

## Steg 3: Formatera pajdiagram‑segment

En bra visualisering framhäver ofta ett specifikt segment. Här **format pie chart** genom att "exploda" det första segmentet 20 punkter utåt. Detta drar läsarens blick till den viktigaste datapunkten.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro‑tips:** Du kan loopa igenom `pieChart.getSeries()` om du har flera serier och sätta individuella färger, kanter eller datalabels. Det är så du **format chart Word**‑dokument med rik styling.

## Steg 4: Lägg till data i diagrammet

Ett diagram utan data är bara en dekorativ form. Låt oss mata in en enkel dataset—t.ex. kvartalsvisa försäljningssiffror.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Varför vi gör detta:** Genom att explicit lägga till `ChartPoint`‑objekt säkerställer vi att diagrammet speglar vår affärslogik. Anropen `setShowCategoryName` och `setShowValue` är en del av **formatting the pie chart** för att visa både etiketter och siffror.

## Steg 5: Finjustera utseendet (customize chart size & style)

Utöver de initiala dimensionerna kanske du vill justera diagrammets förklaring, titel eller till och med teckensnittet för datalabels. Allt detta faller under **customize chart size** och övergripande formatering.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** Om du senare bestämmer dig för att exportera dokumentet till PDF, behåller diagrammets vektordata skärpan eftersom storleken definieras i punkter, inte pixlar. Det är en fördel för **format chart Word** och efterföljande format.

## Steg 6: Spara och visa dokumentet

Det sista steget är så enkelt som att anropa `doc.save`. Detta skriver en `.docx`‑fil som du kan öppna i Microsoft Word, LibreOffice eller någon annan visare som stödjer OpenXML‑formatet.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Resultat:** Öppna `PieChart.docx` så ser du ett snyggt dimensionerat paj‑ (eller donut‑)diagram med ett exploderat segment, en titel och en förklaring—allt genererat utan att någonsin röra UI:t.

### Förväntad output

| Element | Vad du kommer att se |
|---------|----------------------|
| Diagramtyp | Pajdiagram (eller donut om `holeSize` > 0) |
| Skivaexplosion | Första skivan förskjuten med 20 pts |
| Förklaring | Placeras till höger |
| Titel | “Quarterly Sales Distribution” i fetstil 14 pt |
| Dataetiketter | Kategorinamn och värde visas på varje skiva |
| Dokument | En standard Word `.docx`‑fil klar för delning |

## Vanliga frågor & fallgropar

- **Behöver jag en licens?**  
  Utvärderingsversionen fungerar bra för testning, men den lägger till en vattenstämpel. Lägg din `aspose.words.lic`‑fil i classpath för ett rent resultat.

- **Kan jag använda detta med Maven?**  
  Absolut. Lägg till följande beroende i din `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Vad händer om jag har mer än en serie?**  
  Loop över `pieChart.getSeries()` och applicera `setExplosion`, `setFillColor` eller annan formatering per serie. Så **format pie chart** för multidimensionell data.

- **Kan diagrammet redigeras i Word efter generering?**  
  Ja—när det är sparat kan du öppna dokumentet och manuellt justera färger, teckensnitt eller till och med konvertera pajen till ett stapeldiagram om du så önskar.

## Sammanfattning

Vi har just **inserted pie chart** i ett Word‑dokument med Aspose.Words for Java, visat hur man **generate doughnut chart**, demonstrerat flera sätt att **format pie chart**, gått igenom bästa praxis för **format chart Word** och lärt oss hur man **customize chart size** för ett polerat resultat. Det kompletta, körbara exemplet ovan kan slängas in i vilket Java‑projekt som helst och ger dig omedelbar diagram‑automation utan COM‑interop eller Office‑installationer.

Vad blir nästa steg? Prova att byta datakälla till en live‑databas, lägg till villkorliga färger baserat på tröskelvärden, eller exportera samma dokument till PDF för en utskriftsklar rapport. Varje steg bygger på den grund vi lagt, så övergången blir smidig.

Om du stöter på problem eller har idéer för vidare förbättringar—kanske ett staplat stapeldiagram eller ett linjediagram—lämna en kommentar nedan. Lycka till med diagrammen!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Formatera antal dataetiketter i ett diagram](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Talformat för axel i ett diagram](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}