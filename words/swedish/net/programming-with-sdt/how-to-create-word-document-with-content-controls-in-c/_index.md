---
category: general
date: 2026-09-05
description: Skapa ett Word‑dokument med Aspose.Words, ange platshållartext, lägg
  till en kontroll och spara dokumentet som docx i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: sv
lastmod: 2026-09-05
og_description: Skapa ett Word-dokument med Aspose.Words för .NET, ange platshållartext,
  lägg till en kontroll och spara dokumentet som docx. Följ den här kompletta handledningen.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Skapa ett Word‑dokument med innehållskontroller i C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Hur man skapar ett Word‑dokument med innehållskontroller i C#
url: /sv/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar Word-dokument med innehållskontroller i C#

Om du behöver **create word document** som innehåller strukturerade innehållskontroller, visar den här guiden hur du lägger till en ren‑text‑tagg, **set placeholder text**, och **save document as docx** med Aspose.Words för .NET. Exemplet är fullt körbart och demonstrerar den rekommenderade metoden för programmatisk Word‑generering.

Du kommer att lära dig hur du:

* Initiera en tom Word‑fil med `Document` och `DocumentBuilder`.
* **How to add control** (en `StructuredDocumentTag`) till dokumentets kropp.
* **How to create tag** med en titel och platshållare som guidar slutanvändaren.
* Spara resultatet med `document.Save`, så att filen blir en giltig `.docx`.

Handledningen förutsätter att du har en grundläggande C#‑utvecklingsmiljö och en licens för Aspose.Words (den kostnadsfria utvärderingen fungerar för lärandeändamål).

---

## Förutsättningar

| Krav | Orsak |
|------|-------|
| .NET 6.0 or later | Tillhandahåller runtime för Aspose.Words för .NET. |
| Aspose.Words for .NET NuGet package | Tillhandahåller klasserna `Document`, `DocumentBuilder` och `StructuredDocumentTag`. |
| IDE such as Visual Studio 2022 | Gör det enkelt att köra och felsöka exemplet. |

Installera paketet med .NET CLI:

```bash
dotnet add package Aspose.Words
```

---

## Steg 1: Ställ in projektet för att **create word document**

Skapa ett nytt konsolprojekt (eller lägg till koden i ett befintligt). De första raderna instansierar en tom Word‑fil och en `DocumentBuilder` som låter dig skriva innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` representerar filstrukturen, medan `DocumentBuilder` spårar infogningspunkten. Detta mönster är grunden för alla Word‑genereringsscenarier.

---

## Steg 2: **How to add control** – skapa en ren‑text‑innehållskontroll (tagg)

En innehållskontroll i Word kallas en *structured document tag* (SDT). Följande kod skapar en ren‑text‑SDT, tilldelar en titel och definierar platshållaren som visas när dokumentet öppnas.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Varför detta är viktigt:**
* `Title`‑egenskapen fungerar som en stabil identifierare, vilket gör att du senare kan hitta eller ersätta kontrollen programatiskt.
* `PlaceholderName` ger visuell vägledning till dokumentets mottagare utan att kräva extra UI‑kod.

![Skapa Word-dokument med en innehållskontroll som visar platshållartext](image.png)

*Image alt text: Skapa Word-dokument med en innehållskontroll som visar platshållartext.*

---

## Steg 3: Flytta markören in i kontrollen och skriv standardtext

Efter att kontrollen har infogats pekar builderns markör fortfarande utanför den. Flytta markören in i taggen så att efterföljande skrivningar blir en del av kontrollens innehåll.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Om du föredrar att låta kontrollen vara tom, utelämna `Write`‑anropet. Platshållaren förblir synlig tills användaren skriver in ett värde.

---

## Steg 4: **Set placeholder text** (alternativ metod)

Ibland behöver du ändra platshållaren efter att taggen har skapats. Du kan ändra `PlaceholderName`‑egenskapen direkt:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Att ändra platshållaren påverkar **inte** det befintliga innehållet, vilket gör det säkert att uppdatera UI‑tips utan att ändra användargenererad data.

---

## Steg 5: **Save document as docx**

Spara det minnesbaserade dokumentet till en fysisk fil. `Save`‑metoden bestämmer automatiskt formatet utifrån filändelsen.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Om du behöver ett annat format (t.ex. PDF eller HTML), ange ett `SaveFormat`‑enum‑värde:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Steg 6: Fullt, körbart exempel

När delarna sätts ihop får du ett koncist program som demonstrerar **how to create tag**, sätter dess platshållare och **save document as docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Förväntad output:**
När programmet körs skapas `SdtExample.docx` som innehåller ett enda stycke med en ren‑text‑innehållskontroll med titeln *CustomerName*. Kontrollen visar “John Doe” som sitt initiala innehåll; om standardtexten tas bort visas platshållaren “Enter name” i ljusgrått när filen öppnas i Microsoft Word.

---

## Vanliga variationer och kantfall

| Scenario | Rekommenderad justering |
|----------|------------------------|
| **Multiple controls** | Upprepa steg 2‑4 för varje fält och ge varje en unik `Title`. |
| **Rich‑text control** | Använd `SdtType.RichText` istället för `PlainText`. |
| **Repeating section** | Välj `SdtType.RepeatingSection` och lägg till underkontroller i sektionen. |
| **Existing document** | Läs in en befintlig fil med `new Document("template.docx")` och infoga kontroller på önskad plats. |
| **Unicode placeholder** | Sätt `PlaceholderName` till en valfri Unicode‑sträng; Word renderar den korrekt. |
| **Large documents** | Disposera `DocumentBuilder` efter användning för att frigöra minne (`builder.Dispose();`). |

**Pro tip:** När du senare behöver hämta det användargenererade värdet, anropa `StructuredDocumentTag.GetText()` efter att dokumentet har sparats och öppnats igen. Denna metod returnerar den inre texten utan platshållaren.

**Watch out for:** Att använda en platshållare som matchar standardtexten kan skapa förvirring, eftersom Word döljer platshållaren när någon text finns. Håll dem åtskilda.

---

## Slutsats

Du vet nu hur du **create word document** programatiskt, **how to add control**, **how to create tag**, **set placeholder text**, och **save document as docx** med Aspose.Words för .NET. Det kompletta exemplet kan kopieras in i vilket C#‑projekt som helst och utökas för att stödja ytterligare kontrolltyper, repeterande sektioner eller integration med datakällor.

Nästa steg du kan utforska inkluderar:

* Lägga till **image content controls** (`SdtType.Picture`) för att bädda in grafik som tillhandahålls av användaren.  
* Använda **binding** för att mappa SDT:er till XML‑data för mail‑merge‑scenarier.  
* Konvertera det genererade DOCX‑dokumentet till PDF (`SaveFormat.Pdf`) för distribution.

Experimentera med olika taggtyper och platshållarmeddelanden för att matcha ditt programs arbetsflöde. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument med Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Skapa ett Word-dokument med tabell med Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Skapa Word-dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}