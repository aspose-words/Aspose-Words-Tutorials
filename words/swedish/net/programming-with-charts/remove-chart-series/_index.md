---
title: Ta bort en Chart Series från ett Word Document med Aspose.Words for .NET
weight: 510
limit:
description: Lär dig hur du tar bort en specifik dataserie från ett stapeldiagram i ett Word‑dokument med Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig hur du tar bort en specifik dataserie från ett stapeldiagram
    i ett Word‑dokument med Aspose.Words for .NET.
  headline: Ta bort en Chart Series från ett Word Document med Aspose.Words for .NET
  type: TechArticle
- description: Lär dig hur du tar bort en specifik dataserie från ett stapeldiagram
    i ett Word‑dokument med Aspose.Words for .NET.
  name: Ta bort en Chart Series från ett Word Document med Aspose.Words for .NET
  steps:
  - name: Skapa ett nytt Word Document och en DocumentBuilder som är kopplad till
      det.
    text: Skapa ett nytt Word Document och en DocumentBuilder som är kopplad till
      det.
  - name: Infoga ett stapeldiagram med storleken 432×252 punkter och hämta Chart‑objektet
      för vidare manipulation.
    text: Infoga ett stapeldiagram med storleken 432×252 punkter och hämta Chart‑objektet
      för vidare manipulation.
  - name: Definiera det nollbaserade indexet för den serie som ska tas bort (den andra
      serien).
    text: Definiera det nollbaserade indexet för den serie som ska tas bort (den andra
      serien).
  - name: Om indexet är giltigt, anropa RemoveAt på diagrammets Series‑samling för
      att ta bort den serien.
    text: Om indexet är giltigt, anropa RemoveAt på diagrammets Series‑samling för
      att ta bort den serien.
  - name: Spara det uppdaterade dokumentet till en .docx‑fil.
    text: Spara det uppdaterade dokumentet till en .docx‑fil.
  type: HowTo
- questions:
  - answer: '`if`‑kontrollen (`targetSeriesIdx < columnChart.Series.Count`) kommer
      att misslyckas, så `RemoveAt` anropas aldrig och diagrammet förblir oförändrat.'
    question: Vad händer om jag skickar ett index som är lika med antalet serier i
      diagrammet?
  - answer: Ja, efter `columnChart.Series.RemoveAt` regenereras förklaringen för att
      återspegla de återstående serierna, så den borttagna posten försvinner från
      förklaringen.
    question: Uppdateras diagrammets förklaring automatiskt när en serie tas bort?
  - answer: Koden fungerar för alla diagramtyper som stöder en `Series`‑samling; ändra
      bara `ChartType.Column` till önskad typ när du infogar diagrammet.
    question: Kan jag använda samma kod för att ta bort en serie från ett linje‑ eller
      cirkeldiagram?
  - answer: Ett diagram med noll serier är fortfarande en giltig `Shape` och kommer
      att sparas, men det kommer att visas tomt i det resulterande dokumentet.
    question: Om jag tar bort den enda serien i ett diagram, kommer diagrammet fortfarande
      att sparas korrekt?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Ta bort en Chart Series i ett Word Document
og_description: Steg‑för‑steg‑guide för att ta bort en dataserie från ett Word‑diagram med Aspose.Words for .NET.
og_image_alt: Guide som visar hur man tar bort en specifik dataserie från ett stapeldiagram i ett Word‑dokument med Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ta bort en Chart Series från ett Word Document med Aspose.Words
Den här handledningen visar hur man skapar ett Word‑dokument, lägger till ett stapeldiagram med DocumentBuilder och sedan tar bort en specifik dataserie från diagrammet med metoden ChartSeriesCollection.RemoveAt. I slutet har du ett sparat dokument där den oönskade serien har tagits bort, vilket ger dig exakt kontroll över diagrammets innehåll direkt från .NET‑kod.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Vad händer om jag skickar ett index som är lika med antalet serier i diagrammet?**  
A: `if`‑kontrollen (`targetSeriesIdx < columnChart.Series.Count`) kommer att misslyckas, så `RemoveAt` anropas aldrig och diagrammet förblir oförändrat.

**Q: Uppdateras diagrammets förklaring automatiskt när en serie tas bort?**  
A: Ja, efter `columnChart.Series.RemoveAt` regenereras förklaringen för att återspegla de återstående serierna, så den borttagna posten försvinner från förklaringen.

**Q: Kan jag använda samma kod för att ta bort en serie från ett linje‑ eller cirkeldiagram?**  
A: Koden fungerar för alla diagramtyper som stöder en `Series`‑samling; ändra bara `ChartType.Column` till önskad typ när du infogar diagrammet.

**Q: Om jag tar bort den enda serien i ett diagram, kommer diagrammet fortfarande att sparas korrekt?**  
A: Ett diagram med noll serier är fortfarande en giltig `Shape` och kommer att sparas, men det kommer att visas tomt i det resulterande dokumentet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}