---
category: general
date: 2026-08-14
description: Skapa ett cirkeldiagram i Word med Java med Aspose.Words. Lär dig hur
  du lägger till seriedata i diagrammet och roterar ett cirkeldiagramsegment med bara
  några rader.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: sv
lastmod: 2026-08-14
og_description: Skapa ett cirkeldiagram i Word med Java och Aspose.Words. Den här
  handledningen visar hur du lägger till seriedata i diagrammet och snabbt roterar
  en cirkeldiagramsskiva.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Skapa ett cirkeldiagram i Word med Java – komplett kodningsguide
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Skapa cirkeldiagram i Word med Java – steg‑för‑steg‑guide
url: /sv/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa pajdiagram i Word med Java – steg‑för‑steg guide

Om du behöver **create pie chart in Word** programatiskt, visar den här guiden exakt hur du gör det med Java och Aspose.Words. Du kommer att lära dig hela arbetsflödet, från att infoga diagrammet till att lägga till datapunkter och rotera den första sektorn.

Att generera ett diagram direkt i en `.docx`‑fil tar bort det manuella kopiera‑och‑klistra‑steget och låter dig automatisera rapporter, fakturor eller instrumentpaneler. På vägen kommer vi också att gå igenom **how to add series data to chart** och hur man **rotate pie chart slice** för bättre visuell betoning.

## Skapa pajdiagram i Word – översikt

Aspose.Words for Java tillhandahåller ett flytande `DocumentBuilder`‑API som kan infoga ett diagramobjekt i ett Word‑dokument. Diagramtypen du väljer bestämmer standardlayouten, och du kan anpassa serier, färger, vinklar och till och med byta till en doughnut‑form med ett enda metodanrop.

### Varför använda Aspose.Words?

* **No Microsoft Office required** – biblioteket fungerar på vilken server eller CI‑miljö som helst.  
* **Full .docx fidelity** – det genererade diagrammet ser identiskt ut som ett som skapats manuellt i Word.  
* **Single‑file dependency** – lägg bara till JAR‑filen så är du klar.

## Hur man lägger till seriedata i diagrammet

Ett diagram utan data är bara en platshållare. `Chart`‑objektet exponerar en `Series`‑samling; varje serie innehåller en lista med numeriska värden som motsvarar sektorer (för ett pajdiagram) eller punkter (för en linje). Att lägga till data är enkelt:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Vad koden gör:**  
* `chart.getSeries()` returnerar en `List<ChartSeries>`.  
* `get(0)` väljer den första serien eftersom ett pajdiagram per definition innehåller endast en serie.  
* `add(double)` lägger till en datapunkt. Värdena konverteras automatiskt till procentandelar som summerar till 100 % när diagrammet renderas.

> **Proffstips:** Om din datakälla innehåller mer än tre kategorier, fortsätt att lägga till värden på samma sätt. Aspose.Words kommer automatiskt att skapa ytterligare sektorer.

## Rotera pajdiagramsektion

Ibland vill du att en viss sektor ska börja vid en specifik vinkel så att det viktigaste segmentet vänds mot betraktaren. Metoden `setFirstSliceAngle(double)` roterar hela diagrammet och flyttar effektivt startpunkten för den första sektorn:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Vinkeln mäts i grader medurs från den vertikala axeln. Att sätta den till `0` (standardvärdet) placerar den första sektorn högst upp. Justera värdet för att framhäva en sektor eller för att följa en designriktlinje.

> **Vanlig fråga:** *Påverkar rotationen datasekvensen?*  
> Nej. Datasekvensen förblir densamma; endast den visuella startpositionen ändras.

## Fullständigt Java‑exempel

Nedan är ett komplett, färdigt‑att‑köra program som skapar ett Word‑dokument med ett pajdiagram, lägger till seriedata, roterar sektorn och sparar filen. Alla nödvändiga import‑satser listas, så du kan kopiera koden till vilken IDE som helst.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Förväntat resultat

* En fil med namnet **PieChart.docx** visas i `output`‑mappen.  
* När du öppnar filen i Microsoft Word visas ett färgglatt pajdiagram med tre sektorer (40 %, 30 %, 30 %).  
* Diagrammet är roterat 45° medurs, så den första sektorn börjar något till höger om den vertikala axeln.

## Vanliga fallgropar och bästa praxis

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Diagram visas tomt** | Dokumentet sparades innan diagrammet var helt renderat. | Anropa `doc.save()` **efter** alla diagramändringar. |
| **Sektorvärden summerar inte till 100 %** | Att lägga till råa tal som inte representerar procent kan leda till oväntad skalning. | Ange värden som logiskt representerar delar av en helhet, eller låt Aspose.Words beräkna procentandelarna automatiskt. |
| **Rotation har ingen effekt** | Att använda `ChartType.DOUGHNUT` utan att sätta `holeSize` kan dölja rotationseffekten. | Behåll diagrammet som `PIE` eller justera `holeSize` efter att ha satt vinkeln. |
| **Filsökvägsfel** | Relativa sökvägar kan lösas olika på Windows jämfört med Linux. | Använd `Paths.get("output", "PieChart.docx").toString()` eller en absolut sökväg för produktionskod. |

### Tips för produktionsanvändning

* **Återanvänd `DocumentBuilder`** – du kan infoga flera diagram i samma dokument genom att anropa `insertChart` upprepade gånger.  
* **Styling** – använd `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` för att visa procentandelar direkt på diagrammet.  
* **Prestanda** – generera diagrammet en gång och klona det (`chart.deepClone()`) om du behöver identiska diagram på flera ställen.

## Rotera pajdiagramsektion – avancerade scenarier

* **Dynamisk vinkel** – beräkna vinkeln baserat på data (t.ex. låt den största sektorn börja högst upp).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Flera serier** – även om ett pajdiagram normalt har en serie, låter Aspose.Words dig lägga till fler för staplade pajer. Rotation gäller fortfarande endast den första serien.

## Slutsats

Du vet nu hur du **create pie chart in Word** med Java, hur du **add series data to chart**, och hur du **rotate pie chart slice** för visuell betoning. Det kompletta exemplet demonstrerar hela arbetsflödet – från dokumentinitiering till sparande av den slutgiltiga `.docx`‑filen – så att du kan integrera diagramgenerering i vilken automatiserad rapporteringspipeline som helst.

### Vad blir nästa?

* Utforska andra diagramtyper (`ChartType.BAR`, `ChartType.LINE`) för att bredda ditt automatiseringsverktyg.  
* Kombinera diagramgenerering med **mail merge** för att skapa personliga rapporter för varje mottagare.  
* Fördjupa dig i **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) för att anpassa till ditt företags varumärke.

Känn dig fri att experimentera med olika datamängder, vinklar och diagramstilar. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hur man konverterar Word till PDF med Aspose.Words för Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}