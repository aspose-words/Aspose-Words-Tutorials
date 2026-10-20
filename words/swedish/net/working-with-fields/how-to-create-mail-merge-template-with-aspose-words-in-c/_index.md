---
category: general
date: 2026-10-20
description: Lär dig hur du skapar en mailmerge‑mall, laddar en Word‑mall och slår
  ihop data i Word med Aspose.Words LowCode. Automatisera dokumentgenerering på några
  minuter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create mail merge template
- load word template
- merge data into word
- automate document generation
- populate word template
language: sv
lastmod: 2026-10-20
og_description: Skapa mall för kopplad utskick, ladda Word-mall och slå samman data
  i Word med Aspise.Words LowCode. Denna guide visar hur du snabbt automatiserar dokumentgenerering.
og_image_alt: Screenshot of a C# program that creates a mail merge template using
  Aspose.Words
og_title: Skapa en mailmerge‑mall i C# med Aspose.Words – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create mail merge template, load word template, and merge
    data into word using Aspose.Words LowCode. Automate document generation in minutes.
  headline: How to create mail merge template with Aspose.Words in C#
  type: TechArticle
- description: Learn how to create mail merge template, load word template, and merge
    data into word using Aspose.Words LowCode. Automate document generation in minutes.
  name: How to create mail merge template with Aspose.Words in C#
  steps:
  - name: '**Field mapping** – `MailMerger` maps each property to its corresponding
      `«FieldName»`.'
    text: '**Field mapping** – `MailMerger` maps each property to its corresponding
      `«FieldName»`.'
  - name: '**Record iteration** – For every object in `mailMergeData`, a copy of the
      template is generated.'
    text: '**Record iteration** – For every object in `mailMergeData`, a copy of the
      template is generated.'
  - name: '**Document concatenation** – All copies are combined into a single `Document`
      instance, preserving page breaks.'
    text: '**Document concatenation** – All copies are combined into a single `Document`
      instance, preserving page breaks.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
title: Hur man skapar en mailmerge‑mall med Aspose.Words i C#
url: /sv/net/working-with-fields/how-to-create-mail-merge-template-with-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar mail merge‑mall med Aspose.Words i C#

Om du behöver **create mail merge template** för personliga brev, fakturor eller certifikat, visar den här guiden de exakta stegen. Du kommer att lära dig hur du **load word template**, **merge data into word**, och **automate document generation** så att du kan **populate word template** utan manuell kopiering‑och‑klistring.

Dokumentautomatisering är ett vanligt krav i affärsapplikationer, men många utvecklare börjar från början varje gång. I slutet av den här handledningen kommer du att ha en återanvändbar C#‑metod som tar en samling objekt, slår ihop dem i en Word‑fil och sparar resultatet – allt med några få kodrader.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
- Visual Studio 2022 eller någon IDE som stödjer C#
- En Aspose.Words‑licens (eller en tillfällig utvärderingsnyckel)
- Grundläggande kunskap om C#‑anonyma typer

> **Pro tip:** Om du planerar att köra detta på en server, lagra licensen på en säker plats och läs in den en gång vid applikationens start.

## Steg 1: Skapa mail merge‑mallen

Den första uppgiften är att designa ett Word‑dokument som innehåller sammanslagningsfält. I Aspose.Words skrivs ett sammanslagningsfält som `«FieldName»`. Öppna Microsoft Word, infoga en tabell eller ett stycke och lägg till fält för de data du planerar att slå ihop, till exempel:

```
Dear «Name»,

Your order number «OrderId» has been processed.

Thank you,
Acme Corp.
```

Spara den här filen som `MailMergeTemplate.docx` i en mapp som du kan referera till från koden, t.ex. `C:\Docs\Templates`.

> **Why this matters:** En välstrukturerad mall separerar layout från data, vilket gör att du kan återanvända samma fil för tusentals poster utan att röra designen igen.

## Steg 2: Läs in word‑mallen i C#

Nu läser vi in mallen i minnet. Aspose.Words `Document`‑klass läser `.docx`‑filen och ger dig full programmatisk åtkomst.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;   // hypothetical namespace for LowCode classes

// Load the mail‑merge template document
Document template = new Document(@"C:\Docs\Templates\MailMergeTemplate.docx");
```

- **load word template** – `Document`‑konstruktorn gör det tunga arbetet: den parsar OpenXML‑paketet, validerar strukturen och förbereder ett DOM‑liknande objektmodell.
- **Error handling:** Omge inläsningen med ett `try / catch`‑block för att hantera saknade filer eller korrupta mallar.

```csharp
try
{
    Document template = new Document(@"C:\Docs\Templates\MailMergeTemplate.docx");
}
catch (FileNotFoundException ex)
{
    Console.Error.WriteLine($"Template not found: {ex.Message}");
    return;
}
```

## Steg 3: Förbered datakällan

Aspose.Words kan slå ihop data från vilken `IEnumerable` som helst. Här använder vi en array av anonyma objekt, men du kan också skicka en `DataTable`, `DataSet` eller en anpassad POCO‑samling.

```csharp
// Prepare the data source that will be merged into the template
var mailMergeData = new[]
{
    new { Name = "Alice",   OrderId = 101 },
    new { Name = "Bob",     OrderId = 102 },
    new { Name = "Charlie", OrderId = 103 }
};
```

- **merge data into word** – Egenskapsnamnen (`Name`, `OrderId`) måste matcha sammanslagningsfältnamnen i mallen.
- **Edge case:** Om ett fält saknas i datakällan lämnar Aspose.Words platshållaren oförändrad. Du kan upptäcka detta senare med `Document.Range.Fields`.

## Steg 4: Utför mail merge

`MailMerger`‑klassen (del av low‑code‑API:t) förenklar sammanslagningsoperationen. Den itererar automatiskt över samlingen och skapar ett separat dokument för varje post, och sammanfogar dem sedan.

```csharp
// Create a MailMerger instance using the template
MailMerger merger = new MailMerger(template);

