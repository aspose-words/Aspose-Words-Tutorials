---
title: Infoga exempel på kolumndiagram i Word-dokument med Aspose.Words for .NET
weight: 410
limit:
description: Steg‑för‑steg‑guide för att skapa en Word‑fil, infoga ett standardkolumndiagram med DocumentBuilder.InsertChart, komma åt diagramobjektet och spara som .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Steg‑för‑steg‑guide för att skapa en Word‑fil, infoga ett standardkolumndiagram
    med DocumentBuilder.InsertChart, komma åt diagramobjektet och spara som .docx.
  headline: Infoga exempel på kolumndiagram i Word-dokument med Aspose.Words for .NET
  type: TechArticle
- description: Steg‑för‑steg‑guide för att skapa en Word‑fil, infoga ett standardkolumndiagram
    med DocumentBuilder.InsertChart, komma åt diagramobjektet och spara som .docx.
  name: Infoga exempel på kolumndiagram i Word-dokument med Aspose.Words for .NET
  steps:
  - name: Skapa ett tomt Word-dokument och en DocumentBuilder för att redigera det.
    text: Skapa ett tomt Word-dokument och en DocumentBuilder för att redigera det.
  - name: Infoga ett kolumndiagram med storleken 432 × 252 punkter i dokumentet.
    text: Infoga ett kolumndiagram med storleken 432 × 252 punkter i dokumentet.
  - name: Hämta Chart-objektet från den infogade formen för ytterligare anpassning
      om så behövs.
    text: Hämta Chart-objektet från den infogade formen för ytterligare anpassning
      om så behövs.
  - name: Spara dokumentet, som nu innehåller det infogade kolumndiagrammet, som en
      .docx-fil.
    text: Spara dokumentet, som nu innehåller det infogade kolumndiagrammet, som en
      .docx-fil.
  type: HowTo
- questions:
  - answer: Dimensionerna anges i punkter (1 punkt = 1/72 tum), så 432 pt ≈ 6 tum
      och 252 pt ≈ 3,5 tum.
    question: Vilka enheter används för bredd‑ och höjdpunkterna (432, 252) i InsertChart?
  - answer: Ja—efter infogandet har du Chart‑objektet via `chartContainer.Chart`;
      du kan ändra dess SeriesCollection, Categories och Values för att ersätta exempeldata.
    question: Kan jag ändra diagramdata efter att ha anropat InsertChart med standarddatamängden?
  - answer: Byt helt enkelt ut `ChartType.Column` mot ett annat enum‑värde, till exempel
      `ChartType.Line`, i anropet till `InsertChart`.
    question: Är det möjligt att infoga en annan diagramtyp (t.ex. ett linjediagram)
      med samma kod?
  - answer: Nej—`docBuilder.InsertChart` bäddar automatiskt in diagrammet i en `Shape`;
      när du anropar `wordDoc.Save` skrivs diagrammet med dokumentet.
    question: Behöver jag anropa någon extra metod för att bädda in diagrammet innan
      dokumentet sparas?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Infoga ett exempel på kolumndiagram i ett Word‑dokument
og_description: Lägg till ett färdigt kolumndiagram i ett Word-dokument med Aspose.Words for .NET på några minuter.
og_image_alt: Skärmbild som visar ett Word-dokument med ett exempel på kolumndiagram infogat med Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga exempel på kolumndiagram i Word-dokument med Aspose.Words
Den här handledningen guidar dig genom att skapa ett nytt Word-dokument och infoga ett standardkolumndiagram med DocumentBuilder.InsertChart. Du får också se hur du hämtar det inbäddade Chart-objektet för vidare manipulation. Slutligen visar guiden hur du sparar dokumentet som en .docx-fil.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: Vilka enheter används för bredd‑ och höjdpunkterna (432, 252) i InsertChart?**  
A: Dimensionerna anges i punkter (1 punkt = 1/72 tum), så 432 pt ≈ 6 tum och 252 pt ≈ 3,5 tum.

**Q: Kan jag ändra diagramdata efter att ha anropat InsertChart med standarddatamängden?**  
A: Ja—efter infogandet har du Chart‑objektet via `chartContainer.Chart`; du kan ändra dess SeriesCollection, Categories och Values för att ersätta exempeldata.

**Q: Är det möjligt att infoga en annan diagramtyp (t.ex. ett linjediagram) med samma kod?**  
A: Byt helt enkelt ut `ChartType.Column` mot ett annat enum‑värde, till exempel `ChartType.Line`, i anropet till `InsertChart`.

**Q: Behöver jag anropa någon extra metod för att bädda in diagrammet innan dokumentet sparas?**  
A: Nej—`docBuilder.InsertChart` bäddar automatiskt in diagrammet i en `Shape`; när du anropar `wordDoc.Save` skrivs diagrammet med dokumentet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}