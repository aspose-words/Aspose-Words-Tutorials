---
category: general
date: 2026-11-25
description: Leer hoe je een Word‑document maakt, een rechthoekvorm toevoegt, het
  document samenvat met AI, tekst vertaalt met AI en het document opslaat als DOCX
  met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: nl
lastmod: 2026-11-25
og_description: Maak een Word‑document, voeg een rechthoekvorm toe, vat het document
  samen met AI, vertaal de tekst met AI en sla het document op als DOCX – allemaal
  in één C#‑tutorial.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Maak een Word-document met vormen, AI-samenvatting en vertaling in C#
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
title: Hoe maak je een Word-document met vormen, AI-samenvatting en vertaling in C#
url: /nl/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een Word‑document met vormen, AI‑samenvatting en vertaling in C#

Als je **programmeer­matig een Word‑document wilt maken**, laat deze gids je precies zien hoe. Met Aspose.Words voor .NET leer je **een rechthoekige vorm toevoegen**, een AI‑service aanroepen om het **document samen te vatten met AI**, een alinea **vertalen met AI**, en tenslotte het **document opslaan als DOCX**.

Veel ontwikkelaars worstelen met het combineren van documentautomatisering en moderne AI‑functies. Aan het einde van deze tutorial heb je een enkel, zelfstandig C#‑project dat een volledig opgemaakte *.docx*‑file produceert, compleet met een visuele vorm, AI‑gegenereerde samenvatting en meertalige inhoud.

## Vereisten

Zorg ervoor dat je het volgende hebt:

- .NET 6.0 SDK of later geïnstalleerd  
- Visual Studio 2022 (of een andere C#‑IDE)  
- Een Aspose.Words voor .NET‑licentie (of een gratis evaluatiesleutel)  
- Internettoegang voor de AI‑samenvatting‑ en vertaal‑aanroepen  

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words` en `Aspose.Words.AI`.

## Stap 1: Het project opzetten en benodigde pakketten toevoegen

Maak een nieuw console‑project aan en haal de Aspose.Words‑bibliotheken binnen.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** Als je de evaluatiemodus wilt gebruiken, roep dan `Aspose.Words.License.SetLicense("Aspose.Words.lic");` vroeg in `Main` aan om watermerken te vermijden.

## Stap 2: Het document initialiseren – de kern van **create word document**

De eerste uitvoerbare regel code maakt een nieuw **Word‑document**‑object aan. Dit object is het canvas voor alle daaropvolgende bewerkingen.

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

De `DocumentBuilder` vereenvoudigt het invoegen van tekst, vormen en besturingselementen zonder handmatig met low‑level node‑bomen te werken.

## Stap 3: **Add rectangle shape** aan het document

Een rechthoekige vorm kan dienen als visuele placeholder, label‑achtergrond of eenvoudige grafiek. We maken eerst een `GroupShape` aan en voegen vervolgens een `Rectangle` toe.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

De rechthoek is 100 punten breed en 50 punten hoog. Omdat hij zich binnen een `GroupShape` bevindt, kun je later meer elementen (bijv. tekstvakken) toevoegen zonder je zorgen te maken over lay‑outconflicten.

## Stap 4: Een platte‑tekst StructuredDocumentTag (SDT) invoegen

StructuredDocumentTag‑objecten zijn handig voor content‑controls die later aan gegevensbronnen kunnen worden gekoppeld.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

De `true`‑vlag markeert de tag als een **repeating**‑control, wat handig is voor sjablonen.

## Stap 5: Een ActiveX CommandButton‑control toevoegen (optionele UI)

Als het gegenereerde document wordt gebruikt in een omgeving die ActiveX ondersteunt, kun je een knop insluiten.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Deze stap is optioneel; je kunt hem weglaten als je doelgroep het document nooit in een Windows‑omgeving zal gebruiken.

## Stap 6: **Summarize document with AI**

Aspose.Words.AI biedt een handige wrapper rond large‑language‑model‑services. Hier roepen we `DocumentSummarizer.Summarize` aan met de OpenAI‑backend.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

De methode analyseert de huidige node‑boom, haalt de meest relevante zinnen eruit en retourneert een beknopte alinea. Dit is de kern van de functionaliteit **summarize document with AI**.

## Stap 7: **Translate text using AI**

Vervolgens laten we zien hoe je een voorbeeldtekst van Engels naar Frans vertaalt. De `Translator.Translate`‑methode roept intern een Google‑AI‑model aan.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Je kunt `Language.French` vervangen door elke ondersteunde taal‑enumwaarde, waardoor je on‑the‑fly meertalige documentgeneratie mogelijk maakt.

## Stap 8: **Save document as DOCX**

Tot slot sla je het bewerkte document op schijf op. De `Save`‑methode schrijft automatisch een *.docx*‑bestand wanneer je de extensie `.docx` opgeeft.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

Het bestand `Result.docx` bevat nu:

- Een rechthoekige vorm binnen een group‑shape  
- Een platte‑tekst content‑control (SDT)  
- Een ActiveX CommandButton (als je Stap 5 hebt behouden)  
- Een AI‑gegenereerde samenvattingsalinea  
- Een Franse vertaling van “Hello world”

Je kunt het bestand openen in Microsoft Word om elk element te verifiëren.

## Complete broncode

Hieronder staat het volledige, kant‑klaar programma. Kopieer het naar `Program.cs` en voer `dotnet run` uit.

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

### Verwachte output

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Wanneer je `Result.docx` opent, zie je de rechthoekige vorm bovenaan, de SDT‑placeholder, de knop, de samenvattingsalinea en de Franse vertaling als platte tekst.

## Conclusie

Je weet nu hoe je **een Word‑document** vanaf nul maakt, **een rechthoekige vorm toevoegt**, **document samenvat met AI**, **tekst vertaalt met AI**, en **het document opslaat als DOCX**—allemaal met een paar beknopte C#‑regels. Dit patroon schaalt: je kunt de hard‑gecodeerde strings vervangen door dynamische data, meer vormen of grafieken toevoegen, en de AI‑provider wijzigen door de `SummarizerOptions`‑ of `Translator`‑parameters aan te passen.

### Wat is het volgende?

- Verken variaties op **add rectangle shape**: wijzig vulkleur, lijntype of voeg tekst toe binnen de vorm.  
- Gebruik **summarize document with AI** op grotere documenten om automatisch executive summaries te genereren.  
- Breid **translate text using AI** uit om volledige alinea’s of tabellen batch‑gewijs te vertalen voor meertalige rapporten.  
- Combineer Aspose.Words‑chart‑API’s om datavisualisaties naast AI‑gegenereerde inzichten in te sluiten.  

Experimenteer gerust, en deel je resultaten in de reacties of op GitHub. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}