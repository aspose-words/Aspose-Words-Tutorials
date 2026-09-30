---
category: general
date: 2026-02-13
description: Spara docx som pdf samtidigt som du bevarar flytande former. Lär dig
  hur du konverterar Word till pdf, exporterar former och hanterar kantfall i C#.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: sv
og_description: Spara docx som pdf samtidigt som flytande former bevaras. Den här
  guiden visar hur du konverterar Word till pdf, exporterar former och hanterar vanliga
  fallgropar.
og_title: Spara docx som PDF med Shape Export – Komplett guide
tags:
- Aspose.Words
- C#
- PDF conversion
title: Spara docx som pdf med Shape Export – Komplett guide
url: /sv/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara docx som pdf – Full‑stack‑tutorial (C#)

Har du någonsin behövt **save docx as pdf** och behålla de flytande diagrammen exakt lika? Du är inte ensam. Många utvecklare stöter på problem när Words former försvinner eller blir förvrängda efter konvertering. Den goda nyheten? Med några rader C# kan du instruera biblioteket att behandla varje form som ett block‑nivå‑element, och resultatet blir en trogen PDF‑replik.

I den här guiden går vi igenom hela processen: att ladda en `.docx`‑fil, konfigurera **convert word to pdf**‑alternativen så att former exporteras korrekt, och slutligen skriva PDF‑filen till disk. I slutet kommer du att veta **how to export shapes**, förstå för- och nackdelar med olika exportlägen, och ha ett färdigt kodexempel som du kan lägga in i vilket .NET‑projekt som helst.

> **Vad du får:** ett komplett, körbart exempel, förklaringar till *varför* varje inställning är viktig, tips för kantfall, och idéer för att utöka lösningen (t.ex. hantera bilder, anpassade typsnitt eller lösenordsskyddade PDF‑filer).

---

## Förutsättningar

- .NET 6+ (eller .NET Framework 4.7+). API‑et vi använder fungerar på båda.
- Aspose.Words för .NET (gratis provversion eller licensierad version). Installera via NuGet: `Install-Package Aspose.Words`.
- Ett Word‑dokument (`input.docx`) som innehåller flytande former (textrutor, auto‑former, SmartArt, osv.).
- Visual Studio 2022 eller någon IDE du föredrar.

Inga andra tredjepartsbibliotek krävs.

## Steg‑för‑steg‑implementering

Under varje steg ser du ett kort kodsnutt, en enkel förklaring på engelska, och en notering om **how to export shapes** korrekt.

### ## Steg 1 – Ladda källdokumentet (save docx as pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Varför detta är viktigt:* `Document`‑klassen representerar hela Word‑filen i minnet. Om du hoppar över detta steg finns det inget att konvertera, och de efterföljande PDF‑alternativen har inget att verka på.

### ## Steg 2 – Konfigurera PDF‑sparalternativ (how to export shapes)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Förklaring**

- `PdfSaveOptions` är en “bag of settings” som talar om för Aspose.Words hur man översätter Word‑konstruktioner till PDF.
- Egenskapen **ExportFloatingShapesAsInlineTag** har tre möjliga värden:
  1. **Inline** – former blir inline‑element (ofta klämda in i omgivande text).
  2. **Block** – varje form placeras i sitt eget block, vilket är det säkraste sättet att behålla originalutseendet.
  3. **Auto** – biblioteket bestämmer automatiskt (kan ibland inte välja det bästa alternativet).

Att välja **Block** är den rekommenderade metoden när du *need to export shapes* exakt som de visas i originaldokumentet. Det förhindrar problemet med “shape disappears” som många stöter på när man bara anropar `doc.Save("out.pdf")`.

### ## Steg 3 – Spara dokumentet som PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*Vad du kommer att se:* Efter att den här raden har körts ligger `FloatingShapes.pdf` i `C:\MyFolder`. Öppna den, och du bör se varje textruta, anrop och SmartArt placerade precis som i käll‑`.docx`.

---

## Fullt fungerande exempel

Nedan är **complete program** som du kan kompilera och köra som en konsolapp. Den innehåller alla nödvändiga `using`‑satser och kommentarer för tydlighet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Förväntad output**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Öppna den resulterande PDF‑filen och verifiera att alla former behåller sina ursprungliga positioner. Om någon form fortfarande ser felaktig ut, dubbelkolla att den verkligen är en *floating* form (jämfört med en inline‑bild) i Word.

---

## Vanliga frågor & kantfall

| Question | Answer |
|----------|--------|
| **Kan jag exportera former som inline istället för block?** | Ja – sätt `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline`. Detta kan vara användbart för enkla layouter, men förvänta dig tätare textflöde och eventuell överlappning. |
| **Vad händer om mitt dokument innehåller bilder i former?** | Samma alternativ fungerar; Aspose.Words rasteriserar formen tillsammans med dess bild. För högsta noggrannhet, aktivera även `PdfSaveOptions.JpegQuality` om du behöver bättre bildkomprimering. |
| **Fungerar detta med lösenordsskyddade DOCX‑filer?** | Läs in dokumentet med ett `LoadOptions`‑objekt som anger lösenordet, fortsätt sedan som vanligt. |
| **Kan jag konvertera flera DOCX‑filer i ett batch?** | Packa in den tre‑stegs‑logiken i en `foreach`‑loop över en fillista. Kom ihåg att återanvända `PdfSaveOptions` för prestanda. |
| **Är PDF‑filen kompatibel med äldre läsare (Acrobat 7)?** | Som standard skapar Aspose.Words PDF 1.7‑filer. Sätt `pdfOptions.Compliance = PdfCompliance.PdfA1b` för arkiv‑grade PDF‑filer som fungerar på äldre läsare. |

---

## Pro‑tips & vanliga fallgropar

- **Pro tip:** Om du märker små vertikala förskjutningar efter konvertering, prova att sätta `pdfOptions.UsePdfDocumentStructure = true`. Detta tvingar PDF‑motorn att respektera Word‑layoutens hierarki.
- **Var uppmärksam på:** Dokument som blandar flytande former med förankrade tabeller. I vissa fall kan block‑exporten skjuta en tabell till en ny sida; du kan mildra detta genom att justera `pdfOptions.PageSetup` innan du sparar.
- **Prestanda‑notering:** Att återanvända en enda `PdfSaveOptions`‑instans för många filer minskar GC‑trycket och snabbar upp batch‑konverteringar.

## Visuell referens

Nedan är en schematisk skärmdump (platshållare) som visar före/efter av ett dokument med en flytande textruta.

![save docx as pdf example with floating shapes](image-placeholder.png "save docx as pdf example with floating shapes")

*Bilden illustrerar hur formen förblir exakt där den var i original‑Word‑filen efter konvertering.*

## Sammanfattning

Vi har gått igenom **how to save docx as pdf** samtidigt som vi behåller varje flytande form intakt, utforskat **convert word to pdf**‑inställningarna som är viktiga, och besvarat de vanligaste “**how to export shapes**”‑frågorna. Det kompletta kodexemplet är redo att läggas in i vilket C#‑projekt som helst, och de valfria justeringarna ger dig flexibilitet för verkliga scenarier som batch‑behandling eller PDF/A‑kompatibilitet.

### Nästa steg

- Prova **convert word document pdf** med olika efterlevnadsnivåer (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) för att uppfylla regulatoriska krav.
- Experimentera med **how to convert docx pdf** för lösenordsskyddade filer — lägg till `LoadOptions` med ett lösenord och `PdfSaveOptions` med `EncryptionDetails`.
- Utforska andra utdataformat (t.ex. XPS, HTML) med samma `Document`‑objekt; den enda förändringen är `Save`‑metodens formatargument.

Har du fler frågor? Lämna en kommentar, och lycka till med kodningen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}