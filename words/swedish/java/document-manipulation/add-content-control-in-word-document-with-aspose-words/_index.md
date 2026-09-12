---
category: general
date: 2026-09-11
description: Lägg till innehållskontroll i Word‑dokument med Aspose.Words. Följ den
  här steg‑för‑steg‑guiden för att programatiskt infoga en vanlig‑text Structured
  Document Tag (SDT).
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: sv
lastmod: 2026-09-11
og_description: Lägg till innehållskontroll i Word-dokument med Aspose.Words. Denna
  guide visar hur du programatiskt infogar en vanlig text Structured Document Tag
  (SDT) och anpassar den.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Lägg till innehållskontroll i Word‑dokument – komplett Aspose.Words‑handledning
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: Lägg till innehållskontroll i Word-dokument med Aspose.Words
url: /sv/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till innehållskontroll i Word-dokument med Aspose.Words

Om du behöver **add content control in Word document** programatiskt, visar den här handledningen exakt hur du gör det med Aspose.Words för .NET. Oavsett om du bygger en dokument‑genereringstjänst eller automatiserar formulärskapande, kommer du att lära dig att infoga en vanlig text Structured Document Tag (SDT) och ge den en meningsfull titel.

I den här guiden kommer du att se ett komplett, körbart exempel som täcker alla nödvändiga importeringar, förklarar varför varje API‑anrop är viktigt, och demonstrerar hur du verifierar resultatet. Inga externa referenser behövs—kopiera bara koden, kör den och öppna den genererade *.docx*-filen.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat  
* Visual Studio 2022 (eller någon C#‑IDE)  
* Aspose.Words for .NET 23.5 eller nyare – du kan skaffa ett gratis prov‑NuGet‑paket  

Dessa komponenter utgör den minsta uppsättningen för **word automation** med Aspose.Words.

## Steg 1: Ställ in projektet och importera namnrymder

Skapa ett nytt konsolprojekt och lägg till Aspose.Words‑paketet:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Öppna nu `Program.cs` och lägg till de nödvändiga `using`‑direktiven:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

Dessa namnrymder ger dig åtkomst till `DocumentBuilder`, `StructuredDocumentTag` och andra kärntyper som behövs för att **add content control in Word document**.

## Steg 2: Skapa ett nytt dokument och en DocumentBuilder

En `DocumentBuilder` är huvudingångspunkten för att bygga Word‑filer. Den har en markör som spårar var nästa element ska infogas.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt*: `Document`‑objektet representerar hela Word‑filen, medan `DocumentBuilder` förenklar infogandet av stycken, tabeller och **content controls** såsom Structured Document Tags.

## Steg 3: Infoga en vanlig‑text Structured Document Tag (SDT)

Kärnan i vår lösning är metoden `insertStructuredDocumentTag`. Den skapar en **content control** som kan hålla vanlig text, datum, rullgardinsmenyer osv. Här använder vi enum‑värdet `SdtType.PLAIN_TEXT`.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*Varför detta är viktigt*: Att sätta `true` får kontrollen att visas som en ljusgrå platshållare, vilket signalerar till slutanvändaren att de ska fylla i fältet.

## Steg 4: Ge SDT:n en titel för senare identifiering

En titel (eller tagg) låter dig hitta kontrollen senare, till exempel när du behöver ersätta dess innehåll programatiskt.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

Titeln visas inte i dokumentets UI, men den lagras i den underliggande XML‑en och kan hämtas via Aspose.Words‑API:t.

## Steg 5: Lägg till platshållartext i SDT:n

För att göra kontrollen mer användarvänlig, infoga ett standard‑run som talar om för användaren vad som ska skrivas.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*Varför detta är viktigt*: `Run`‑objektet representerar en textbit. Genom att lägga till det i SDT:n skapar du en synlig ledtråd som försvinner när användaren börjar skriva.

## Steg 6: Spara dokumentet

Sist, skriv dokumentet till disk så att du kan öppna det i Microsoft Word.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

När du öppnar `ContentControlExample.docx` kommer du att se en gråskuggad content control med titeln **CustomerName** och platshållartexten *Enter name here*.

## Fullständigt fungerande exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i `Program.cs`. Det inkluderar alla steg, kommentarer och nödvändig felhantering.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Förväntad output

När programmet körs skrivs:

```
Document saved to ContentControlExample.docx
```

När den genererade filen öppnas i Word visas en enda content control med den gråa platshållaren **Enter name here**. Kontrollens kan redigeras, tas bort eller nås programatiskt senare med dess titel *CustomerName*.

## Vanliga variationer och kantfall

| Scenario | Hur du anpassar koden |
|----------|----------------------|
| **Multiple content controls** | Anropa `InsertStructuredDocumentTag` upprepade gånger och tilldela en unik `Title` varje gång. |
| **Rich‑text content control** | Använd `SdtType.RichText` istället för `PlainText`. |
| **Date picker control** | Använd `SdtType.Date` och sätt eventuellt `sdt.DateDisplayFormat`. |
| **Locking the control** | Sätt `sdt.LockContentControl = true` för att förhindra att användare tar bort den. |
| **Finding a control later** | Använd `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` och filtrera på `Title`. |

Dessa variationer illustrerar flexibiliteten i **Aspose.Words** när du behöver **add content control in Word document** för olika formulärifyllnings‑scenarier.

## Pro‑tips

* **Prestanda** – Om du genererar många dokument i en loop, återanvänd en enda `DocumentBuilder`‑instans och anropa `doc.Clone()` för varje iteration för att undvika upprepad objektkonstruktion.  
* **Styling** – Du kan applicera ett `ParagraphFormat` eller `Font` på platshållar‑`Run` för att matcha ditt dokuments visuella tema.  
* **Validering** – Efter att ha infogat en kontroll kan du inspektera `sdt.IsShowingPlaceholderText` för att bekräfta att platshållaren visas korrekt.  

## Slutsats

Du vet nu hur du **add content control in Word document** med Aspose.Words, från att skapa en `DocumentBuilder` till att infoga en vanlig‑text `StructuredDocumentTag`, tilldela en titel och lägga till platshållartext. Det kompletta exemplet kan utökas till andra SDT‑typer, flera kontroller samt avancerade lås‑ eller stylingalternativ.

Redo att gå vidare? Utforska dessa relaterade ämnen:

* **Arbeta med tabeller inuti content controls** – använd `DocumentBuilder.InsertTable` efter SDT:n.  
* **Extrahera data från ifyllda kontroller** – hämta `Sdt`‑noden via titel och läs dess `Text`‑egenskap.  
* **Använda OpenXML SDK** – ett alternativt tillvägagångssätt om du föredrar ett gratis, Microsoft‑stött bibliotek.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Lägg till innehåll med Document Builder i Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/)
- [Infoga inbäddad bild i Word-dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Skapa ett Word-dokument med tabell med Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}