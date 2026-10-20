---
category: general
date: 2026-10-20
description: Ställ in platshållartext i ett Word‑dokument med C#. Lär dig hur du snabbt
  lägger till kontroll och sätter platshållare med Aspose.Words för .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: sv
lastmod: 2026-10-20
og_description: Ställ in platshållartext i ett Word‑dokument med C#. Den här handledningen
  visar hur du lägger till kontroll, sätter platshållare och genererar Word‑filer
  programatiskt.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Ange platshållartext i ett Word‑dokument med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Ange platshållartext i ett Word‑dokument med C#
url: /sv/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ange platshållartext i ett Word‑dokument med C#

Om du behöver **ange platshållartext** i en Microsoft Word‑fil när du genererar den med C#, visar den här guiden exakt hur du gör. Du får en kortfattad, end‑to‑end‑lösning som lägger till en innehållskontroll, definierar dess platshållare och sparar dokumentet – allt med Aspose.Words för .NET.

Många utvecklare undrar **hur man lägger till kontroll** i ett Word‑dokument eller **hur man anger platshållare** utan att öppna Word manuellt. Denna handledning svarar på de frågorna och demonstrerar dessutom ett rent sätt att **generera Word C#**‑filer som är redo för användarinmatning.

## Vad du kommer att åstadkomma

I slutet av den här handledningen kommer du att:

* Skapa ett tomt Word‑dokument programmässigt.
* Infoga en ren‑text Structured Document Tag (SDT), vilket är det tekniska namnet för en innehållskontroll.
* Tilldela en meningsfull titel och platshållartext till SDT:n.
* Spara den resulterande `.docx`‑filen till disk.

Inga extra verktyg krävs utöver Aspose.Words‑biblioteket och en .NET 6 (eller senare) utvecklingsmiljö.

## Förutsättningar

* .NET 6 SDK eller nyare installerat.  
* Visual Studio 2022 (eller någon IDE som stödjer .NET).  
* Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`).  

> **Pro tip:** Använd den kostnadsfria utvärderingsversionen av Aspose.Words om du bara testar; den lägger till ett vattenmärke men fungerar annars på samma sätt som den licensierade versionen.

## Steg 1: Ställ in projektet och importera namnrymder

Skapa ett nytt konsolprojekt och lägg till de nödvändiga `using`‑direktiven. Dessa importerar de centrala Aspose.Words‑klasserna och markup‑namnrymden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Varför detta steg är viktigt:* Genom att importera `Aspose.Words.Markup` får du åtkomst till `StructuredDocumentTag`, `SdtType` och `MarkupLevel` – objekten som behövs för att **lägga till kontroll** och **ange platshållare**.

## Steg 2: Skapa ett tomt dokument och en DocumentBuilder

Ett `Document` representerar hela Word‑filen, medan en `DocumentBuilder` ger en bekväm markör för att infoga element.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta steg är viktigt:* Att börja med ett rent dokument säkerställer att den platshållare du anger visas exakt där du vill, utan störningar från befintligt innehåll.

## Steg 3: Skapa innehållskontrollen (Structured Document Tag)

Här skapar vi en ren‑text SDT, ger den en titel och anger den platshållartext som användaren kommer att se när kontrollen är tom.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Varför detta steg är viktigt:* `Title`‑egenskapen låter dig referera till kontrollen senare (t.ex. för databindning). `PlaceholderName` är exakt den **platshållartext** du vill att ska visas och guidar slutanvändaren.

## Steg 4: Infoga kontrollen på den aktuella markörpositionen

Med `DocumentBuilder` infogar du SDT:n i dokumentet där byggaren för närvarande är placerad.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Varför detta steg är viktigt:* När du infogar noden kopplas kontrollen till dokumentets DOM. Om du behöver lägga till flera platshållare kan du flytta byggarens markör och upprepa detta steg.

## Steg 5: Spara dokumentet

Skriv slutligen dokumentet till disk. Ersätt `YOUR_DIRECTORY` med en faktisk sökväg på din maskin.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

När du öppnar `SDT.docx` i Microsoft Word ser du en gråtonad inline‑textruta som visar **Enter name here**. När du klickar i rutan rensas platshållaren och användaren kan skriva in ett kundnamn.

### Förväntat resultat

| Filplats | Förhandsgranskning av innehåll |
|----------|--------------------------------|
| `C:\Temp\SDT.docx` | Inline‑platshållare **Enter name here** i en ren‑text innehållskontroll med titeln *CustomerName*. |

## Specialfall och variationer

| Situation | Rekommenderad justering |
|-----------|------------------------|
| **Flera platshållare** | Skapa ytterligare `StructuredDocumentTag`‑objekt med olika `Title`‑ och `PlaceholderName`‑värden, och infoga varje där det behövs. |
| **Rich‑text‑platshållare** | Använd `SdtType.RichText` istället för `PlainText` för att tillåta formatering i platshållaren. |
| **Block‑nivå‑kontroll** | Ändra `MarkupLevel.Inline` till `MarkupLevel.Block` för att få kontrollen att fungera som ett helt stycke. |
| **Platshållaren syns inte** | Säkerställ att dokumentets visningsinställningar i Word inte är satta på att dölja innehållskontroller (`File → Options → Advanced → Show content controls`). |
| **Spara till en ström** | Anropa `doc.Save(stream, SaveFormat.Docx)` om du behöver skicka filen via HTTP istället för att skriva till disk. |

## Fullt, körbart exempel

Nedan finns hela programmet som du kan kopiera, klistra in och köra. Det innehåller alla stegen ovan i en enda `Main`‑metod.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Kör programmet, öppna den genererade filen, och du kommer att se platshållartexten redo för användarinmatning.

## Vanliga frågor besvarade

**Q: Fungerar detta med .NET Core?**  
A: Ja. Aspose.Words for .NET är kompatibel med .NET Core, .NET 5 och .NET 6+. Samma kod körs oförändrad.

**Q: Kan jag ange ett standardvärde utöver platshållaren?**  
A: Använd `sdt.SetText("Default value")` efter att du skapat SDT:n. Platshållaren försvinner när ett värde har satts.

**Q: Vad händer om jag senare behöver hämta det inmatade värdet?**  
A: Ladda dokumentet, lokalisera SDT:n via dess `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) och läs `sdt.GetText()`.

## Slutsats

Du vet nu hur du **anger platshållartext** i ett Word‑dokument med C#. Genom att skapa en ren‑text `StructuredDocumentTag`, tilldela en titel och platshållare, infoga den med en `DocumentBuilder` och spara filen, kan du **lägga till kontroll** och **generera Word C#**‑filer programmässigt.  

Härnäst kan du utforska:

* Att lägga till rich‑text‑ eller rullgardinslistkontroller (`SdtType.RichText`, `SdtType.DropDownList`).  
* Att fylla flera platshållare från en databas.  
* Att konvertera den genererade `.docx`‑filen till PDF med Aspose.Words.

Experimentera med olika kontrolltyper och platshållarstilar för att passa ditt programs behov. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

De följande handledningarna behandlar närliggande ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringssätt i dina egna projekt.

- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}