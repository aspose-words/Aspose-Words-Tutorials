---
category: general
date: 2026-11-25
description: Lär dig hur du skapar ett Word-dokument, lägger till en rektangelform,
  sammanfattar dokumentet med AI, översätter text med AI och sparar dokumentet som
  DOCX med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: sv
lastmod: 2026-11-25
og_description: Skapa ett Word-dokument, lägg till en rektangelform, sammanfatta dokumentet
  med AI, översätt text med AI och spara dokumentet som DOCX – allt i en enda C#-handledning.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Skapa ett Word-dokument med former, AI‑sammanfattning och översättning i
  C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Hur man skapar ett Word-dokument med former, AI‑sammanfattning och översättning
  i C#
url: /sv/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett Word-dokument med former, AI‑sammanfattning och översättning i C#

Om du behöver **skapa ett Word-dokument** programatiskt visar den här guiden exakt hur. Med Aspose.Words för .NET kommer du att lära dig att **lägga till en rektangel‑form**, anropa en AI‑tjänst för att **sammanfatta dokumentet med AI**, översätta ett stycke med **översätta text med AI**, och slutligen **spara dokumentet som DOCX**.

Många utvecklare har svårt att kombinera dokumentautomatisering med moderna AI‑funktioner. I slutet av den här handledningen har du ett enda, självständigt C#‑projekt som producerar en fullt formaterad *.docx*-fil, komplett med en visuell form, AI‑genererad sammanfattning och flerspråkigt innehåll.

## Förutsättningar

Innan du börjar, se till att du har:

- .NET 6.0 SDK eller senare installerat  
- Visual Studio 2022 (eller någon C#‑IDE)  
- En Aspose.Words för .NET‑licens (eller en gratis utvärderingsnyckel)  
- Internetåtkomst för AI‑sammanfattning och översättningsanrop  

Inga ytterligare NuGet‑paket krävs förutom `Aspose.Words` och `Aspose.Words.AI`.

## Steg 1: Ställ in projektet och lägg till nödvändiga paket

Skapa ett nytt konsolprojekt och hämta Aspose.Words‑biblioteken.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Proffstips:** Om du planerar att använda utvärderingsläget, anropa `Aspose.Words.License.SetLicense("Aspose.Words.lic");` tidigt i `Main` för att undvika vattenstämplar.

## Steg 2: Initiera dokumentet – kärnan i **create word document**

Den första körbara kodraden skapar ett nytt **Word-dokument**‑objekt. Detta objekt är duken för alla efterföljande operationer.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` förenklar insättning av text, former och kontroller utan att manuellt hantera lågnivå‑nodträd.

## Steg 3: **Add rectangle shape** till dokumentet

En rektangel‑form kan användas som en visuell platshållare, en etikettbakgrund eller en enkel grafik. Vi skapar först en `GroupShape` och infogar sedan en `Rectangle` i den.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Rektangeln är 100 punkter bred och 50 punkter hög. Eftersom den finns i en `GroupShape` kan du senare lägga till fler element (t.ex. textrutor) utan att oroa dig för layoutkollisioner.

## Steg 4: Infoga en vanlig text StructuredDocumentTag (SDT)

StructuredDocumentTag‑objekt är användbara för innehållskontroller som senare kan bindas till datakällor.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

`true`‑flaggan markerar taggen som en **upprepande** kontroll, vilket är praktiskt för mallar.

## Steg 5: Lägg till en ActiveX CommandButton‑kontroll (valfritt UI)

Om det genererade dokumentet ska användas i en miljö som stödjer ActiveX kan du bädda in en knapp.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Detta steg är valfritt; du kan ta bort det om din målgrupp aldrig interagerar med dokumentet i en Windows‑miljö.

## Steg 6: **Summarize document with AI**

Aspose.Words.AI erbjuder ett bekvämt omslag runt stora språkmodelltjänster. Här anropar vi `DocumentSummarizer.Summarize` med OpenAI‑bakänden.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Metoden analyserar det aktuella nodträdet, extraherar de mest relevanta meningarna och returnerar ett koncist stycke. Detta är kärnan i **summarize document with AI**‑funktionaliteten.

## Steg 7: **Translate text using AI**

Här demonstrerar vi hur man översätter en exempelsträng från engelska till franska. Metoden `Translator.Translate` anropar internt en Google‑AI‑modell.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Du kan ersätta `Language.French` med vilket som helst av de stödjade språk‑enum‑värdena, vilket möjliggör flerspråkig dokumentgenerering i realtid.

## Steg 8: **Save document as DOCX**

Slutligen sparas det redigerade dokumentet till disk. Metoden `Save` skriver automatiskt en *.docx*-fil när du anger filändelsen `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

Filen `Result.docx` innehåller nu:

- En rektangel‑form i en gruppform  
- En vanlig text‑innehållskontroll (SDT)  
- En ActiveX CommandButton (om du behöll Steg 5)  
- Ett AI‑genererat sammanfattningsstycke  
- En fransk översättning av “Hello world”

Du kan öppna filen i Microsoft Word för att verifiera varje element.

## Komplett källkod

Nedan är det fullständiga, färdiga programmet. Kopiera det till `Program.cs` och kör `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Förväntad output

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

När du öppnar `Result.docx` kommer du att se rektangel‑formen nära toppen, SDT‑platshållaren, knappen, sammanfattningsstycket och den franska översättningen infogad som vanlig text.

## Slutsats

Du vet nu hur man **skapar ett Word-dokument** från grunden, **lägger till en rektangel‑form**, **sammanfattar dokumentet med AI**, **översätter text med AI**, och **sparar dokumentet som DOCX**—allt med några korta rader C#. Detta mönster skalar: du kan ersätta de hårdkodade strängarna med dynamiska data, lägga till fler former eller diagram, och byta AI‑leverantör genom att justera `SummarizerOptions` eller `Translator`‑parametrarna.

### Vad är nästa steg?

- Utforska variationer av **add rectangle shape**: ändra fyllningsfärg, linjestil eller lägg till text i formen.  
- Använd **summarize document with AI** på större dokument för att automatiskt generera ledningssammanfattningar.  
- Utöka **translate text using AI** för att batch‑processa hela stycken eller tabeller för flerspråkiga rapporter.  
- Kombinera Aspose.Words diagram‑API:er för att bädda in datavisualiseringar tillsammans med AI‑genererade insikter.  

Känn dig fri att experimentera och dela dina resultat i kommentarerna eller på GitHub. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa ett tomt Word-dokument och lägg till en rektangel‑form](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Lägg till textvattenstämpel i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}