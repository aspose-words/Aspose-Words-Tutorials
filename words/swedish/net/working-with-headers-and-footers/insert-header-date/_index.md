---
title: Infoga dynamiskt datum i sidhuvud i Word-dokument med Aspose.Words för .NET
weight: 110
limit:
description: Lär dig hur du lägger till ett dynamiskt DATE-fält i ett Word-dokuments primära sidhuvud med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Lär dig hur du lägger till ett dynamiskt DATE-fält i ett Word-dokuments
    primära sidhuvud med Aspose.Words för .NET.
  headline: Infoga dynamiskt datum i sidhuvud i Word-dokument med Aspose.Words för
    .NET
  type: TechArticle
- description: Lär dig hur du lägger till ett dynamiskt DATE-fält i ett Word-dokuments
    primära sidhuvud med Aspose.Words för .NET.
  name: Infoga dynamiskt datum i sidhuvud i Word-dokument med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt Document och en DocumentBuilder för att redigera det.
    text: Skapa ett nytt Document och en DocumentBuilder för att redigera det.
  - name: Flytta builderns markör till det primära sidhuvudet så att efterföljande
      insättningar påverkar sidhuvudet.
    text: Flytta builderns markör till det primära sidhuvudet så att efterföljande
      insättningar påverkar sidhuvudet.
  - name: Skriv den statiska etiketten och infoga ett DATE-fält formaterat som “MMMM
      d, yyyy” i sidhuvudet, vilket skapar ett dynamiskt datum.
    text: Skriv den statiska etiketten och infoga ett DATE-fält formaterat som “MMMM
      d, yyyy” i sidhuvudet, vilket skapar ett dynamiskt datum.
  - name: Återgå till huvudtexten och lägg till ett exempelparagraf, som visar normalt
      dokumentinnehåll tillsammans med sidhuvudet.
    text: Återgå till huvudtexten och lägg till ett exempelparagraf, som visar normalt
      dokumentinnehåll tillsammans med sidhuvudet.
  - name: Spara dokumentet som en .docx-fil.
    text: Spara dokumentet som en .docx-fil.
  type: HowTo
- questions:
  - answer: '`MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)`‑anropet placerar
      buildern i det befintliga primära sidhuvudet, och `Write`/`InsertField` lägger
      helt enkelt till text till det som redan finns där; de raderar inte befintligt
      innehåll.'
    question: Vad händer om dokumentet redan har ett primärt sidhuvud – kommer min
      kod att skriva över det?
  - answer: Ja – ändra switch‑formatet i fältkoden som skickas till `InsertField`,
      t.ex. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\"")` kommer att producera
      ett datum som 2026‑09‑22.
    question: Kan jag ändra datumformatet som DATE-fältet använder, och i så fall
      hur?
  - answer: Byt ut `HeaderFooterType.HeaderPrimary` mot `HeaderFooterType.HeaderFirst`
      när du anropar `MoveToHeaderFooter`; resten av koden fungerar på samma sätt.
    question: Om jag behöver datumfältet i första sidans sidhuvud istället för det
      primära sidhuvudet, vad ska jag göra?
  - answer: Fältet infogas endast med `\\@`‑switchen, vilket instruerar Word att visa
      aktuellt datum varje gång fältet uppdateras (t.ex. vid öppning av filen eller
      när du trycker på Ctrl+Alt+F9).
    question: Uppdateras DATE-fältet automatiskt när dokumentet öppnas senare?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Lägg till ett dynamiskt datum i ett Word‑sidhuvud
og_description: Steg‑för‑steg‑guide för att bädda in ett levande datumfält i ditt Word‑sidhuvud med Aspose.Words.
og_image_alt: Skärmbild som visar hur man infogar ett dynamiskt DATE-fält i ett Word-dokuments sidhuvud med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga dynamiskt datum i sidhuvud i Word-dokument med Aspose.Words för .NET
Den här handledningen visar hur man använder klasserna Document och DocumentBuilder i Aspose.Words för .NET för att infoga ett dynamiskt DATE-fält i det primära sidhuvudet i ett Word-dokument. Det tillagda fältet uppdateras automatiskt till aktuellt datum varje gång dokumentet öppnas, vilket säkerställer att ditt sidhuvud alltid visar det senaste datumet. Följ den steg‑för‑steg‑kod som läggs till fältet och spara den uppdaterade filen.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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

**Q: Vad händer om dokumentet redan har ett primärt sidhuvud – kommer min kod att skriva över det?**  
A: `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)`‑anropet placerar buildern i det befintliga primära sidhuvudet, och `Write`/`InsertField` lägger helt enkelt till text till det som redan finns där; de raderar inte befintligt innehåll.

**Q: Kan jag ändra datumformatet som DATE-fältet använder, och i så fall hur?**  
A: Ja – ändra switch‑formatet i fältkoden som skickas till `InsertField`, t.ex. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\"")` kommer att producera ett datum som 2026‑09‑22.

**Q: Om jag behöver datumfältet i första sidans sidhuvud istället för det primära sidhuvudet, vad ska jag göra?**  
A: Byt ut `HeaderFooterType.HeaderPrimary` mot `HeaderFooterType.HeaderFirst` när du anropar `MoveToHeaderFooter`; resten av koden fungerar på samma sätt.

**Q: Uppdateras DATE-fältet automatiskt när dokumentet öppnas senare?**  
A: Fältet infogas endast med `\\@`‑switchen, vilket instruerar Word att visa aktuellt datum varje gång fältet uppdateras (t.ex. vid öppning av filen eller när du trycker på Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}