---
title: Uppdatera diagramseriedata i ett Word‑dokument med Aspose.Words för .NET
weight: 610
limit:
description: Lär dig att modifiera datapunkter i diagramserier i ett Word‑dokument och uppdatera diagrammet med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig att modifiera datapunkter i diagramserier i ett Word‑dokument
    och uppdatera diagrammet med Aspose.Words för .NET.
  headline: Uppdatera diagramseriedata i ett Word‑dokument med Aspose.Words för .NET
  type: TechArticle
- description: Lär dig att modifiera datapunkter i diagramserier i ett Word‑dokument
    och uppdatera diagrammet med Aspose.Words för .NET.
  name: Uppdatera diagramseriedata i ett Word‑dokument med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt Document, infoga ett stapeldiagram med en DocumentBuilder
      och spara det som den ursprungliga filen.
    text: Skapa ett nytt Document, infoga ett stapeldiagram med en DocumentBuilder
      och spara det som den ursprungliga filen.
  - name: Öppna den sparade filen och lokalisera diagramformen för att hämta det befintliga
      Chart‑objektet.
    text: Öppna den sparade filen och lokalisera diagramformen för att hämta det befintliga
      Chart‑objektet.
  - name: Rensa den första seriens värden och lägg till nya punkter, justera sedan
      den andra serien genom att ta bort dess första punkt och lägga till en ny.
    text: Rensa den första seriens värden och lägg till nya punkter, justera sedan
      den andra serien genom att ta bort dess första punkt och lägga till en ny.
  - name: Spara det modifierade dokumentet till en ny fil som innehåller det uppdaterade
      diagrammet.
    text: Spara det modifierade dokumentet till en ny fil som innehåller det uppdaterade
      diagrammet.
  type: HowTo
- questions:
  - answer: Använd `document.GetChildNodes(NodeType.Shape, true)` för att hämta alla
      former, filtrera sedan med `s.HasChart` och välj den första (eller den du behöver)
      – detta undviker att plocka orelaterade bilder eller textrutor.
    question: Hur kan jag på ett pålitligt sätt lokalisera diagramformen i ett dokument
      som kan innehålla andra former?
  - answer: '`ClearValues()` tar bort de befintliga datapunkterna; utan den läggs
      de nya punkterna till efter de gamla, vilket kan leda till duplicerade kategorier
      eller felaktiga totalsummor.'
    question: Varför måste jag anropa `ClearValues()` innan jag lägger till nya punkter
      i en serie?
  - answer: Använd `FromString` när diagrammets X‑axelkategorier är textuella (t.ex.
      "Group A"), och `FromDouble` när axeln förväntar sig numeriska värden såsom
      datum eller mätningar.
    question: När bör jag använda `ChartXValue.FromString` jämfört med `ChartXValue.FromDouble`
      för X‑axelvärdena?
  - answer: Försök att komma åt en icke‑existerande serie kastar ett `ArgumentOutOfRangeException`;
      kontrollera alltid `existingChart.Series.Count` innan du refererar till ett
      specifikt index.
    question: Vad händer om diagrammet bara har en serie och jag försöker komma åt
      `existingChart.Series[1]`?
  - answer: Att spara `openedDoc` räcker eftersom det är den dokumentinstans som innehåller
      det modifierade diagrammet; det ursprungliga `document` användes bara för att
      skapa den initiala filen.
    question: Behöver jag spara om det ursprungliga `document` efter att ha modifierat
      diagrammet, eller räcker det att spara `openedDoc`?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Redigera diagramseriedata i Word
og_description: Steg‑för‑steg‑guide för att ändra ett diagrams serievärden i en Word‑fil med Aspose.Words för .NET.
og_image_alt: Guide som visar ett Word‑dokument med ett stapeldiagram före och efter uppdatering av dess seriedata med Aspose.Words för .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uppdatera diagramseriedata i ett Word‑dokument med Aspose.Words för .NET
Denna handledning visar hur man skapar ett Word‑dokument som innehåller ett stapeldiagram, sedan öppnar filen igen, hämtar de befintliga diagramserierna, ändrar deras datapunkter och sparar dokumentet så att diagrammet visar de nya värdena. Följ den steg‑för‑steg‑koden för att se hur enkelt det är att programatiskt justera diagramdata med Aspose.Words för .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Hur kan jag på ett pålitligt sätt lokalisera diagramformen i ett dokument som kan innehålla andra former?**  
A: Använd `document.GetChildNodes(NodeType.Shape, true)` för att hämta alla former, filtrera sedan med `s.HasChart` och välj den första (eller den du behöver) – detta undviker att plocka orelaterade bilder eller textrutor.

**Q: Varför måste jag anropa `ClearValues()` innan jag lägger till nya punkter i en serie?**  
A: `ClearValues()` tar bort de befintliga datapunkterna; utan den läggs de nya punkterna till efter de gamla, vilket kan leda till duplicerade kategorier eller felaktiga totalsummor.

**Q: När bör jag använda `ChartXValue.FromString` jämfört med `ChartXValue.FromDouble` för X‑axelvärdena?**  
A: Använd `FromString` när diagrammets X‑axelkategorier är textuella (t.ex. "Group A"), och `FromDouble` när axeln förväntar sig numeriska värden såsom datum eller mätningar.

**Q: Vad händer om diagrammet bara har en serie och jag försöker komma åt `existingChart.Series[1]`?**  
A: Försök att komma åt en icke‑existerande serie kastar ett `ArgumentOutOfRangeException`; kontrollera alltid `existingChart.Series.Count` innan du refererar till ett specifikt index.

**Q: Behöver jag spara om det ursprungliga `document` efter att ha modifierat diagrammet, eller räcker det att spara `openedDoc`?**  
A: Att spara `openedDoc` räcker eftersom det är den dokumentinstans som innehåller det modifierade diagrammet; det ursprungliga `document` användes bara för att skapa den initiala filen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}