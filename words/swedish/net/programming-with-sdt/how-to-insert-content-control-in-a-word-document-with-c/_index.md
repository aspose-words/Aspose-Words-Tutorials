---
category: general
date: 2026-09-08
description: Lär dig hur du infogar innehållskontroll i ett Word‑dokument med C# och
  Aspose.Words. Inkluderar steg för att skapa innehållskontroll, sätta platshållare
  och spara filen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: sv
lastmod: 2026-09-08
og_description: Infoga innehållskontroll i en Word‑fil med C# och Aspose.Words. Följ
  den här guiden för att skapa innehållskontroll, ange platshållartext och spara dokumentet.
og_image_alt: Insert content control example in a Word document
og_title: Infoga innehållskontroll i Word med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Hur man infogar innehållskontroll i ett Word‑dokument med C#
url: /sv/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar innehållskontroll i ett Word-dokument med C#

Om du behöver **infoga innehållskontroll** i ett Word-dokument, visar den här guiden en komplett, körbar lösning. Du kommer också att lära dig hur du **skapar innehållskontroll** programatiskt, sätter platshållartext och skriver filen till disk.

Innehållskontroller låter dig definiera områden som användare kan fylla i, upprepa eller låsa. De används ofta för mallar, formulär och dynamiska rapporter. Stegen nedan använder Aspose.Words för .NET-biblioteket, som fungerar med .NET 6+, .NET Framework 4.6+ och .NET Core.

## Hur man infogar innehållskontroll i ett Word-dokument

1. **Lägg till Aspose.Words i ditt projekt**  
   Öppna en terminal i projektmappen och kör:

   ```bash
   dotnet add package Aspose.Words
   ```

   Paketet innehåller klasserna `Document`, `DocumentBuilder` och `StructuredDocumentTag` som behövs för innehållskontroller.

2. **Skapa ett nytt tomt dokument**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   `Document`-objektet representerar hela .docx-filen, medan `DocumentBuilder` ger en bekväm markör för att infoga noder.

## Skapa en innehållskontroll med Aspose.Words

Innehållskontroller representeras av klassen `StructuredDocumentTag` (SDT). Följande kod skapar en **plain‑text**-innehållskontroll och ger den en titel som du kan fråga efter senare.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Varför detta är viktigt:*  
- `SdtType.PlainText` säkerställer att kontrollen bara accepterar vanliga tecken.  
- `MarkupLevel.Block` får kontrollen att bete sig som ett helt stycke, vilket är idealiskt för formulärfält.  
- `Title`-egenskapen är en stabil identifierare som du kan använda vid sökning eller bindning av data.

## Ställa in platshållare och standardtext

En platshållare guidar användaren innan de skriver något. Du kan också förifylla kontrollen med standardinnehåll.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

XML-fragmentet måste matcha kontrollens datatyp. För plain‑text‑kontroller krävs `<text>`-elementet. Om du utelämnar detta steg visas den tidigare definierade platshållaren istället.

## Infoga innehållskontrollen på önskad plats

`DocumentBuilder`-markören bestämmer var kontrollen visas. Som standard är markören i början av dokumentet.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Om du behöver kontrollen i en tabell, sidhuvud eller efter befintliga stycken, flytta först byggaren:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Spara dokumentet med den infogade innehållskontrollen

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

Filen `SDT.docx` innehåller nu en plain‑text‑innehållskontroll med titeln **CustomerName** och platshållaren “Enter name here” samt standardtexten “John Doe”.

![Exempel på infogad innehållskontroll i ett Word-dokument](insert-content-control.png)

*Bildtext:* Exempel på infogad innehållskontroll i ett Word-dokument

### Förväntat resultat

När du öppnar `SDT.docx` i Microsoft Word:

- En grå platshållare “Enter name here” visas om du tar bort standardtexten.  
- Kontrollen markeras när du klickar i den, vilket indikerar att den kan redigeras.  
- **Developer**-fliken (om den är aktiverad) visar kontrollens titel **CustomerName** i egenskapspanelen.

## Fullt fungerande exempel

Nedan är ett enda, självständigt program som du kan kopiera, kompilera och köra. Det demonstrerar varje steg från projektuppsättning till att spara filen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kör programmet med `dotnet run`. Efter körning, öppna den genererade filen för att verifiera att innehållskontrollen visas som beskrivet.

## Praktiska tips och vanliga fallgropar

| Situation | Rekommenderad metod |
|-----------|----------------------|
| **Flera kontroller av samma typ** | Ge varje kontroll en unik `Title`. Du kan senare hämta en kontroll med `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Kontrollen syns inte i Word** | Se till att du sparade dokumentet med filändelsen `.docx` och att `Aspose.Words`-versionen är kompatibel med din Office-version. |
| **Behöver en rich‑text‑kontroll** | Använd `SdtType.RichText` istället för `PlainText`. XML-fragmentet använder då `<w:richText>`-element. |
| **Placera kontrollen i en tabellcell** | Flytta byggaren till cellen först: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Prestanda med stora dokument** | Skapa `StructuredDocumentTag` en gång och återanvänd den om du behöver många identiska kontroller; klona den via `sdt.Clone(true)`. |

## Nästa steg

- **Skapa repeterande innehållskontroller** (`SdtType.RepeatingSection`) för tabeller som växer dynamiskt.  
- **Bind innehållskontroller till XML-data** med `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Lås kontrollen** (`sdt.LockContentControl = true`) för att förhindra användarredigeringar samtidigt som programmatisk uppdatering tillåts.  

Att utforska dessa ämnen kommer att fördjupa din förmåga att bygga robusta Word-mallar med Aspose.Words.

---

**Slutsats**  
Du vet nu hur du **infogar innehållskontroll** i ett Word-dokument med C#. Handledningen täckte att skapa kontrollen, sätta platshållare och standardtext, infoga den på önskad plats och spara den slutliga filen. Med denna grund kan du bygga avancerade formulär, kopplade mallar och automatiserade rapporter som utnyttjar Words inbyggda innehållskontrollfunktioner.

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Ställ in stil för innehållskontroll](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Ställ in färg för innehållskontroll](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}