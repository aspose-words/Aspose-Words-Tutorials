---
category: general
date: 2026-09-08
description: Ange taggnamn och skapa en innehållskontroll (SDT) i ett Word‑dokument
  med C#. Lär dig hur du lägger till SDT, skriver text till taggen och modifierar
  dokumentet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: sv
lastmod: 2026-09-08
og_description: Ange taggnamn och skapa en innehållskontroll (SDT) i ett Word‑dokument
  med C#. Följ den här steg‑för‑steg‑guiden för att lägga till SDT, skriva text till
  taggen och ändra dokumentet.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Ange taggnamn och lägg till SDT i ett Word‑dokument – C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man anger taggnamn och lägger till SDT i ett Word‑dokument med C#
url: /sv/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man anger taggnamn och lägger till SDT i ett Word-dokument med C#

Om du behöver **set tag name** för en StructuredDocumentTag (SDT) när du arbetar med Word-filer, visar den här guiden exakt hur. Du kommer att se ett komplett, körbart exempel som **creates a content control**, skriver text till taggen och **modifies the Word document** från början till slut.

Utvecklare frågar ofta, *“how to add sdt* till ett befintligt .docx och sedan *write text to tag*?” – svaret ligger i att använda Aspose.Words for .NET API. I slutet av den här tutorialen kommer du att kunna öppna en Word-fil, infoga en plain‑text SDT, **set tag name**, fylla den med innehåll och spara ändringarna utan att lämna några hängande resurser.

## Förutsättningar

* .NET 6.0 eller senare installerat.
* En giltig Aspose.Words for .NET-licens (eller så kan du arbeta med utvärderingsversionen).
* Visual Studio 2022 (eller någon IDE som stödjer C#).
* Ett inmatnings‑Word‑dokument (`input.docx`) placerat i en mapp som du kan referera till från kod.

## Steg 1: Ställ in projektet och importera namnrymder

Skapa ett nytt Console App‑projekt och lägg till Aspose.Words NuGet‑paketet:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Lägg sedan till de nödvändiga `using`‑direktiven högst upp i `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

## Steg 2: Ladda det befintliga Word‑dokumentet

Den första operationen är att ladda filen du vill redigera. Detta steg krävs för varje scenario där du **modify word document** innehåll.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Varför vi laddar dokumentet först** – `Document`‑objektet representerar hela .docx‑paketet i minnet. Endast efter inläsning kan du säkert infoga nya noder såsom en SDT.

## Steg 3: Infoga en StructuredDocumentTag (SDT) och ange dess taggnamn

Nu svarar vi på kärnfrågan: **how to add sdt** och **set tag name**. Vi använder `DocumentBuilder.InsertStructuredDocumentTag` med `SdtType.PlainText`. Det andra argumentet är taggnamnet, som du senare kan referera till programatiskt eller via Words UI.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Förklaring** – `InsertStructuredDocumentTag` returnerar en `StructuredDocumentTag`‑instans. Genom att skicka `"MyTag"` **set tag name** direkt vid skapandet. Om du behöver ändra den senare kan du tilldela ett nytt värde till `sdt.Tag`.

## Steg 4: Skriv text till den nyss skapade taggen

Efter att SDT‑en finns, vill du vanligtvis **write text to tag** så att slutanvändare ser en platshållare eller standardinnehåll. Metoden `SetText` gör exakt det.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Varför använda SetText** – Att direkt tilldela `Text`‑egenskapen skulle ersätta hela nodhierarkin. `SetText` uppdaterar säkert den inre texten i innehållskontrollen samtidigt som strukturen bevaras.

## Steg 5: Spara det modifierade dokumentet

Till sist, spara ändringarna till en ny fil. Detta slutför **modify word document**‑arbetsflödet.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

När du öppnar `output.docx` i Microsoft Word kommer du att se en plain‑text innehållskontroll märkt **MyTag** som innehåller texten “Sample content”. Kontrollen kan redigeras manuellt, och taggnamnet förblir tillgängligt via Words utvecklarverktyg.

## Fullständig källkod

Nedan är det kompletta, självständiga programmet. Kopiera det till `Program.cs` och kör det; inga ytterligare kodsnuttar behövs.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Förväntad utskrift i konsolen

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Så ser den resulterande Word-filen ut

![Word-dokument som visar en innehållskontroll med namn MyTag och texten “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Exempel på att sätta taggnamn i ett Word-dokument"}

*Skärmdumpen illustrerar SDT med **tag name** satt till *MyTag* och den inbäddade texten synlig.*

## Vanliga variationer och kantfall

| Situation | Hur man hanterar det |
|-----------|----------------------|
| **Create a rich‑text SDT** | Use `SdtType.RichText` instead of `PlainText`. |
| **Set a different tag name after insertion** | `sdt.Tag = "NewTag";` – you can re‑assign the tag name at any time. |
| **Add the SDT inside a specific paragraph** | Move the builder’s cursor (`builder.MoveToParagraph(index)`) before calling `InsertStructuredDocumentTag`. |
| **Multiple SDTs in the same document** | Repeat steps 3‑4 for each control; each can have a unique tag name. |
| **Working with protected documents** | Ensure the document is unprotected (`doc.Unprotect()`) before inserting an SDT. |

## Proffstips för robust Word-automation

* **Licensiera tidigt** – Anropa `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` i början av `Main` för att undvika utvärderingsvattenstämplar.
* **Dispose objects** – Wrappa `Document` i ett `using`‑block om du riktar dig mot .NET Framework för att garantera att filhandtag frigörs.
* **Validate tag existence** – När du läser ett dokument senare, använd `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` för att hitta taggar via `Tag`‑egenskapen.
* **Performance** – För stora dokument, ladda endast nödvändiga sektioner med `LoadOptions` tillsammans med `LoadFormat.Docx` och `LoadFormat.Auto`.  

## Slutsats

Du vet nu hur man **set tag name**, **create a content control**, **write text to tag**, och **modify a Word document** med C#. Det kompletta exemplet demonstrerar standardmönstret för **how to add sdt** och hur man säkert sparar ändringar.  

Från här

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Lägg till innehåll med Document Builder i Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/)
- [Word-dokument – Hur man tar bort innehåll](/words/english/net/remove-content/)
- [Skapa Word-dokument med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}