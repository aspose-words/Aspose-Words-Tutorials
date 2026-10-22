---
title: Lägg till rött diagonalt textvattenmärke i Word-dokument med Aspose.Words för .NET
weight: 110
limit:
description: Applicera automatiskt ett rött diagonalt textvattenmärke på varje Word-fil som genereras i en batch med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Applicera automatiskt ett rött diagonalt textvattenmärke på varje Word-fil
    som genereras i en batch med Aspose.Words för .NET.
  headline: Lägg till rött diagonalt textvattenmärke i Word-dokument med Aspose.Words
    för .NET
  type: TechArticle
- description: Applicera automatiskt ett rött diagonalt textvattenmärke på varje Word-fil
    som genereras i en batch med Aspose.Words för .NET.
  name: Lägg till rött diagonalt textvattenmärke i Word-dokument med Aspose.Words
    för .NET
  steps:
  - name: Skapa mappen "GeneratedReports" där utdatafilerna kommer att sparas.
    text: Skapa mappen "GeneratedReports" där utdatafilerna kommer att sparas.
  - name: Starta en loop som kommer att generera tre separata dokument.
    text: Starta en loop som kommer att generera tre separata dokument.
  - name: Skapa ett nytt tomt Word-dokumentobjekt.
    text: Skapa ett nytt tomt Word-dokumentobjekt.
  - name: Använd DocumentBuilder för att skriva en titelrad och en beskrivning i dokumentet.
    text: Använd DocumentBuilder för att skriva en titelrad och en beskrivning i dokumentet.
  - name: Definiera utseendet på vattenmärket, inklusive teckensnitt, storlek, färg
      och diagonal layout.
    text: Definiera utseendet på vattenmärket, inklusive teckensnitt, storlek, färg
      och diagonal layout.
  - name: Applicera det konfigurerade röda diagonala vattenmärket med texten "PROTECTED"
      på dokumentet.
    text: Applicera det konfigurerade röda diagonala vattenmärket med texten "PROTECTED"
      på dokumentet.
  - name: Spara det vattenmärkta dokumentet i mappen "GeneratedReports" med ett unikt
      filnamn.
    text: Spara det vattenmärkta dokumentet i mappen "GeneratedReports" med ett unikt
      filnamn.
  - name: Stäng loopen efter att ha bearbetat det aktuella dokumentet.
    text: Stäng loopen efter att ha bearbetat det aktuella dokumentet.
  type: HowTo
- questions:
  - answer: IsSemitrasparent bestämmer om vattenmärket renderas med partiell opacitet;
      att sätta det till **true** gör texten semi‑transparent så att underliggande
      innehåll förblir mer läsbart.
    question: Vad styr alternativet **IsSemitrasparent** och vilken effekt har det
      att sätta det till **true**?
  - answer: Ja—sätt **Layout**-egenskapen till **WatermarkLayout.Horizontal** i **TextWatermarkOptions**
      innan du anropar **document.Watermark.SetText**.
    question: Kan jag ändra vattenmärkesorienteringen till horisontell istället för
      diagonal?
  - answer: Kodsnutten skapar en ny **Document**-instans, men du kan öppna vilken
      befintlig fil som helst (t.ex. `new Document("Existing.docx")`) och sedan anropa
      **document.Watermark.SetText** för att applicera samma vattenmärke.
    question: Kommer den här koden att lägga till ett vattenmärke i en befintlig Word-fil,
      eller bara i nyss skapade dokument?
  - answer: Tilldela en anpassad färg med **Color.FromArgb(red, green, blue)** till
      **Color**-egenskapen i **TextWatermarkOptions**, t.ex. `Color = Color.FromArgb(128,
      0, 128)` för lila.
    question: Hur kan jag använda en anpassad RGB-färg för vattenmärket istället för
      den fördefinierade **Color.Red**?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Lägg till ett rött diagonalt textvattenmärke i Word-dokument
og_description: Se hur du automatiskt applicerar ett rött diagonalt vattenmärke på varje Word-dokument i en batch med Aspose.Words.
og_image_alt: Guide som visar hur du lägger till ett rött diagonalt textvattenmärke i Word-dokument med Aspise.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till rött diagonalt textvattenmärke i Word-dokument med Aspose.Words för .NET
Den här handledningen visar hur du automatiskt inbäddar ett rött diagonalt textvattenmärke i varje Word-dokument som skapas under en batchrapportgenerering. Med hjälp av Aspose.Words för .NETs Document- och DocumentBuilder-klasser appliceras vattenmärket programatiskt när filerna produceras, vilket säkerställer att varje dokument bär samma varumärke eller konfidentialitetsmeddelande utan manuellt arbete.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Vad styr alternativet **IsSemitrasparent** och vilken effekt har det att sätta det till **true**?**  
A: IsSemitrasparent bestämmer om vattenmärket renderas med partiell opacitet; att sätta det till **true** gör texten semi‑transparent så att underliggande innehåll förblir mer läsbart.

**Q: Kan jag ändra vattenmärkesorienteringen till horisontell istället för diagonal?**  
A: Ja—sätt **Layout**-egenskapen till **WatermarkLayout.Horizontal** i **TextWatermarkOptions** innan du anropar **document.Watermark.SetText**.

**Q: Kommer den här koden att lägga till ett vattenmärke i en befintlig Word-fil, eller bara i nyss skapade dokument?**  
A: Kodsnutten skapar en ny **Document**-instans, men du kan öppna vilken befintlig fil som helst (t.ex. `new Document("Existing.docx")`) och sedan anropa **document.Watermark.SetText** för att applicera samma vattenmärke.

**Q: Hur kan jag använda en anpassad RGB-färg för vattenmärket istället för den fördefinierade **Color.Red**?**  
A: Tilldela en anpassad färg med **Color.FromArgb(red, green, blue)** till **Color**-egenskapen i **TextWatermarkOptions**, t.ex. `Color = Color.FromArgb(128, 0, 128)` för lila.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}