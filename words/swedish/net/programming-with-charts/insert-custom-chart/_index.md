---
title: Infoga anpassat stapeldiagram i Word‑dokument med Aspose.Words for .NET
weight: 310
limit:
description: Skapa en Word‑fil, infoga ett stapeldiagram, ersätt dess data med en anpassad matris, lägg till en titel och spara—allt med Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Skapa en Word‑fil, infoga ett stapeldiagram, ersätt dess data med en
    anpassad matris, lägg till en titel och spara—allt med Aspose.Words for .NET.
  headline: Infoga anpassat stapeldiagram i Word‑dokument med Aspose.Words for .NET
  type: TechArticle
- description: Skapa en Word‑fil, infoga ett stapeldiagram, ersätt dess data med en
    anpassad matris, lägg till en titel och spara—allt med Aspose.Words for .NET.
  name: Infoga anpassat stapeldiagram i Word‑dokument med Aspose.Words for .NET
  steps:
  - name: Skapa ett nytt Document och en DocumentBuilder som är kopplad till det.
    text: Skapa ett nytt Document och en DocumentBuilder som är kopplad till det.
  - name: Infoga ett stapeldiagram med storleken 432×252 punkter i dokumentet och
      hämta dess Chart‑objekt.
    text: Infoga ett stapeldiagram med storleken 432×252 punkter i dokumentet och
      hämta dess Chart‑objekt.
  - name: Ta bort den automatiskt genererade exempelserien från diagrammet.
    text: Ta bort den automatiskt genererade exempelserien från diagrammet.
  - name: Definiera X‑axelns kategorietiketter och legendposterna för varje serie.
    text: Definiera X‑axelns kategorietiketter och legendposterna för varje serie.
  - name: Skapa en tvådimensionell matris där varje rad innehåller värdena för en
      serie.
    text: Skapa en tvådimensionell matris där varje rad innehåller värdena för en
      serie.
  - name: Iterera över varje serie, extrahera radvärdena från matrisen och lägg till
      serien i diagrammet med motsvarande legendpost och X‑axelns etiketter.
    text: Iterera över varje serie, extrahera radvärdena från matrisen och lägg till
      serien i diagrammet med motsvarande legendpost och X‑axelns etiketter.
  - name: Ställ in diagramtitelns text till 'Half‑Yearly Revenue' och gör den synlig.
    text: Ställ in diagramtitelns text till 'Half‑Yearly Revenue' och gör den synlig.
  - name: Spara dokumentet som innehåller det anpassade diagrammet till en .docx‑fil.
    text: Spara dokumentet som innehåller det anpassade diagrammet till en .docx‑fil.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` förväntar sig att värdearrayens längd är lika med
      antalet X‑axel‑etiketter, och du måste lägga till exakt en serie per **legendpost**;
      en mismatch kommer att kasta ett `ArgumentException` vid körning.'
    question: Vad händer om raderna eller kolumnerna i `dataMatrix` inte matchar längderna
      på `legendEntries` eller `xLabels`?
  - answer: Ja—byt ut `ChartType.Column` i `docBuilder.InsertChart` mot någon annan
      `ChartType` (t.ex. `ChartType.Line`) så kommer de efterföljande `Series.Add`‑anropen
      att fylla det nya diagrammet på samma sätt.
    question: Kan jag använda en annan diagramtyp, till exempel ett linjediagram,
      med samma data‑populeringslogik?
  - answer: Justera `Width`‑ och `Height`‑egenskaperna på den `Shape` som returneras
      av `InsertChart` (t.ex. `chartContainer.Width = 500; chartContainer.Height =
      300;`).
    question: Hur ändrar jag storleken på diagrammet efter att det har infogats?
  - answer: Ställ in `chartObj.Series[i].HasDataLabel = true;` för varje serie efter
      att den lagts till, eller loopa igenom `chartObj.Series` och aktivera `HasDataLabel`
      för att visa värdena i diagrammet.
    question: Finns det ett snabbt sätt att visa datalabels på varje stapel i diagrammet?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Lägg till ett anpassat stapeldiagram i ett Word‑dokument
og_description: Byt ut ett diagrams standarddata mot din egen matris och sätt en titel på några sekunder.
og_image_alt: Skärmbild som visar ett Word‑dokument med ett anpassat stapeldiagram skapat med Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga anpassat stapeldiagram i Word‑dokument med Aspose.Words
Denna handledning guidar dig genom att skapa ett Word‑dokument, infoga ett stapeldiagram, rensa dess standarddata och fylla diagrammet med anpassade värden från en tvådimensionell matris—där varje rad motsvarar en serie och varje kolumn en kategori. Du får också se hur du lägger till en diagramtitel innan du sparar filen. Följ stegen för att skapa ett helt anpassat diagram direkt i ditt Word‑dokument.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Vad händer om raderna eller kolumnerna i `dataMatrix` inte matchar längderna på `legendEntries` eller `xLabels`?**  
A: `Chart.Series.Add` förväntar sig att värdearrayens längd är lika med antalet X‑axel‑etiketter, och du måste lägga till exakt en serie per **legendpost**; en mismatch kommer att kasta ett `ArgumentException` vid körning.

**Q: Kan jag använda en annan diagramtyp, till exempel ett linjediagram, med samma data‑populeringslogik?**  
A: Ja—byt ut `ChartType.Column` i `docBuilder.InsertChart` mot någon annan `ChartType` (t.ex. `ChartType.Line`) så kommer de efterföljande `Series.Add`‑anropen att fylla det nya diagrammet på samma sätt.

**Q: Hur ändrar jag storleken på diagrammet efter att det har infogats?**  
A: Justera `Width`‑ och `Height`‑egenskaperna på den `Shape` som returneras av `InsertChart` (t.ex. `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Finns det ett snabbt sätt att visa datalabels på varje stapel i diagrammet?**  
A: Ställ in `chartObj.Series[i].HasDataLabel = true;` för varje serie efter att den lagts till, eller loopa igenom `chartObj.Series` och aktivera `HasDataLabel` för att visa värdena i diagrammet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}