---
title: Lägg till en namngiven dataserie i ett histogramdiagram i Word med Aspose.Words för .NET
weight: 610
limit:
description: Lär dig hur du bäddar in ett histogramdiagram i ett Word‑dokument och lägger till en namngiven dataserie med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig hur du bäddar in ett histogramdiagram i ett Word‑dokument och
    lägger till en namngiven dataserie med Aspose.Words för .NET.
  headline: Lägg till en namngiven dataserie i ett histogramdiagram i Word med Aspose.Words
    för .NET
  type: TechArticle
- description: Lär dig hur du bäddar in ett histogramdiagram i ett Word‑dokument och
    lägger till en namngiven dataserie med Aspose.Words för .NET.
  name: Lägg till en namngiven dataserie i ett histogramdiagram i Word med Aspose.Words
    för .NET
  steps:
  - name: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
    text: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
  - name: Infoga en histogramdiagramform av storleken 500×300 i dokumentet och hämta
      dess Chart‑objekt.
    text: Infoga en histogramdiagramform av storleken 500×300 i dokumentet och hämta
      dess Chart‑objekt.
  - name: Ta bort den standardplatshållarserien som Aspose.Words lägger till i nya
      diagram.
    text: Ta bort den standardplatshållarserien som Aspose.Words lägger till i nya
      diagram.
  - name: Lägg till en namngiven serie som heter "Demo Series" med de angivna datapunkterna
      till histogramdiagrammet.
    text: Lägg till en namngiven serie som heter "Demo Series" med de angivna datapunkterna
      till histogramdiagrammet.
  - name: Spara dokumentet till en .docx‑fil som innehåller den märkta diagramserien.
    text: Spara dokumentet till en .docx‑fil som innehåller den märkta diagramserien.
  type: HowTo
- questions:
  - answer: '`InsertChart` skapar en standardplatshållarserie; genom att rensa den
      tas den tomma serien bort så att diagrammet bara visar de data du lägger till
      med `Series.Add`.'
    question: Varför måste jag anropa `histogramChart.Series.Clear()` innan jag lägger
      till min egen serie?
  - answer: Ja, anropa `histogramChart.Series.Add` flera gånger, varje gång med ett
      unikt namn och `double[]`‑värden; varje serie kommer att listas i diagrammets
      legend med det angivna namnet.
    question: Kan jag lägga till mer än en serie med samma overload, och kommer varje
      serie att visas med sin egen etikett?
  - answer: Overloaden förväntar sig en `double[]`; om du har `int[]` eller andra
      numeriska arrayer, kasta eller konvertera dem till `double[]` innan du skickar
      dem.
    question: Är `double[]`‑argumentet den enda typen som accepteras för datapunkterna?
  - answer: Strängen som skickas som första argument (t.ex. "Demo Series") används
      som serietitel och visas som standard i diagrammets legend.
    question: Kommer serienamnet jag anger att visas i diagrammet automatiskt?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Lägg till en namngiven serie i ett Word‑histogramdiagram
og_description: Märk snabbt en diagramserie i Word med Aspose.Words och se den renderas omedelbart.
og_image_alt: Skärmbild som visar ett Word‑dokument med ett histogramdiagram som innehåller en märkt dataserie skapad med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till en namngiven dataserie i ett histogramdiagram i Word med Aspose.Words för .NET
Den här handledningen visar hur du skapar ett Word‑dokument med Aspose.Words för .NET, infogar ett histogramdiagram och lägger till en märkt dataserie med hjälp av overloaden ChartSeriesCollection.Add som accepterar ett namn och värden. Genom att namnge serien kan du tydligt identifiera varje dataset i diagrammet, vilket gör den visuella utskriften lättare att läsa och tolka.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: Varför måste jag anropa `histogramChart.Series.Clear()` innan jag lägger till min egen serie?**  
A: `InsertChart` skapar en standardplatshållarserie; genom att rensa den tas den tomma serien bort så att diagrammet bara visar de data du lägger till med `Series.Add`.

**Q: Kan jag lägga till mer än en serie med samma overload, och kommer varje serie att visas med sin egen etikett?**  
A: Ja, anropa `histogramChart.Series.Add` flera gånger, varje gång med ett unikt namn och `double[]`‑värden; varje serie kommer att listas i diagrammets legend med det angivna namnet.

**Q: Är `double[]`‑argumentet den enda typen som accepteras för datapunkterna?**  
A: Overloaden förväntar sig en `double[]`; om du har `int[]` eller andra numeriska arrayer, kasta eller konvertera dem till `double[]` innan du skickar dem.

**Q: Kommer serienamnet jag anger att visas i diagrammet automatiskt?**  
A: Strängen som skickas som första argument (t.ex. "Demo Series") används som serietitel och visas som standard i diagrammets legend.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}