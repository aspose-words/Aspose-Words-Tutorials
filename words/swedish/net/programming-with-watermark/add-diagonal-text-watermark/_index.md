---
title: Skapa ett diagonalt textvattenmärke med anpassat teckensnitt i ett Word-dokument med Aspose.Words för .NET
weight: 210
limit:
description: Steg‑för‑steg‑kod för att lägga till ett diagonalt textvattenmärke med anpassat teckensnitt i en Word .docx med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Steg‑för‑steg‑kod för att lägga till ett diagonalt textvattenmärke
    med anpassat teckensnitt i en Word .docx med Aspose.Words för .NET.
  headline: Skapa ett diagonalt textvattenmärke med anpassat teckensnitt i ett Word-dokument
    med Aspose.Words för .NET
  type: TechArticle
- description: Steg‑för‑steg‑kod för att lägga till ett diagonalt textvattenmärke
    med anpassat teckensnitt i en Word .docx med Aspose.Words för .NET.
  name: Skapa ett diagonalt textvattenmärke med anpassat teckensnitt i ett Word-dokument
    med Aspose.Words för .NET
  steps:
  - name: Skapa en ny tom Word-dokumentinstans med namnet `document`.
    text: Skapa en ny tom Word-dokumentinstans med namnet `document`.
  - name: Konfigurera `watermarkSettings` med Arial 48‑pt grått teckensnitt, diagonal
      layout och opak rendering.
    text: Konfigurera `watermarkSettings` med Arial 48‑pt grått teckensnitt, diagonal
      layout och opak rendering.
  - name: Applicera textvattenmärket "Private" på `document` med de tidigare definierade
      inställningarna.
    text: Applicera textvattenmärket "Private" på `document` med de tidigare definierade
      inställningarna.
  - name: Definiera filsökvägen där det vattenmärkta dokumentet ska sparas.
    text: Definiera filsökvägen där det vattenmärkta dokumentet ska sparas.
  - name: Spara det modifierade `document` till den angivna sökvägen som en .docx-fil.
    text: Spara det modifierade `document` till den angivna sökvägen som en .docx-fil.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` bestämmer om vattenmärket renderas med partiell opacitet;
      sätts den till `false` blir vattenmärket helt opakt, medan `true` applicerar
      en standard halvgenomskinlig effekt.'
    question: Vad styr flaggan **IsSemitrasparent** i `TextWatermarkOptions`?
  - answer: Ja—sätt `Layout`‑egenskapen till `WatermarkLayout.Horizontal` (eller ett
      annat enum‑värde) innan du anropar `document.Watermark.SetText`.
    question: Kan jag ändra vattenmärkesorienteringen till horisontell istället för
      diagonal?
  - answer: Word kommer att falla tillbaka på sitt standardteckensnitt för vattenmärket,
      så texten visas fortfarande men kan se annorlunda ut än den avsedda stilen.
    question: Vad händer om den angivna `FontFamily` (t.ex. "Arial") inte är installerad
      på målmaskinen?
  - answer: Läs in den befintliga filen med `Document document = new Document("Existing.docx");`
      och konfigurera sedan `TextWatermarkOptions` och anropa `document.Watermark.SetText`
      som visas.
    question: Är det möjligt att lägga till ett vattenmärke i en befintlig `.docx`-fil
      istället för att skapa en ny?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Lägg till ett diagonalt textvattenmärke med anpassat teckensnitt
og_description: Lär dig att bädda in ett snett textvattenmärke med ditt eget teckensnitt i en Word-fil på några minuter.
og_image_alt: Guide som visar hur man lägger till ett diagonalt textvattenmärke med anpassat teckensnitt i ett Word-dokument med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett diagonalt textvattenmärke med anpassat teckensnitt i ett Word-dokument med Aspose.Words för .NET
Denna handledning guidar dig genom att skapa ett nytt Word-dokument, konfigurera ett diagonalt textvattenmärke med dina valda teckensnittinställningar, applicera det via Document.Watermark.SetText API och spara resultatet som en .docx-fil. I slutet har du ett professionellt vattenmärkt dokument som visar ditt varumärke eller ägandeskap. Steg‑för‑steg‑koden är klar att kopieras in i vilket .NET‑projekt som helst.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Vad styr flaggan **IsSemitrasparent** i `TextWatermarkOptions`?**  
A: `IsSemitrasparent` bestämmer om vattenmärket renderas med partiell opacitet; sätts den till `false` blir vattenmärket helt opakt, medan `true` applicerar en standard halvgenomskinlig effekt.

**Q: Kan jag ändra vattenmärkesorienteringen till horisontell istället för diagonal?**  
A: Ja—sätt `Layout`‑egenskapen till `WatermarkLayout.Horizontal` (eller ett annat enum‑värde) innan du anropar `document.Watermark.SetText`.

**Q: Vad händer om den angivna `FontFamily` (t.ex. "Arial") inte är installerad på målmaskinen?**  
A: Word kommer att falla tillbaka på sitt standardteckensnitt för vattenmärket, så texten visas fortfarande men kan se annorlunda ut än den avsedda stilen.

**Q: Är det möjligt att lägga till ett vattenmärke i en befintlig `.docx`-fil istället för att skapa en ny?**  
A: Läs in den befintliga filen med `Document document = new Document("Existing.docx");` och konfigurera sedan `TextWatermarkOptions` och anropa `document.Watermark.SetText` som visas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}