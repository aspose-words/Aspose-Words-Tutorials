---
category: general
date: 2026-08-07
description: Skapa ett pajdiagram i Word med C# snabbt. Lär dig hur du infogar ett
  pajdiagram, lägger till datamärkningar för pajen, visar procent i diagrammet och
  anpassar diagrammets datamärkningar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: sv
lastmod: 2026-08-07
og_description: Skapa ett cirkeldiagram i Word med C# och Aspose.Words. Denna handledning
  visar hur du infogar ett cirkeldiagram, lägger till datapunktsetiketter och visar
  procentandelen i diagrammet samtidigt som du anpassar diagrammets datapunktsetiketter.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Skapa pajdiagramord i C# – komplett handledning
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Skapa pajdiagram i C# – steg‑för‑steg guide
url: /sv/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa pie chart word i C# – steg‑för‑steg guide

Om du behöver **create pie chart word**‑dokument i C# erbjuder den här guiden en komplett, färdig‑att‑köra‑lösning. Du får se hur du **insert pie chart**, **add data labels pie** och **show percentage chart** samtidigt som du **customize chart data labels** för ett polerat utseende.

Att generera diagram programatiskt sparar dig från manuellt redigerande, särskilt när rapporter eller instrumentpaneler måste produceras automatiskt. I avsnitten nedan kommer du att lära dig allt som krävs för att bädda in ett fullt märkt pie chart i en Word‑fil med hjälp av Aspose.Words för .NET.

## Förutsättningar och installation

