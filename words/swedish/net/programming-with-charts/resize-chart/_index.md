---
title: Ändra diagrammets storlek proportionellt när du ändrar sidstorlek i Word med Aspose.Words för .NET
weight: 210
limit:
description: Lär dig att automatiskt ändra storlek på ett Word‑stapeldiagram när du byter dokumentet till A4 med Aspose.Words för .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig att automatiskt ändra storlek på ett Word‑stapeldiagram när
    du byter dokumentet till A4 med Aspose.Words för .NET.
  headline: Ändra diagrammets storlek proportionellt när du ändrar sidstorlek i Word
    med Aspose.Words för .NET
  type: TechArticle
- description: Lär dig att automatiskt ändra storlek på ett Word‑stapeldiagram när
    du byter dokumentet till A4 med Aspose.Words för .NET.
  name: Ändra diagrammets storlek proportionellt när du ändrar sidstorlek i Word med
    Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt Document‑objekt och en DocumentBuilder för att redigera det.
    text: Skapa ett nytt Document‑objekt och en DocumentBuilder för att redigera det.
  - name: Infoga ett stapeldiagram med storleken 432×252 punkter och hämta dess Chart‑objekt.
    text: Infoga ett stapeldiagram med storleken 432×252 punkter och hämta dess Chart‑objekt.
  - name: Ställ in diagramtitelns text till "Quarterly Revenue" och gör den synlig.
    text: Ställ in diagramtitelns text till "Quarterly Revenue" och gör den synlig.
  - name: Spara dokumentet till en fil som visar diagrammets ursprungliga storlek.
    text: Spara dokumentet till en fil som visar diagrammets ursprungliga storlek.
  - name: Ändra dokumentets pappersstorlek till A4 och uppdatera layouten.
    text: Ändra dokumentets pappersstorlek till A4 och uppdatera layouten.
  - name: Beräkna en ny diagrambredd som är 80 % av sidbredden samtidigt som det ursprungliga
      bildförhållandet bevaras.
    text: Beräkna en ny diagrambredd som är 80 % av sidbredden samtidigt som det ursprungliga
      bildförhållandet bevaras.
  - name: Om formen innehåller ett diagram, tillämpa den beräknade bredden och höjden
      för att ändra dess storlek.
    text: Om formen innehåller ett diagram, tillämpa den beräknade bredden och höjden
      för att ändra dess storlek.
  - name: Spara dokumentet efter att diagrammet har ändrats i storlek för att återspegla
      den nya sidstorleken.
    text: Spara dokumentet efter att diagrammet har ändrats i storlek för att återspegla
      den nya sidstorleken.
  type: HowTo
- questions:
  - answer: Ja. Att ändra `docBuilder.PageSetup.PaperSize` justerar inte automatiskt
      befintliga former, så du måste själv beräkna och tilldela `chartContainer.Width`
      och `Height` som visas.
    question: Behöver jag manuellt ändra diagrammets storlek efter att ha ändrat dokumentets
      pappersstorlek?
  - answer: Den lagrar `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      och beräknar sedan `newChartHeight = newChartWidth * originalAspectRatio` efter
      att den nya bredden har bestämts.
    question: Hur behåller koden diagrammets ursprungliga bredd‑till‑höjd‑förhållande
      vid storleksändring?
  - answer: '`UpdatePageLayout()` tvingar layoutmotorn att omvärdera sidmåtten, vilket
      säkerställer att `docBuilder.PageSetup.PageWidth` visar den nya A4‑bredden innan
      diagrammets storlek beräknas om.'
    question: Varför anropas `myDoc.UpdatePageLayout()` efter att pappersstorleken
      har satts till A4?
  - answer: '`if (chartContainer.HasChart)`‑kontrollen förhindrar att koden tilldelar
      `Width` och `Height` när inget diagram finns, vilket undviker ett körningsfel.'
    question: Vad händer om den infogade formen faktiskt inte innehåller ett diagram?
  - answer: Absolut—byt ut multiplikatorn `0.8` mot vilken proportion du föredrar;
      resten av storleksändringslogiken kommer fortfarande att bevara det ursprungliga
      bildförhållandet.
    question: Kan jag ändra 80 %‑skalningsfaktorn till ett annat värde?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Ändra storlek på ett Word‑diagram när du byter till A4
og_description: Behåll ditt diagram proportionellt genom att automatiskt ändra storlek på det efter att du bytt dokumentet till A4.
og_image_alt: Skärmbild som visar ett stapeldiagram som automatiskt har ändrats i storlek för att passa ett A4‑storat Word‑dokument med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ändra diagrammets storlek proportionellt när du ändrar sidstorlek i Word med Aspose.Words för .NET
Denna handledning visar hur man infogar ett stapeldiagram i ett Word‑dokument, byter dokumentets sidstorlek till A4 och låter diagrammet automatiskt ändra storlek så att det förblir proportionellt mot den nya sidbredden. Genom att följa stegen kommer du att se diagrammet anpassa sina dimensioner utan manuell skalning, vilket säkerställer en konsekvent layout över olika sidformat.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Behöver jag manuellt ändra diagrammets storlek efter att ha ändrat dokumentets pappersstorlek?**  
A: Ja. Att ändra `docBuilder.PageSetup.PaperSize` justerar inte automatiskt befintliga former, så du måste själv beräkna och tilldela `chartContainer.Width` och `Height` som visas.

**Q: Hur behåller koden diagrammets ursprungliga bredd‑till‑höjd‑förhållande vid storleksändring?**  
A: Den lagrar `originalAspectRatio = chartContainer.Height / chartContainer.Width` och beräknar sedan `newChartHeight = newChartWidth * originalAspectRatio` efter att den nya bredden har bestämts.

**Q: Varför anropas `myDoc.UpdatePageLayout()` efter att pappersstorleken har satts till A4?**  
A: `UpdatePageLayout()` tvingar layoutmotorn att omvärdera sidmåtten, vilket säkerställer att `docBuilder.PageSetup.PageWidth` visar den nya A4‑bredden innan diagrammets storlek beräknas om.

**Q: Vad händer om den infogade formen faktiskt inte innehåller ett diagram?**  
A: `if (chartContainer.HasChart)`‑kontrollen förhindrar att koden tilldelar `Width` och `Height` när inget diagram finns, vilket undviker ett körningsfel.

**Q: Kan jag ändra 80 %‑skalningsfaktorn till ett annat värde?**  
A: Absolut—byt ut multiplikatorn `0.8` mot vilken proportion du föredrar; resten av storleksändringslogiken kommer fortfarande att bevara det ursprungliga bildförhållandet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}