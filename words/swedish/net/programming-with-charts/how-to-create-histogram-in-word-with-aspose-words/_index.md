---
category: general
date: 2026-09-21
description: Hur man skapar ett histogram i Word med Aspose.Words. Lär dig hur du
  ställer in histogramklasser och konfigurerar histogramklasser för exakt datavisualisering.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: sv
lastmod: 2026-09-21
og_description: Hur du skapar ett histogram i Word med Aspose.Words. Denna handledning
  visar hur du ställer in histogramintervall och konfigurerar histogramintervall för
  korrekta diagram.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: Skapa ett histogram i Word med Aspose.Words – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: Hur man skapar ett histogram i Word med Aspose.Words
url: /sv/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett histogram i Word med Aspose.Words

Om du behöver skapa ett histogram i Word gör Aspose.Words processen enkel. Denna guide går igenom varje steg, från att sätta upp projektet till att konfigurera histogramstaplar för tydlig datapresentation. Du kommer också att se hur du ställer in histogramstaplar och konfigurerar histogramstaplar för att matcha dina rapporteringskrav.

## Så skapar du ett histogram i Word – övergripande arbetsflöde

Det övergripande arbetsflödet består av fyra logiska faser:

1. Förbered utvecklingsmiljön.  
2. Skapa ett tomt Word-dokument och hämta en `DocumentBuilder`.  
3. Infoga ett histogramdiagram och justera dess egenskaper.  
4. Spara dokumentet och verifiera resultatet.

Varje fas behandlas i detalj nedan, och den kompletta källkoden finns i slutet av artikeln.

## Ställ in utvecklingsmiljön

Innan du skriver någon kod, se till att du har följande förutsättningar:

| Prerequisite | Reason |
|--------------|--------|
| .NET 6.0 or later | Tillhandahåller runtime för C#-projekt. |
| Visual Studio 2022 (or any IDE that supports .NET) | Gör det möjligt att kompilera och felsöka exemplet. |
| Aspose.Words for .NET NuGet package | Tillhandahåller `Document`, `DocumentBuilder` och diagramklasser. |

Du kan lägga till Aspose.Words-paketet med NuGet CLI:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Använd en fast version (t.ex. `23.9.0`) i produktion för att undvika oväntade brytande förändringar.

## Infoga ett histogramdiagram

När miljön är klar, skapa ett nytt konsolprojekt och öppna filen `Program.cs`. De två första kodraderna instansierar ett tomt dokument och en `DocumentBuilder` som låter dig manipulera dokumentet:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Anropa sedan `InsertChart` för att lägga till ett histogram. Metoden kräver diagramtypen, bredd och höjd i punkter:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

Vid detta tillfälle innehåller dokumentet en tom histogramplatshållare. När du öppnar den genererade *.docx*-filen kommer du att se ett grått diagramområde redo för data.

![Histogram placeholder in Word document](/images/histogram-placeholder.png){: .img-fluid alt="Skärmbild av ett Word-dokument som visar en histogramdiagramplatshållare skapad med Aspose.Words"}

## Hur man ställer in histogramstaplar

Ett histogram visualiserar fördelningen av numerisk data genom att gruppera värden i *staplar*. `HistogramBins`-egenskapen styr hur många staplar diagrammet visar. Att sätta denna egenskap innan data läggs till säkerställer att diagrammet reserverar rätt antal staplar.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

Du kan justera antalet staplar för att matcha granulariteten i din dataset. Till exempel, ett dataset som sträcker sig från 0 till 100 med ett stapelantal på 10 skapar intervall på 10 enheter vardera (0‑9, 10‑19, …, 90‑100).

> **Why it matters:** Att välja för få staplar kan dölja viktiga mönster, medan för många staplar kan skapa ett brusigt diagram. Testa några värden för att hitta den optimala balansen för din specifika data.

## Konfigurera histogramstaplar för bättre läsbarhet