// Execute the mail merge with the prepared data
Document mergedDocument = merger.Execute(mailMergeData);
```

### Vad händer under huven?

1. **Field mapping** – `MailMerger` mappar varje egenskap till motsvarande `«FieldName»`.
2. **Record iteration** – För varje objekt i `mailMergeData` genereras en kopia av mallen.
3. **Document concatenation** – Alla kopior kombineras till en enda `Document`‑instans, med sidbrytningar bevarade.

Om du behöver en utdatafil per post istället för en kombinerad fil, anropa `merger.ExecuteToSeparateFiles(mailMergeData, outputFolder)` (hypotetisk överlagring).

## Steg 5: Spara det resulterande dokumentet

Slutligen skriver du det sammanslagna dokumentet till disk. Du kan välja vilket som helst av de stödjade formaten (`.docx`, `.pdf`, `.html`, etc.).

```csharp
// Save the resulting document to a new file
mergedDocument.Save(@"C:\Docs\Results\MailMergeResult.docx");
Console.WriteLine("Mail merge completed successfully.");
```

- **populate word template** – `Save`‑metoden skriver det fullständigt ifyllda dokumentet, redo för distribution.
- **Automation tip:** Om du behöver skicka filen via e‑post kan du strömma `mergedDocument` direkt till en bilaga utan att skriva till filsystemet.

## Fullt fungerande exempel

När allt sätts ihop, här är en fristående konsolapplikation som du kan kopiera‑och‑klistra in i ett nytt C#‑projekt.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LowCode;   // hypothetical LowCode namespace

namespace MailMergeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word template
            const string templatePath = @"C:\Docs\Templates\MailMergeTemplate.docx";
            Document template;
            try
            {
                template = new Document(templatePath);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to load template: {ex.Message}");
                return;
            }

            // 2️⃣ Prepare data to merge
            var mailMergeData = new[]
            {
                new { Name = "Alice",   OrderId = 101 },
                new { Name = "Bob",     OrderId = 102 },
                new { Name = "Charlie", OrderId = 103 }
            };

            // 3️⃣ Perform the merge
            MailMerger merger = new MailMerger(template);
            Document mergedDocument = merger.Execute(mailMergeData);

            // 4️⃣ Save the merged result
            const string outputPath = @"C:\Docs\Results\MailMergeResult.docx";
            try
            {
                mergedDocument.Save(outputPath);
                Console.WriteLine($"Merged document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to save merged document: {ex.Message}");
            }
        }
    }
}
```

### Förväntad utdata

När du öppnar `MailMergeResult.docx` bör du se tre sidor – en för varje post – formaterade exakt som mallen, med platshållarna ersatta:

```
Page 1
Dear Alice,
Your order number 101 has been processed.

Page 2
Dear Bob,
Your order number 102 has been processed.

Page 3
Dear Charlie,
Your order number 103 has been processed.
```

## Hantera vanliga variationer

| Scenario | Recommended approach |
|----------|----------------------|
| **Stort dataset (10 000+ rader)** | Använd `MailMerger.ExecuteToSeparateFiles` för att undvika massiv in‑memory‑konkatenering, eller strömma sidor till en PDF i realtid. |
| **Villkorligt innehåll** | Placera `IF`‑fält i mallen (`«If:HasDiscount»Discount applied«EndIf»`) och aktivera `MailMerger`‑s villkorliga logikflagga. |
| **Annat utdataformat** | Anropa `mergedDocument.Save("result.pdf")` för att skapa en PDF; Aspose.Words konverterar layouten automatiskt. |
| **Anpassad fältformatering** | Implementera `IMailMergeFieldFormatter` (hypotetisk) för att formatera datum, valutor eller tillämpa kulturspecifika regler. |

## Bästa praxis för robust mail merge‑automatisering

- **Validate the data source** before merging. Saknade fält leder till tomma platshållare.
- **Lock the template** (read‑only file attribute) för att förhindra oavsiktliga redigeringar i produktion.
- **Version the template** med versionskontroll så att du kan spåra layoutändringar.
- **Dispose objects** (`Document` implements `IDisposable` in newer versions) för att snabbt frigöra inhemska resurser.
- **Test with edge cases** såsom mycket långa namn, specialtecken eller null‑värden för att säkerställa att det genererade dokumentet förblir välformaterat.

## Slutsats

Du vet nu hur du **create mail merge template**, **load word template**, **merge data into word**, och **automate document generation** för att **populate word template** med Aspose.Words LowCode i C#. Det kompletta exemplet demonstrerar ett produktionsklart arbetsflöde som du kan anpassa till fakturor, certifikat eller vilket personligt dokumentscenario som helst.

Nästa steg kan du utforska:

- **Generating PDFs** från det sammanslagna dokumentet (`mergedDocument.Save("result.pdf")`) – en naturlig fortsättning på *automate document generation*.
- **Integrating with a web API** för att ta emot JSON‑payloads och returnera

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Flytta till sammanslagningsfält i Word‑dokument](/words/english/net/add-content-using-documentbuilder/move-to-merge-field/)
- [Skapa Word‑dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Skapa formaterad tabell i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-table-styles-and-formatting/create-table-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}