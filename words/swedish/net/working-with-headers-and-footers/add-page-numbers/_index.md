---
title: Lägg till sidnummer i sidfoten på ett Word‑dokument med Aspose.Words för .NET
weight: 210
limit:
description: Lägg till automatiskt uppdaterande sidnummer i ett Word‑dokumentets primära sidfot med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Lägg till automatiskt uppdaterande sidnummer i ett Word‑dokumentets
    primära sidfot med Aspose.Words för .NET.
  headline: Lägg till sidnummer i sidfoten på ett Word‑dokument med Aspose.Words för
    .NET
  type: TechArticle
- description: Lägg till automatiskt uppdaterande sidnummer i ett Word‑dokumentets
    primära sidfot med Aspose.Words för .NET.
  name: Lägg till sidnummer i sidfoten på ett Word‑dokument med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt Document‑objekt och en DocumentBuilder som är knuten till
      det.
    text: Skapa ett nytt Document‑objekt och en DocumentBuilder som är knuten till
      det.
  - name: Flytta builderns markör till den primära sidfoten i den första sektionen.
    text: Flytta builderns markör till den primära sidfoten i den första sektionen.
  - name: Ställ in styckejusteringen till centrerad så att sidfotstexten blir centrerad.
    text: Ställ in styckejusteringen till centrerad så att sidfotstexten blir centrerad.
  - name: Skriv etiketten "Page " och infoga ett PAGE‑fält som visar det aktuella
      sidnumret.
    text: Skriv etiketten "Page " och infoga ett PAGE‑fält som visar det aktuella
      sidnumret.
  - name: Skriv " of " och infoga ett NUMPAGES‑fält som visar det totala antalet sidor.
    text: Skriv " of " och infoga ett NUMPAGES‑fält som visar det totala antalet sidor.
  - name: Spara dokumentet som en .docx‑fil.
    text: Spara dokumentet som en .docx‑fil.
  type: HowTo
- questions:
  - answer: Nej. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` flyttar buildern
      endast till den primära sidfoten i den *första* sektionen, så fälten infogas
      bara där.
    question: Om dokumentet har mer än en sektion, kommer den här koden att lägga
      till sidnummer i varje sektons sidfot?
  - answer: Ställ in `builder.ParagraphFormat.Alignment` till ett annat `ParagraphAlignment`‑värde
      (t.ex. `ParagraphAlignment.Right`) innan du skriver fälten.
    question: Hur kan jag ändra justeringen av sidnummerstycket i sidfoten?
  - answer: '`InsertField` tar fältkoden och ett valfritt fältresultat; att skicka
      `null` talar om för Aspose.Words att låta Word beräkna resultatet vid körning.'
    question: Vad representerar argumentet `null` i `InsertField("PAGE", null)`?
  - answer: Ja—byt ut `HeaderFooterType.FooterPrimary` mot `HeaderFooterType.HeaderPrimary`
      (eller en annan sidhuvudstyp) innan du infogar fälten.
    question: Kan jag placera samma "Page X of Y"‑fält i sidhuvudet istället för i
      sidfoten?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Infoga automatiska sidnummer i Word‑sidfot
og_description: Steg‑för‑steg‑kod för att lägga till dynamiska sidnummer i en Word‑sidfot med Aspose.Words för .NET.
og_image_alt: Guide som visar hur du lägger till automatiska sidnummer i en Word‑dokumentfot med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till sidnummer i sidfoten på ett Word‑dokument med Aspose.Words för .NET
Denna handledning visar hur du använder Aspose.Words Document och DocumentBuilder för att infoga automatiskt uppdaterande sidnummer i den primära sidfoten i ett Word‑dokument. Genom att lägga till sidnummer programatiskt säkerställer du enhetlig paginering i hela filen utan manuell redigering. Exempelkoden är klar att köras i en .NET‑miljö.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Om dokumentet har mer än en sektion, kommer den här koden att lägga till sidnummer i varje sektons sidfot?**  
A: Nej. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` flyttar buildern endast till den primära sidfoten i den *första* sektionen, så fälten infogas bara där.

**Q: Hur kan jag ändra justeringen av sidnummerstycket i sidfoten?**  
A: Ställ in `builder.ParagraphFormat.Alignment` till ett annat `ParagraphAlignment`‑värde (t.ex. `ParagraphAlignment.Right`) innan du skriver fälten.

**Q: Vad representerar argumentet `null` i `InsertField("PAGE", null)`?**  
A: `InsertField` tar fältkoden och ett valfritt fältresultat; att skicka `null` talar om för Aspose.Words att låta Word beräkna resultatet vid körning.

**Q: Kan jag placera samma "Page X of Y"‑fält i sidhuvudet istället för i sidfoten?**  
A: Ja—byt ut `HeaderFooterType.FooterPrimary` mot `HeaderFooterType.HeaderPrimary` (eller en annan sidhuvudstyp) innan du infogar fälten.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}