* .NET 6.0 SDK eller senare installerat.  
* En giltig Aspose.Words för .NET‑licens (eller en tillfällig utvärderingsnyckel).  
* Visual Studio 2022 (eller någon IDE som stödjer C#).  

Lägg till Aspose.Words NuGet‑paketet i ditt projekt:

```bash
dotnet add package Aspose.Words
```

> **Proffstips:** Om du planerar att generera många diagram, aktivera **Free‑Form Drawing**‑läget (`DocumentBuilder.UseFreeFormDrawing = true`) för bättre prestanda.

## Skapa pie chart word med Aspose.Words

Det första stora steget är att skapa ett tomt Word‑dokument och en `DocumentBuilder`. Detta objekt styr alla efterföljande insättningar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt*: `Document` representerar hela `.docx`‑filen, medan `DocumentBuilder` erbjuder ett flytande API för att lägga till stycken, tabeller och diagram. Att börja med ett rent dokument säkerställer att ingen dold formatering stör diagrammets layout.

## Infoga pie chart i dokumentet

Nu placerar vi ett pie chart i önskad storlek. Metoden `InsertChart` returnerar ett `Chart`‑objekt som vi kan konfigurera vidare.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Varför detta är viktigt*: `ChartType.Pie`‑flaggan instruerar Aspose.Words att generera ett cirkulärt diagram. Bredden (`400`) och höjden (`300`) anges i punkter, vilket ger dig exakt kontroll över diagrammets visuella fotavtryck.

## Fyll diagrammet med data

Ett pie chart kräver minst en serie med numeriska värden. Här lägger vi till tre kategorier: “Apples”, “Bananas” och “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Varför detta är viktigt*: Varje anrop till `AddCategory` skapar en skiva. Det numeriska värdet bestämmer skivans storlek, medan etiketten blir kategorinamnet som visas när dataetiketter är aktiverade.

## Lägg till dataetiketter pie och visa procentdiagram

För att göra diagrammet informativt aktiverar vi dataetiketter, placerar dem utanför skivorna och ber Aspose.Words att visa både kategorinamnet och procentandelen.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Varför detta är viktigt*: Att sätta `Position` till `OutsideEnd` förbättrar läsbarheten, särskilt när skivorna är små. Att aktivera `ShowCategoryName` och `ShowPercentage` uppfyller kravet **show percentage chart** och uppfyller målet **add data labels pie**.

## Anpassa diagrammets dataetiketter ytterligare (valfritt)

Du kanske vill ändra teckensnittet, lägga till en ledarlinje eller dölja förklaringen. Följande kodsnutt visar vanliga anpassningar:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Varför detta är viktigt*: Att anpassa etikettens utseende säkerställer att diagrammet följer ditt dokuments stilguide. Att ta bort förklaringen minskar visuellt brus när dataetiketter redan förmedlar samma information.

## Spara dokumentet med det anpassade diagrammet

Till sist skriver du dokumentet till disk. Välj en sökväg som du har skrivrättigheter till.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

När du öppnar `ChartWithCustomLabels.docx` i Microsoft Word kommer du att se ett pie chart där varje skiva är märkt med sitt kategorinamn och procentandel, placerad utanför skivan, och stylad med de anpassade teckensnittsinställningarna.

### Förväntat resultat

| Skiva   | Värde | Procent | Etikett visad i Word |
|---------|-------|---------|----------------------|
| Apples  | 40    | 40 %    | Apples – 40 %        |
| Bananas | 35    | 35 %    | Bananas – 35 %       |
| Cherries| 25    | 25 %    | Cherries – 25 %      |

Diagrammet bör se ut som illustrationen nedan:

![Word-dokument som visar ett pie chart med procentetiketter utanför varje skiva](pie-chart-word.png "Exempel på create pie chart word")

*Bildens alt‑text innehåller huvudnyckelordet för SEO.*

## Hantera flera serier och kantfall

Det grundläggande exemplet använder en enda serie, vilket är typiskt för ett pie chart. Om du behöver visa flera serier (t.ex. jämföra två år) måste du:

1. Anropa `chart.Series.Add()` för varje ytterligare serie.  
2. Säkerställ att varje serie använder samma kategorier; annars kommer Aspose.Words att kasta ett `ArgumentException`.  
3. Eventuellt, sätt `labels.ShowSeriesName = true` för att särskilja skivorna.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

När flera serier finns renderas diagrammet automatiskt som ett **clustered pie** (även kallat “pie of pies”). Granska resultatet för att verifiera att etiketter är läsbara.

## Vanliga fallgropar och hur man undviker dem

| Problem | Orsak | Lösning |
|---------|-------|---------|
| Etiketter överlappar skivor | Litet diagramområde eller många kategorier | Öka diagrammets dimensioner (`InsertChart(width, height)`) eller byt `Position` till `InsideEnd`. |
| Procentandelar summerar inte till 100 % | Avrundningsfel i data | Använd `labels.ShowPercentage = true` (Aspose.Words normaliserar automatiskt). |
| Diagrammet visas tomt i Word | Saknad licens eller utvärderingstid har gått ut | Se till att en giltig Aspose.Words‑licens laddas innan dokumentet skapas. |
| Teckensnittsfärger skiljer sig från Word‑temat | Anpassat teckensnitt satt i kod | Ta bort anpassade teckensnitt eller matcha Word‑temafärger (`System.Drawing.Color.Black`). |

## Fullständig källkod (körbar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

När programmet körs genereras `ChartWithCustomLabels.docx`, som innehåller ett **create pie chart word**‑exempel som uppfyller alla krav som listas i handledningen.

## Slutsats

Du vet nu hur du **create pie chart word**‑dokument i C# med Aspose.Words. Guiden täckte insättning av ett pie chart, **add data labels pie**, **show percentage chart** och **customize chart data labels** för att uppnå en professionell, datadriven Word‑fil.  

Härifrån kan du utforska relaterade ämnen såsom **insert pie chart** i befintliga stycken, generera **bar**‑ eller **line**‑diagram, eller automatisera batch‑skapande av rapporter med varierande datamängder. Experimentera med olika etikettpositioner, teckensnittsstilar och konfigurationer med flera serier för att anpassa resultatet efter dina specifika rapporteringsbehov.

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Anpassa diagrammets dataetikett](/words/english/net/programming-with-charts/chart-data-label/)
- [Ställ in standardalternativ för dataetiketter i ett diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Infoga stapeldiagram i ett Word‑dokument](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}