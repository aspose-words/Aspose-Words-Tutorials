---
category: general
date: 2026-10-13
description: Skapa ett nytt Word‑dokument i C# och infoga en innehållskontroll med
  platshållartext. Lär dig hur du sätter platshållartext och sparar Word‑dokumentet
  effektivt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: sv
lastmod: 2026-10-13
og_description: Skapa ett nytt Word-dokument i C# med Aspose.Words, infoga en innehållskontroll,
  ange platshållartext och spara Word-dokumentet – allt i en enda guide.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Skapa ett nytt Word‑dokument och infoga innehållskontroll i C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Skapa ett nytt Word-dokument och infoga innehållskontroll i C#
url: /sv/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa nytt Word-dokument och infoga innehållskontroll i C#

Om du behöver **skapa ett nytt Word-dokument** programatiskt visar den här guiden hur du gör det med Aspose.Words för .NET. Du kommer att lära dig att **infoga innehållskontroll**, tilldela **platshållartext**, och slutligen **spara Word-dokument C#** kod som du kan kopiera in i ditt projekt.

Handledningen går igenom varje steg, förklarar varför varje API-anrop är viktigt, och täcker vanliga variationer såsom att lägga till en rich‑text SDT eller hantera befintliga dokument. I slutet har du ett komplett, körbart exempel som du kan anpassa till fakturor, kontrakt eller någon annan mallbaserad Word-utmatning.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
* Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)
* En IDE såsom Visual Studio 2022 eller Visual Studio Code

Inga ytterligare bibliotek krävs.

## Skapa nytt Word-dokument med Aspose.Words

Det första steget är att instansiera ett `Document`‑objekt. Detta objekt representerar en tom Word‑fil i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` ger dig ett flytande API för att infoga element vid den aktuella markörpositionen. Eftersom dokumentet är tomt startar markören i början av den första (och enda) sektionen.

## Infoga innehållskontroll (StructuredDocumentTag)

En **innehållskontroll** i Word kallas Structured Document Tag (SDT). Följande kod skapar en plain‑text SDT, sätter dess titel och definierar platshållartext som visas när användaren öppnar filen.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Varför detta är viktigt:**  
* `SdtType.PlainText` begränsar innehållet till en enda rad med vanlig text, vilket är idealiskt för enkla fält som namn eller e‑post.  
* Att sätta `PlaceholderName` ger en visuell ledtråd (`Enter name here`) som vägleder slutanvändaren.  

Om du behöver ett rikare fält (t.ex. flerradig text eller en datumväljare), ersätt `SdtType.PlainText` med `SdtType.RichText` eller `SdtType.Date`.

## Lägg till valfri omgivande text

De flesta mallar innehåller en etikett före innehållskontrollen. Du kan lägga till den med samma `DocumentBuilder`‑instans:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Den resulterande Word‑filen visar:

```
Customer Name: [Enter name here]
```

## Spara Word-dokument i C#‑stil

Slutligen skriver du dokumentet till disk. Aspose.Words bestämmer automatiskt formatet utifrån filändelsen.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

När du öppnar `output.docx` i Microsoft Word kommer du att se platshållartexten inuti en gråskuggad innehållskontroll. Användare kan klicka på kontrollen och ersätta platshållaren med sitt eget värde.

## Fullt, körbart exempel

Nedan är ett fristående konsolprogram som sätter ihop allt. Kopiera koden till ett nytt konsolprojekt och kör det.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förväntad utskrift** (konsol):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

När du öppnar `output.docx` visas en enda rad med etiketten *Customer Name:* följt av en innehållskontroll som visar *Enter name here*.

## Vanliga variationer och kantfall

| Scenario | Kodändring | Orsak |
|----------|------------|-------|
| **Rich‑text field** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Tillåter flerradig inmatning och grundläggande formatering. |
| **Read‑only control** | `sdt.LockContentControl = true;` | Förhindrar att användare redigerar kontrollens innehåll. |
| **Pre‑populate with data** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Infogar ett standardvärde som skriver över platshållaren. |
| **Add to an existing document** | Load with `new Document("template.docx")` instead of an empty `Document` | Möjliggör mallscenarier där kontrollen placeras i en fördefinierad layout. |
| **Multiple controls** | Repeat the creation block with different titles and placeholders | Användbart för formulär som samlar in flera uppgifter. |

### Proffstips

När du genererar stora dokument, återanvänd en enda `DocumentBuilder`‑instans istället för att skapa en ny för varje kontroll. Detta minskar minnesbelastningen och förbättrar prestandan.

## Testa resultatet

1. Kör konsolappen.  
2. Öppna `output.docx` i Microsoft Word.  
3. Verifiera att platshållartexten visas i en gråskuggad ruta.  
4. Klicka på rutan, skriv ett namn och spara filen. Den inmatade texten ersätter platshållaren.

Om platshållaren inte visas, bekräfta att du använder Aspose.Words version 23.9 eller senare, eftersom äldre versioner hade en bugg med `PlaceholderName` på plain‑text SDT:er.

## Slutsats

Du vet nu hur du **skapar ett nytt Word-dokument**, **infogar innehållskontroll**, **sätter platshållartext**, och **sparar Word-dokument C#** med hjälp av Aspose.Words. Det kompletta exemplet demonstrerar standardmönstret, och variationstabellen visar hur du anpassar lösningen för mer avancerade scenarier.

Nästa steg kan du utforska:

* **Infoga innehållskontroll för datum** – använd `SdtType.Date`‑enumerationen.  
* **Fyll i en mall med data** – kombinera `StructuredDocumentTag` med mail‑merge‑fält.  
* **Exportera till PDF** – anropa `doc.Save("output.pdf")` efter att ha lagt till kontroller.

Känn dig fri att experimentera med olika SDT‑typer, låsinställningar och styling för att matcha ditt projekts krav. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa nytt Word-dokument](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Infoga textinmatningsformulärfält i Word-dokument](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Skapa Word-dokument med Aspose.Words för .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}