---
category: general
date: 2026-07-19
description: Ställ in platshållartext i en StructuredDocumentTag med Aspose.Words.
  Lär dig hur du lägger till kontroll, flyttar till kontroll och sätter taggattribut
  i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- move to control
- how to add control
- how to create sdt
- set tag attribute
language: sv
lastmod: 2026-07-19
og_description: Ställ in platshållartext i en StructuredDocumentTag med Aspose.Words.
  Följ den här steg‑för‑steg‑guiden för att lägga till kontroll, flytta till kontroll
  och ange taggattribut.
og_image_alt: Screenshot showing a Word document with placeholder text inside a content
  control created by Aspose.Words
og_title: Ange platshållartext i Aspose.Words – Snabb C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  headline: Set Placeholder Text in Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  name: Set Placeholder Text in Aspose.Words – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6+ (or .NET Framework 4.7.2) – the code works on any recent runtime.
      - Aspose.Words for .NET (NuGet package `Aspose.Words` version 23.12 or later).
      - A basic understanding of C# and Visual Studio (or your favorite IDE).'
  - name: Expected Result
    text: 'Open `SDTExample.docx` in Microsoft Word:'
  - name: What if I need a **dropdown** instead of plain text?
    text: Replace `SdtType.PlainText` with `SdtType.DropDownList` and populate the
      `ListItems` collection. The rest of the workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—remains
      the same.
  - name: Can I **set the tag attribute** after insertion?
    text: 'Absolutely. The `Tag` property can be modified at any time:'
  - name: How do I **find a control later** in a large document?
    text: Use the `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` method
      and filter by `Tag` or `Title`. This is handy when you need to replace placeholder
      text in bulk.
  - name: What if I want the placeholder to appear in **all languages**?
    text: Aspose.Words supports localized placeholder text via the `PlaceholderName`
      property. Set it to a resource string that varies per culture.
  type: HowTo
tags:
- Aspose.Words
- C#
- ContentControl
title: Ställ in platshållartext i Aspose.Words – Komplett C#‑guide
url: /sv/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in platshållartext i Aspose.Words – Komplett C#-guide

Har du någonsin undrat hur man **ställer in platshållartext** i en Word-innehållskontroll med Aspose.Words? Du är inte ensam. Oavsett om du bygger en dokument‑genereringsmotor eller bara behöver en återanvändbar mall, är det viktigt att veta hur man lägger till kontroll, flyttar till kontroll och sätter tag‑attribut.

I den här handledningen går vi igenom ett verkligt exempel som visar exakt hur man skapar en SDT (StructuredDocumentTag), ger den en tag, ställer in platshållartext och skriver standardinnehåll – allt i ren C#. När du är klar har du ett färdigt kodexempel som du kan klistra in i vilket .NET‑projekt som helst.

## Vad du kommer att lära dig

- Hur man **skapar SDT** (StructuredDocumentTag) programatiskt.
- Det korrekta sättet att **ställa in platshållartext** så att användare ser hjälpsamma tips.
- Använda **move to control** för att placera markören i den nyss tillagda kontrollen.
- Tilldela ett **tag attribute** för senare identifiering.
- Spara dokumentet och verifiera resultatet.

### Förutsättningar

- .NET 6+ (eller .NET Framework 4.7.2) – koden fungerar på alla moderna runtime‑miljöer.
- Aspose.Words för .NET (NuGet‑paketet `Aspose.Words` version 23.12 eller senare).
- Grundläggande förståelse för C# och Visual Studio (eller din föredragna IDE).

Inga andra externa bibliotek krävs.

## Steg 1: Initiera dokumentet och byggaren

Först och främst – skapa ett tomt `Document` och en `DocumentBuilder`. Byggaren är din pensel; dokumentet är duken.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Create a brand‑new blank document.
Document document = new Document();

// DocumentBuilder lets us insert text, tables, and controls.
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

> **Varför detta är viktigt:** Att börja med ett rent `Document` garanterar att platshållaren vi sätter senare inte krockar med befintligt innehåll.

## Steg 2: Skapa StructuredDocumentTag (SDT)

Nu kommer vi att **hur man skapar sdt** – en innehållskontroll som kan hålla vanlig text, datum, rullgardinsmenyer osv. I det här fallet behöver vi en plain‑text‑kontroll.

```csharp
// Create a plain‑text StructuredDocumentTag (content control).
StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
    document, SdtType.PlainText, true);

// Give the control a friendly name and a tag for later lookup.
plainTextSdt.Title = "CustomerName";
plainTextSdt.Tag   = "CustomerNameTag";

// Here’s the crucial part: set the placeholder text that the user sees.
plainTextSdt.PlaceholderText = "Enter name here";
```

> **Proffstips:** `PlaceholderText`‑egenskapen är vad användaren ser innan de skriver något. Den skiljer sig från standardtext som du eventuellt skriver senare.

## Steg 3: Infoga kontrollen i dokumentet

Med SDT:n klar måste vi **hur man lägger till kontroll** i dokumentet. Metoden `InsertNode` gör exakt det.

```csharp
// Insert the content control at the current cursor position.
docBuilder.InsertNode(plainTextSdt);
```

