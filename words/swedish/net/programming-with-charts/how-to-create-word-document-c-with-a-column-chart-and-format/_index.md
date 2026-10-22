---
category: general
date: 2026-09-21
description: Lär dig hur du skapar ett Word‑dokument i C# och infogar ett stapeldiagram,
  ställer in etikettposition och visar värden med Aspose.Words i en steg‑för‑steg‑guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: sv
lastmod: 2026-09-21
og_description: Skapa Word-dokument i C# med Aspose.Words. Denna handledning visar
  hur du infogar ett stapeldiagram, ställer in etikettposition och visar värden.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Skapa Word-dokument C# – infoga stapeldiagram, sätt etikett, visa värden
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Hur man skapar ett Word‑dokument i C# med ett stapeldiagram och formaterade
  etiketter
url: /sv/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar Word-dokument C# med ett stapeldiagram och formaterade etiketter

Om du behöver **create Word document C#** som innehåller ett diagram, visar den här guiden exakt hur du gör det. Du kommer att lära dig hur du infogar ett stapeldiagram, placerar dess datalabel och visar labelns värden – allt med Aspose.Words för .NET.

Att generera en Word-fil med diagram krävde tidigare manuellt arbete i Microsoft Word. Med stegen **how to insert chart** som beskrivs här kan du automatisera hela processen från kod, vilket gör rapportgenerering snabb och repeterbar. Handledningen täcker också **how to set label**-egenskaper och **how to display values** så att diagrammet är redo för slutanvändare.

I slutet av den här artikeln har du ett komplett, körbart C#-program som skapar en `.docx`-fil som innehåller ett stapeldiagram där datalabelerna visas inuti varje stapel och visar sina numeriska värden.

## Förutsättningar

* .NET 6.0 SDK eller senare installerat  
* En licensierad kopia av **Aspose.Words for .NET** (gratis provversion fungerar för test)  
* En IDE såsom Visual Studio 2022 eller Visual Studio Code  

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Steg 1: Ställ in projektet och lägg till Aspose.Words

Skapa ett nytt konsolprojekt och lägg till Aspose.Words‑paketet:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

`dotnet add package`‑kommandot hämtar den senaste stabila versionen av **Aspose.Words**, som innehåller diagram‑API:et som används i **insert column chart word**‑exemplet.

## Steg 2: Skapa ett nytt tomt Word-dokument

Den första kodsnutten skapar ett tomt dokument och en `DocumentBuilder` som låter dig infoga innehåll. Detta är grunden för **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representerar hela `.docx`‑filen, medan `DocumentBuilder` tillhandahåller metoder som `InsertParagraph`, `InsertImage` och, avgörande för den här handledningen, `InsertChart`.

## Steg 3: Infoga ett stapeldiagram (how to insert chart)

Nu infogar vi ett **column chart**. Metoden `InsertChart` tar diagramtypen, bredd och höjd i punkter.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

Vid detta tillfälle innehåller diagrammet en standarddataserie med platshållarvärden. Du kan ersätta seriedatan om du behöver egna siffror, men för att demonstrera **how to set label** och **how to display values** är standarddatan tillräcklig.

## Steg 4: Placera datalabeln inuti varje stapel (how to set label)

Datalabeler är den text som visas på varje stapel. För att göra diagrammet lättare att läsa flyttar vi labeln inuti stapeln och aktiverar dess numeriska värde.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` placerar labeln högst upp på stapeln men fortfarande inuti stapelns form, vilket är en vanlig visuell stil för rapporter. Att sätta `ShowValue` till `true` uppfyller kravet **how to display values**.

## Steg 5: Spara dokumentet

Till sist skriver du dokumentet till disk. Filen kan öppnas med Microsoft Word, LibreOffice eller någon visare som stödjer Open XML‑formatet.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

När programmet körs skapas `output.docx` som innehåller ett stapeldiagram med datalabeler placerade inuti varje stapel och som visar deras värden.

### Förväntat resultat

När du öppnar `output.docx` bör du se ett enda stapeldiagram liknande bilden nedan. Varje stapel har en numerisk label högst upp, inuti stapeln, som visar serievärdet.

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *Diagram i ett Word‑dokument skapat med C# som demonstrerar hur man infogar column chart word och visar värden.*

## Vanliga variationer och kantfall

### Lägg till anpassad data i diagrammet

Om du behöver ersätta platshållardatan kan du ändra diagrammets `Series`‑samling:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Ändra labelns teckensnitt och färg

Du kan ytterligare anpassa labelns utseende:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Infoga flera diagram

`DocumentBuilder` kan infoga så många diagram du behöver. Anropa bara `InsertChart` igen efter att du flyttat markören med `builder.Writeln()` eller `builder.InsertParagraph()`.

## Pro‑tips

* **Pro tip:** Sätt `chart.HasTitle = true` och tilldela `chart.Title.Text` för att ge diagrammet en beskrivande rubrik. Detta förbättrar tillgängligheten för skärmläsare.
* **Watch out for:** När du sparar till en nätverksdel, se till att applikationen har skrivbehörighet; annars kommer `doc.Save` att kasta ett `UnauthorizedAccessException`.
* **Performance tip:** Återanvänd en enda `DocumentBuilder`‑instans för flera infogningar; att skapa en ny builder för varje operation ger onödig belastning.

## Slutsats

Du vet nu hur du **create Word document C#** som innehåller ett stapeldiagram, hur du **insert chart**‑element, **set label**‑positioner och **display values** inuti varje stapel. Det kompletta kodexemplet ovan är redo att köras, och du kan utöka det med anpassad data, styling eller ytterligare diagram.

Nästa steg är att utforska relaterade ämnen som **how to insert picture**, **how to generate tables** eller **how to apply document themes** för att göra dina automatiserade rapporter ännu rikare. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}