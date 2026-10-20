---
category: general
date: 2026-07-16
description: Skapa ett cirkeldiagram i Java med Aspose.Words. Lär dig hur du lägger
  till ledlinjer, visar diagramlegenden och exploderar en del i en enda handledning.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: sv
lastmod: 2026-07-16
og_description: Skapa ett cirkeldiagram i Java med Aspose.Words. Den här guiden visar
  hur du lägger till ledlinjer, visar diagramförklaringen och exploderar en del, så
  du får en polerad visualisering på några minuter.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Skapa cirkeldiagram med Aspose.Words Java – Komplett formateringshandledning
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Skapa cirkeldiagram med Aspose.Words Java – Fullständig steg‑för‑steg‑guide
url: /sv/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa cirkeldiagram med Aspose.Words Java – Fullständig steg‑för‑steg‑guide

Har du någonsin funderat på hur du **skapar ett cirkeldiagram** programatiskt i Java utan att kämpa med lågnivå‑rit‑API:er? Du är inte ensam. Många utvecklare behöver en snabb visualisering för rapporter, instrumentpaneler eller automatiserade dokument, och de vänder sig till Aspose.Words eftersom det sköter det tunga arbetet.  

I den här handledningen går vi igenom ett komplett, färdigt‑att‑köra exempel som inte bara **skapar ett cirkeldiagram** utan också visar hur du **lägger till ledarlinjer**, **visar diagramförklaring** och till och med **exploderar en del** för att framhäva den. I slutet har du en `.docx`‑fil som ser så polerad ut att den kan imponera på en kund.

> **Snabb vinst:** Kodsnutten nedan fungerar direkt med Aspose.Words for Java 23.9 (eller någon nyare version). Inga extra beroenden, bara JAR‑filen.

## Vad du kommer att lära dig

- Skapa ett tomt Word‑dokument med `DocumentBuilder`.
- Infoga ett **cirkeldiagram** i en anpassad storlek.
- Använd funktionen **explode slice** för att markera en datapunkt.
- Aktivera **ledarlinjer** så att den exploderade delen förblir kopplad till etiketten.
- Slå på **diagramförklaringen** så att läsarna omedelbart kan identifiera varje del.
- Spara resultatet till en `.docx`‑fil som du kan öppna i Microsoft Word eller LibreOffice.

**Förutsättningar** – Du behöver:

1. Java 17 (eller senare) installerat.
2. Aspose.Words for Java‑JAR på din classpath.
3. En grundläggande IDE eller textredigerare – IntelliJ IDEA, Eclipse, VS Code, vad du än föredrar.

Nu kör vi igång.

## Steg 1: Initiera dokumentet och byggaren – Förbereder för att **skapa cirkeldiagram**

Först behöver vi en ren dokument‑canvas. `Document` representerar hela Word‑filen, medan `DocumentBuilder` är hjälpredan som låter oss lägga till innehåll.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Varför detta är viktigt:** Att börja med ett färskt `Document` garanterar att inga dolda stilar eller kvarvarande objekt stör diagramrenderingen.

## Steg 2: Infoga **cirkeldiagrammet** – Storleken spelar roll

Aspose.Words gör diagraminfogning till en endaste rad. Här begär vi ett cirkeldiagram som är 400 × 300 punkter – ungefär 5,5 × 4,2 tum på en vanlig skärm.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Proffstips:** Om du behöver en annan storlek, ändra bara de två numeriska argumenten. API:et arbetar i punkter, där 72 punkter = 1 tum.

## Steg 3: **Hur man exploderar en del** – Betona en nyckeldatapunkt

Att explodera en del drar ut den från resten av cirkeln och fångar läsarens uppmärksamhet. Metoden `setExplosion` tar ett heltal som representerar avståndet i punkter.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Vad händer om du har flera serier?** Du kan anropa `setExplosion` på valfri serie‑index (`get(1)`, `get(2)`, …) för att explodera olika delar.

## Steg 4: **Lägg till ledarlinjer** och **visa diagramförklaring** – Koppla ihop punkterna