> **Vad händer under huven?** `InsertNode` placerar SDT:n som ett barn till det aktuella stycket och bevarar eventuell omgivande formatering.

## Steg 4: Flytta till kontrollen och skriv standardinnehåll (valfritt)

Om du vill förfylla kontrollen med ett värde (t.ex. ett standardkundnamn) måste du först **move to control** och sedan skriva.

```csharp
// Optionally clear the placeholder and write a default name.
plainTextSdt.RemoveAllChildren();          // Remove the placeholder node.
docBuilder.MoveTo(plainTextSdt);           // Move cursor inside the SDT.
docBuilder.Write("John Doe");              // Write default text.
```

> **Varför vi tar bort platshållaren:** Platshållaren är en visuell ledtråd, inte faktiskt dokumentinnehåll. Att ta bort den innan du skriver säkerställer att det slutgiltiga dokumentet bara innehåller den riktiga texten.

## Steg 5: Spara dokumentet

Till sist sparar du filen till disk. Du kan också strömma den som svar i en webbapp – byt bara ut `Save`‑anropet.

```csharp
// Save the Word document to the desired location.
document.Save("C:/Temp/SDTExample.docx");
```

### Förväntat resultat

Öppna `SDTExample.docx` i Microsoft Word:

- Du kommer att se en plain‑text‑innehållskontroll med titeln **CustomerName**.
- Kontrollens platshållartext visar “Enter name here” som en blek indikation (om du inte skrev standardinnehåll).
- Om du behöll raden `Write("John Doe")` visas “John Doe” i kontrollen och platshållaren försvinner.

## Fullständigt fungerande exempel

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet. Det innehåller alla stegen ovan samt några defensiva kontroller.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise document and builder.
        Document document = new Document();
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // 2️⃣ Create a plain‑text SDT (content control).
        StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
            document, SdtType.PlainText, true);
        plainTextSdt.Title = "CustomerName";
        plainTextSdt.Tag   = "CustomerNameTag";
        plainTextSdt.PlaceholderText = "Enter name here";

        // 3️⃣ Insert the control into the document.
        docBuilder.InsertNode(plainTextSdt);

        // 4️⃣ (Optional) Move to the control and set default text.
        plainTextSdt.RemoveAllChildren();   // Clear placeholder.
        docBuilder.MoveTo(plainTextSdt);    // Move cursor inside.
        docBuilder.Write("John Doe");       // Write default value.

        // 5️⃣ Save the file.
        string outputPath = @"C:\Temp\SDTExample.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kör programmet, öppna den genererade filen, så ser du att allt fungerar exakt som beskrivet.

## Vanliga frågor & kantfall

### Vad händer om jag behöver en **dropdown** istället för vanlig text?

Byt ut `SdtType.PlainText` mot `SdtType.DropDownList` och fyll `ListItems`‑samlingen. Resten av arbetsflödet – `InsertNode`, `MoveTo`, `SetTagAttribute` – förblir oförändrat.

### Kan jag **sätta tag attribute** efter insättning?

Absolut. `Tag`‑egenskapen kan ändras när som helst:

```csharp
plainTextSdt.Tag = "NewTagValue";
```

Kom bara ihåg att spara dokumentet igen för att förändringen ska bli bestående.

### Hur hittar jag en **kontroll senare** i ett stort dokument?

Använd metoden `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` och filtrera på `Tag` eller `Title`. Detta är praktiskt när du behöver ersätta platshållartext i bulk.

```csharp
foreach (StructuredDocumentTag sdt in document.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    if (sdt.Tag == "CustomerNameTag")
    {
        // Do something with this control.
    }
}
```

### Vad händer om jag vill att platshållaren ska visas på **alla språk**?

Aspose.Words stödjer lokalanpassad platshållartext via egenskapen `PlaceholderName`. Sätt den till en resursträng som varierar per kultur.

## Tips & tricks (Pro Tips)

- **Återanvänd samma SDT** i flera dokument genom att klona den (`plainTextSdt.Clone(true)`), och sedan infoga klonen där den behövs.
- **Undvik dubblett‑taggar**; de gör senare sökningar tvetydiga. Håll taggar unika per dokument.
- **Prestandatips:** Om du genererar tusentals dokument, återanvänd en enda `Document`‑instans som mall och ersätt bara platshållartexten. Detta minskar overhead för objekt‑skapande.

## Slutsats

Vi har gått igenom allt du behöver för att **ställa in platshållartext** i en Aspose.Words StructuredDocumentTag, från att skapa kontrollen till att flytta till den, skriva standardinnehåll och tilldela ett tag‑attribut. Med den här kunskapen kan du bygga dynamiska Word‑mallar som guidar användare, upprätthåller datainmatningsregler och är enkla att underhålla.

Redo för nästa utmaning? Prova att byta ut plain‑text‑SDT:n mot en **date picker** eller en **combo box**, eller utforska hur du binder SDT:er till XML‑datakällor för ännu rikare dokumentautomatisering.

Lycka till med kodandet, och må dina dokument alltid vara perfekt mallade!

## Vad du bör lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Ställ in innehållskontrollens stil](/words/hindi/net/programming-with-sdt/set-content-control-style/)
- [Ställ in innehållskontrollens färg](/words/hindi/net/programming-with-sdt/set-content-control-color/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}