---
category: general
date: 2026-08-20
description: Lägg snabbt till ledlinjer i pajdiagram i Java. Lär dig att infoga, explodera,
  färga om och märka skivor med Chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: sv
lastmod: 2026-08-20
og_description: Lägg till ledlinjer i ett pajdiagram i Java med ett kort exempel.
  Följ den här guiden för att infoga, spränga, färga om och märka segment med Chart
  API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Lägg till ledlinjer i pajdiagram i Java – steg‑för‑steg guide för Chart
  API
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Hur man lägger till ledlinjer i ett cirkeldiagram i Java med Chart API
url: /sv/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till ledlinjer i pajdiagram i Java med Chart API

Om du behöver **lägga till ledlinjer i pajdiagram** i Java, så guidar den här guiden dig genom hela processen. Du kommer att se hur du infogar ett pajdiagram, exploderar en skiva för att framhäva den, ändrar dess färg och slutligen aktiverar ledlinjer som märker den exploderade delen.

Exemplet använder den standard Chart API som finns i många Java-rapporteringsbibliotek. Inga externa verktyg krävs, och koden körs i alla JDK 8+ miljöer.

## Vad du kommer att uppnå

* Skapa ett `Chart` av typen `ChartType.PIE` med en anpassad storlek.  
* Explodera den första skivan för att dra uppmärksamhet.  
* Sätt den exploderade skivans sektorfärg till blå.  
* **Lägg till ledlinjer i pajdiagram** så att skivans etikett tydligt är kopplad.

Du bör redan ha ett Java-projekt med Chart-biblioteket på classpath. Om du använder Maven, lägg till beroendet som visas i avsnittet för förutsättningar.

## Förutsättningar

* JDK 8 eller nyare installerad.  
* Chart-biblioteket (t.ex. `com.example.chart:chart-api:2.5.0`).  
* Grundläggande kunskap om Java-klasser och metodanrop.

---

## Hur man lägger till ledlinjer i pajdiagram

Nedan är ett komplett, körbart program som demonstrerar varje steg. Koden är avsiktligt självständig så att du kan kopiera, klistra in och köra den utan ändringar.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Förklaring av varje steg

| Steg | Vad koden gör | Varför det är viktigt |
|------|-------------------|----------------|
| **1️⃣ Infoga ett pajdiagram** | `builder.insertChart(ChartType.PIE, 400, 300)` skapar ett 400 × 300 pixel pajdiagram. | Skapar diagrambehållaren och definierar dess dimensioner, vilket påverkar etikettplacering och ledlinjelängd. |
| **2️⃣ Explodera den första skivan** | `setExplosion(20)` förskjuter skivan med 20 % av radien. | En exploderad skiva drar betraktarens uppmärksamhet och gör ledlinjen synlig. |
| **3️⃣ Sätt sektorfärg** | `setSectorColor(Color.BLUE)` ändrar skivans fyllning till blå. | Färgkontrast förbättrar läsbarheten, särskilt när skivan är markerad. |
| **4️⃣ Aktivera ledlinjer** | `setLeaderLines(true)` slår på anslutningslinjerna som länkar skivan till dess etikett. | Ledlinjer säkerställer att etiketten förblir läsbar även när skivan flyttas utåt. |

`saveAsPng`-anropet är valfritt men användbart för att verifiera det visuella resultatet. Efter att ha kört programmet bör du se en bild som liknar den nedan.

![Lägg till ledlinjer i pajdiagram](https://example.com/assets/pie-leader-lines.png "Lägg till ledlinjer i pajdiagram – exploderad skiva med blå färg och ledlinjer")

*Figur: Ett pajdiagram där den första skivan är exploderad, färgad blå, och kopplad till sin etikett med en ledlinje.*

## Anpassa ledlinjer (avancerat)

Det grundläggande anropet `setLeaderLines(true)` använder bibliotekets standardstil. Du kan ytterligare styra utseendet:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Dessa alternativ är praktiska när du behöver matcha företagets varumärke eller förbättra tillgänglighet.

### Hantera flera serier

Om ditt pajdiagram innehåller mer än en serie kan du vilja ha ledlinjer endast för en specifik skiva. Använd serieindexet för att rikta in rätt element:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

När en skiva inte är exploderad är ledlinjen vanligtvis dold automatiskt, men du kan tvinga fram den med `setLeaderLineEnabled(true)`.

## Vanliga fallgropar och hur man undviker dem

| Fallgrop | Symptom | Åtgärd |
|--------|---------|-----|
| **Ledlinjer syns inte** | Diagram renderas utan anslutningar. | Se till att skivan är exploderad (`setExplosion` > 0) eller aktivera explicit ledlinjer på skivan. |
| **Etiketter överlappar** | Etiketter kolliderar med varandra. | Öka diagramstorleken eller sätt `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Färg tillämpas inte** | Skivan behåller standardfärgen. | Verifiera att du riktar in rätt serieindex (`getSeries().get(0)`). |
| **Bild sparas inte** | `saveAsPng` kastar ett undantag. | Kontrollera skrivbehörigheter för mål katalogen och att biblioteket stödjer PNG-export. |

## Fullständig källkodslista

För enkelhetens skull, här är den kompletta källfilen igen, inklusive importeringar och kommentarer:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

När du kör detta program genereras `pie-with-leader-lines.png`, som visar ett pajdiagram med en exploderad blå skiva och tydliga ledlinjer som pekar på skivans etikett.

## Slutsats

Du vet nu hur man **lägger till ledlinjer i pajdiagram**-objekt i Java med Chart API. Processen består av att infoga en `ChartType.PIE`, explodera den önskade skivan, anpassa dess färg och aktivera ledlinjer. Med de valfria stilalternativen kan du finjustera linjefärg, tjocklek och etikettplacering för att uppfylla alla visuella krav.

Nästa steg är att utforska relaterade ämnen såsom **pie chart explosion Java**, **set sector color Chart API**, och **builder.insertChart usage** för att skapa mer sofistikerade visualiseringar som donut-diagram, staplade pajer eller interaktiva instrumentpaneler.

Känn dig fri att experimentera med olika skivindex, färger och ledlinjestilar—dina diagram blir mer informativa och visuellt tilltalande med varje justering. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Lägg till datum‑ och tidsvärden till diagramaxel](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Infoga stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}