När en del är exploderad kan etiketten driva iväg. Ledarlinjer håller etiketten fäst, vilket bevarar läsbarheten. Samtidigt ger en förklaring en snabb nyckel för alla delar.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Varför aktivera ledarlinjer?** Utan dem kan etiketten verka svävande, vilket förvirrar användaren om vilken del den tillhör.  
> **Behöver du en anpassad förklaringsposition?** Använd `chart.getLegend().setPosition(LegendPosition.TOP)` eller någon annan enum‑värde.

## Steg 5: Spara dokumentet – Det sista **skapa cirkeldiagram**‑steget

Till sist sparar vi dokumentet till disk. Anpassa sökvägen till en mapp där du har skrivrättigheter.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Kör programmet, öppna den genererade `PieChartDemo.docx`, och du bör se ett snyggt formaterat cirkeldiagram med en exploderad första del, ledarlinjer och en synlig förklaring.

![Cirkeldiagramsexempel som visar exploderad del och förklaring](pie-chart-example.png){: .center-image alt="Skapa cirkeldiagramsexempel med exploderad del, ledarlinjer och förklaring"}

### Förväntat resultat

När du öppnar Word‑filen ser diagrammet ungefär ut så här:

- Ett 400 × 300 pt cirkeldiagram.
- Den första delen är förskjuten med 10 pt.
- En tunn ledarlinje kopplar den exploderade delen till dess etikett.
- En förklaring under diagrammet listar varje serienamn.

Om du inte ser ledarlinjen, dubbelkolla att `setLeaderLines(true)` anropas *efter* explosionsinställningen – ordningen spelar roll.

## Vanliga fallgropar och hur du undviker dem

| Problem | Varför det händer | Lösning |
|-------|----------------|-----|
| **Ingen förklaring visas** | `setShowLegend(true)` saknades eller anropades på fel diagramobjekt. | Se till att du anropar `chart.setShowLegend(true)` **efter** att du hämtat `Chart` från formen. |
| **Ledarlinje saknas** | Delen exploderades inte, eller diagramtypen stödjer inte ledarlinjer. | Endast `ChartType.PIE` (eller `PIE_3D`) stödjer ledarlinjer. Anropa `setExplosion` först, sedan `setLeaderLines(true)`. |
| **Del rör sig inte** | Explosionsvärdet är för lågt (0‑2 pt). | Öka heltalet, t.ex. `setExplosion(10)` eller högre för en mer dramatisk effekt. |
| **Diagrammet ser förvrängt ut** | En icke‑kvadratisk storlek (bredd ≠ höjd) kan klämma cirkeln. | Håll bredd och höjd lika eller nära; 400 × 300 fungerar men 400 × 400 ger en perfekt cirkel. |

## Avancerade justeringar (valfritt)

Om du vill gå längre än grunderna, överväg:

- **Anpassade färger**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Datapunktsetiketter**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D‑effekt**: Byt ut `ChartType.PIE` mot `ChartType.PIE_3D`.

Dessa alternativ låter dig finjustera utseendet så att det matchar företagets varumärkesriktlinjer.

## Sammanfattning – Vad vi uppnådde

Vi började med ett tomt Word‑dokument, **skapade ett cirkeldiagram**, **exploderade den första delen**, **lade till ledarlinjer** och **visade diagramförklaringen**. Hela flödet får plats i en kort `main`‑metod, vilket gör det enkelt att integrera i större rapporteringspipeline.

## Nästa steg

- **Lägg till fler serier**: Fyll diagrammet med riktiga data från en databas eller CSV‑fil.
- **Exportera till PDF**: Använd `doc.save("output.pdf", SaveFormat.PDF);` för att generera en PDF‑version.
- **Kombinera med andra former**: Infoga tabeller, bilder eller ytterligare diagram för en komplett rapport.

Om du är nyfiken på andra diagramtyper – stapel, kolumn, linje – byt bara ut `ChartType.PIE` mot motsvarande enum och följ samma formateringssteg.

---

*Lycka till med diagrammen!* Kommentera gärna om något inte fungerade som förväntat, eller dela hur du anpassade förklaringspositionen. Din feedback hjälper oss alla att bygga bättre automatiserade dokument.


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}