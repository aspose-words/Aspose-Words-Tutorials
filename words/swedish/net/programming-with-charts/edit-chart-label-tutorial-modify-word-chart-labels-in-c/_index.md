---
category: general
date: 2026-09-11
description: Handledning för att redigera diagrametiketter som visar hur man ändrar
  diagrametikettens position, anpassar diagrammets datamärkning, döljer diagramkategorins
  namn och visar diagrametikettens värde med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: sv
lastmod: 2026-09-11
og_description: Handledningen för att redigera diagrametiketter guidar dig genom att
  ändra diagrametikettens position, anpassa diagramdatatetiketten, dölja diagramkategorins
  namn och visa diagrametikettens värde med Aspose.Words för .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Redigera diagrametiketthandledning – anpassa Word-diagrametiketter i C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Redigera diagrametiketthandledning – ändra Word‑diagrametiketter i C#
url: /sv/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Redigera diagrametikett‑handledning – ändra Word‑diagrametiketter i C#

Om du behöver **edit chart label tutorial** för ett Word‑dokument, visar den här guiden exakt hur du ändrar diagrametikettens position, anpassar diagrammets dataetikett, döljer diagramkategorins namn och visar diagrametikettens värde med Aspose.Words för .NET. Du får ett komplett, körbart exempel som du kan klistra in i vilket C#‑projekt som helst.

Att arbeta med diagrametiketter är ett vanligt krav när man genererar rapporter, fakturor eller instrumentpaneler programatiskt. Denna handledning täcker varje steg – från att ladda dokumentet till att spara ändringarna – så att du kan producera välpolerade diagram utan manuell redigering.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare installerat  
* En giltig Aspose.Words för .NET‑licens (eller en tillfällig utvärderingsnyckel)  
* Visual Studio 2022 eller någon C#‑kompatibel IDE  
* En Word‑fil (`Chart.docx`) som innehåller minst ett diagram  

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Steg 1: Ställ in projektet och importera namnrymder

Skapa en ny konsolapplikation och lägg till Aspose.Words‑NuGet‑paketet:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Öppna `Program.cs` och importera de nödvändiga namnrymderna:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Dessa namnrymder ger dig åtkomst till `Document`‑klassen för att hantera Word‑filer och `Chart`‑klasserna för att manipulera diagramelement.

## Steg 2: Ladda Word‑dokumentet som innehåller ett diagram

Den första handlingsbara raden laddar källdokumentet. Ersätt `YOUR_DIRECTORY` med den faktiska sökvägen där `Chart.docx` finns.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

När dokumentet laddas skapas en in‑memory‑representation som du kan traversera och modifiera.

## Steg 3: Hämta det första diagrammet i dokumentet

Diagram lagras som barnnoder av typen `NodeType.Chart`. Metoden `GetChild` söker i dokumentträdet och returnerar diagrammet du vill redigera.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Om dokumentet innehåller flera diagram kan du ändra indexet för att rikta in dig på ett annat.

## Steg 4: Åtkomst och anpassning av dataetiketten för den första serien

Varje diagramserie har ett `DataLabel`‑objekt som styr hur etiketten visas. Koden nedan demonstrerar de fyra nyckelanpassningarna som krävs av handledningens sekundära nyckelord.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Varför dessa inställningar är viktiga**

* `DataLabelPosition.Center` flyttar etiketten från standardpositionen utanför datapunkten till mitten av datapunkten, vilket gör diagrammet lättare att läsa när punkterna är tätt packade.  
* Att ange en anpassad `Separator` låter dig styra hur serienamnet, värdet och andra delar sammanfogas.  
* Att dölja kategorinamnet (`ShowCategoryName = false`) minskar visuellt brus när kategorin redan är tydlig från axeln.  
* Att aktivera `ShowValue` säkerställer att det faktiska datavärdet är synligt, vilket ofta krävs i finansiella eller statistiska rapporter.

## Steg 5: Spara det ändrade dokumentet

Efter att du justerat etikettens egenskaper, spara ändringarna till en ny fil:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Den nya filen (`CustomLabelChart.docx`) innehåller samma diagramlayout men med den etikettstil du definierat.

## Fullständig källkod

Nedan är det kompletta, färdiga programmet. Kopiera det till `Program.cs`, justera filsökvägarna och kör projektet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Förväntat resultat

Öppna `CustomLabelChart.docx` i Microsoft Word. Du bör se den första seriens diagrametikett centrerad på varje datapunkt, som bara visar det numeriska värdet och använder “; ” som separator. Kategorinamnen visas inte längre bredvid värdena.

## Vanliga frågor och kantfall

| Fråga | Svar |
|----------|--------|
| **Vad händer om dokumentet inte innehåller något diagram?** | Exemplet kontrollerar om diagrammet är `null` och avslutar smidigt med ett konsolmeddelande. |
| **Kan jag redigera etiketter för flera serier?** | Ja. Loopa igenom `chart.Series` och tillämpa samma `DataLabel`‑inställningar på varje `Series[i].DataLabel`. |
| **Hur ändrar jag teckensnittsstilen för etiketten?** | Använd `label.Font` (t.ex. `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Stöds `DataLabelPosition.Center` för alla diagramtyper?** | De flesta 2‑D‑diagramtyper stöder det. För 3‑D‑diagram kan vissa positioner ignoreras av Word. |
| **Behöver jag en licens för Aspose.Words?** | Utvärderingsläget fungerar men lägger till ett vattenmärke. En licens tar bort vattenmärket och låser upp full funktionalitet. |

## Pro‑tips

* **Batch‑behandling:** Inslå laddnings‑ och sparlogiken i en metod som tar emot in‑ och ut‑sökvägar. Detta gör det enkelt att bearbeta dussintals dokument i en slinga.  
* **Prestanda:** Återanvänd en enda `Document`‑instans när du ändrar flera diagram i samma fil för att undvika upprepad I/O.  
* **Testning:** Verifiera etikettändringar genom att automatisera en visuell diff (t.ex. med en headless Word‑visare) om du behöver påstå resultatet i CI‑pipelines.

## Nästa steg

Nu när du behärskar grunderna i **edit chart label tutorial**, överväg att utforska:

* **Ändra diagrametikettens position** för andra serier eller olika diagramtyper  
* **Anpassa diagrammets dataetikett**‑formatering såsom talformat, teckensnittsfärger eller bakgrundsfyllning  
* **Dölj diagramkategorins namn** samtidigt som du visar serienamnet för diagram med flera serier  
* **Visa diagrametikettens värde** tillsammans med procentvärden för cirkeldiagram  

Dessa ämnen fördjupar din kontroll över Word‑diagramens estetik och förbereder dig för avancerade rapporteringsscenarier.

---

*Lycka till med kodningen! Om du fann den här handledningen hjälpsam, dela den med kollegor eller bidra med förbättringar på GitHub.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}