Utöver antalet staplar vill du ofta märka varje stapel så att läsarna kan se exakt antal. `ShowBinLabels`-egenskapen växlar synligheten för dessa etiketter:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

När `ShowBinLabels` är satt till `true` renderar Word en numerisk etikett ovanpå varje stapel. Detta lilla konfigurationssteg förbättrar diagrammets tolkbarhet avsevärt, särskilt i rapporter där mottagarna kanske inte har det ursprungliga datasetet.

Du kan också anpassa etikettens utseende, såsom teckenstorlek eller färg, via `HistogramLabel`-objektet (tillgängligt i senare versioner av Aspose.Words). Följande kodsnutt demonstrerar en vanlig justering:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **Edge case:** Om du sätter `HistogramBins` till ett värde som är större än antalet distinkta datapunkter, kommer vissa staplar att visas som tomma. Diagrammet renderas fortfarande korrekt, men den visuella kan se gles ut. Överväg att minska antalet staplar i sådana scenarier.

## Lägg till dataserie till histogrammet

Ett histogram kräver en enda dataserie som representerar de underliggande numeriska värdena. Du kan fylla serien med en array, en `List<double>` eller någon enumererbar samling. Nedan är ett kort exempel som lägger till ett slumpmässigt dataset:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

`AddRange`-metoden konverterar varje värde till en stapel enligt de tidigare definierade `HistogramBins`. Efter detta steg visar diagrammet ett fullt ifyllt histogram.

## Spara och visa det resulterande dokumentet

Slutligen, skriv dokumentet till disk. Du kan välja vilken plats som helst som din applikation kan komma åt. Följande rad sparar filen som `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

Öppna `output.docx` i Microsoft Word för att se ett histogram med tio staplar, märkta värden och det exempeldata du angav. Diagrammet kommer att se liknande ut som bilden nedan:

![Completed histogram in Word](/images/histogram-complete.png){: .img-fluid alt="Word-dokument som visar ett färdigt histogramdiagram med tio staplar och etiketter"}

## Fullt, körbart exempel

När alla delar sätts ihop, här är ett fristående program som du kan kopiera, klistra in och köra:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**Expected output:** När du öppnar `output.docx` visas ett histogram med tio jämnt fördelade staplar, var och en märkt med sitt antal. Diagrammet speglar fördelningen av `data`-arrayen, vilket gör trender omedelbart synliga.

## Vanliga frågor och felsökning

| Question | Answer |
|----------|--------|
| *Vad händer om jag behöver mer än en dataserie?* | Histogram representerar vanligtvis en enda fördelning. Om du behöver flera serier, överväg att använda ett stapeldiagram istället. |
| *Kan jag ändra diagrammets storlek efter infogning?* | Ja. Justera `histogram.Width` och `histogram.Height`-egenskaperna, eller anropa `builder.InsertChart` igen med andra dimensioner. |
| *Fungerar detta med .NET Framework 4.8?* | Absolut. Aspose.Words stödjer .NET Framework 4.5 och senare, så samma kod körs utan förändringar. |
| *Hur exporterar jag diagrammet som en bild?* | Använd `histogram.ToImage()` för att få en `System.Drawing.Image`, spara sedan med `image.Save("chart.png")`. |

## Slutsats

Du vet nu hur du skapar ett histogram i Word med Aspose.Words, hur du ställer in histogramstaplar och hur du konfigurerar histogramstaplar för tydlig, märkt output. Det kompletta exemplet demonstrerar ett produktionsklart tillvägagångssätt som du kan anpassa till alla datadrivna rapporteringsscenarier.  

Nästa, utforska relaterade ämnen som **hur man skapar pajdiagram i Word**, **anpassa diagramfärger**, och **bädda in Excel-datakällor**. Var och en av dessa bygger på samma `DocumentBuilder`-arbetsflöde, så du kan utöka lösningen med minimal ansträngning.

Lycka till med diagrammen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [hur man skapar pdf från Word – Komplett C#‑guide](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Hur man laddar Word-dokument med Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}