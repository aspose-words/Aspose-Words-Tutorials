---
category: general
date: 2026-09-14
description: Infoga radardiagram i Word med C#. Lär dig hur du sätter diagramtitel,
  lägger till flera serier och skapar diagrammet programatiskt på bara några rader.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: sv
lastmod: 2026-09-14
og_description: Infoga radardiagram i Word med C#. Denna handledning visar hur du
  ställer in diagramrubrik, lägger till flera serier och skapar diagrammet programatiskt.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Infoga radardiagram i Word med C# – snabb programmeringsguide
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Infoga radardiagram i Word med C# – steg‑för‑steg‑guide
url: /sv/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga radardiagram i Word med C# – steg‑för‑steg guide

Om du behöver **infoga radardiagram** i ett Word‑dokument, visar den här guiden hur du gör det programatiskt med C#. Du kommer också att lära dig hur du **sätter diagramtitel**, lägger till ett **radardiagram med flera serier**, och sparar filen utan att lämna din IDE.

Tutorialen täcker allt från projektuppsättning till det sista `doc.Save`‑anropet, så att du kan kopiera‑klistra in det kompletta exemplet och köra det omedelbart. Ingen extern dokumentationsuppslagning krävs.

## Förutsättningar

* .NET 6 (eller senare) installerat.
* En giltig Aspose.Words for .NET‑licens (eller en tillfällig utvärderingsnyckel).
* Visual Studio 2022 eller någon C#‑IDE du föredrar.

> **Proffstips:** Om du använder gratisprovan, kom ihåg att ställa in licensen innan den första `Document`‑skapelsen för att undvika utvärderingsvattenstämpeln.

## Steg 1: Infoga radardiagram i ett Word‑dokument

Den första operationen är att skapa ett nytt `Document` och en `DocumentBuilder`. Buildern ger dig åtkomst till dokumentets innehåll och låter dig placera ett **radardiagram** exakt där du behöver det.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Varför detta steg är viktigt:* `InsertChart` skapar ett diagramobjekt som du kan konfigurera helt innan dokumentet sparas. Genom att använda `ChartType.Radar` instrueras Word att rendera ett radiellt diagram istället för ett stapel‑ eller linjediagram.

## Steg 2: Ställ in diagramtitel och axelgradueringar

Ett diagram utan titel kan vara förvirrande. Här **sätter vi diagramtitel** till “Sales Radar” och aktiverar gradueringar på båda axlarna (tillgängligt från Aspose.Words 24.9 och framåt).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Varför detta steg är viktigt:* Titeln ger läsarna kontext, och gradueringar förbättrar läsbarheten genom att visa var varje datapunkt ligger på skalan.

## Steg 3: Skapa flera serier för radardiagram

Ett **radardiagram med flera serier** låter dig jämföra olika perioder sida‑vid‑sida. Nedan lägger vi till två serier—Q1 och Q2—varje med tre datapunkter.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Varför detta steg är viktigt:* Att lägga till flera serier visar hur man jämför dataset på samma radar, ett vanligt krav för försäljning, prestanda eller enkätresultat.

## Steg 4: Spara Word‑dokumentet programatiskt

Till sist **skapar du diagrammet programatiskt** och sparar dokumentet till disk. `Save`‑metoden skriver en `.docx`‑fil som kan öppnas i Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

När du öppnar `RadialGraduations.docx` kommer du att se ett radardiagram med titeln “Sales Radar” med två serier (Q1 och Q2) plottade mot månaderna Jan‑Mar.

### Förväntat resultat

![Radardiagram i Word](https://example.com/radar-chart.png){: .align-center alt="Word‑dokument som visar ett radardiagram med två dataserier"}

Skärmdumpen (eller den faktiska filen) bekräftar att diagrammet har infogats, fått titel och fyllts i korrekt.

## Fullt, körbart exempel

När vi sätter ihop allt, här är ett fristående program som du kan kompilera och köra:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kör programmet, öppna den genererade filen och verifiera att **infoga radardiagram**‑operationen lyckades.

## Vanliga frågor & edge cases

| Fråga | Svar |
|----------|--------|
| **Kan jag ändra diagramtypen efter infogning?** | Ja. Efter `InsertChart` tilldelar du en ny `ChartType` till `chart.Type`. Att skapa diagrammet med rätt typ från början är dock mer effektivt. |
| **Vad händer om jag behöver mer än två serier?** | Anropa `chart.Series.Add` för varje ytterligare serie. Diagrammet justerar automatiskt legend och färger. |
| **Hur anpassar jag färger eller markörer?** | Använd `chart.Series[i].Format.Fill.ForeColor` för fyllningsfärger och `chart.Series[i].Marker` för markörstilar. |
| **Är API:et kompatibelt med .NET Framework?** | Samma kod fungerar med .NET Framework 4.7+; referera bara till rätt Aspose.Words‑DLL. |
| **Vad händer om jag använder en äldre version av Aspose.Words?** | Gradueringar (`HasGraduations`) introducerades i 24.9. För äldre versioner kan du manuellt lägga till rutnätlinjer med `chart.AxisX.MajorGridLines` och `chart.AxisY.MajorGridLines`. |

## Slutsats

Du vet nu hur du **infogar radardiagram** i ett Word‑dokument med C#, **sätter diagramtitel**, lägger till ett **radardiagram med flera serier**, och **skapar diagrammet programatiskt**. Denna helhetslösning låter dig automatisera rapportering, instrumentpaneler eller vilket scenario som helst där visuell jämförelse av kategorier krävs.

Nästa steg, utforska relaterade ämnen som **anpassa diagramfärger**, **exportera diagram som bilder**, eller **bädda in diagram i PDF‑filer**. Experimentera med olika dataset för att se hur radariseringen anpassar sig.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Infoga ett bubbeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Infoga områdesdiagram i Word‑dokument | Aspose.Words för .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}