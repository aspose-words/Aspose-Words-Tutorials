---
category: general
date: 2026-09-21
description: Lär dig hur du genererar dokumentmall, fyller i Word-mallen och ersätter
  platshållare i en DOCX‑fil med C# – steg‑för‑steg‑guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: sv
lastmod: 2026-09-21
og_description: Generera dokumentmall i C# genom att fylla i en Word‑mall, ersätta
  platshållare och spara en ifylld DOCX‑fil. Följ den här kompletta guiden.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Skapa dokumentmall i C# – fyll DOCX-filer med data
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: Hur man genererar en dokumentmall och fyller den med data i C#
url: /sv/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man genererar dokumentmall och fyller den med data i C#

Om du behöver **generate document template**-filer som kan återanvändas för fakturor, kontrakt eller rapporter, visar den här guiden exakt hur. Du kommer att lära dig att **populate word template**-platshållare, ersätta dem med riktiga värden, och slutligen **fill docx template**-filer programatiskt.

Att skapa en återanvändbar mall eliminerar manuellt kopierande och säkerställer konsekvens i alla genererade dokument. Stegen nedan fungerar med vilken `.docx`-fil som helst som innehåller enkla platshållartoken som `{{Name}}`.

## Förutsättningar

* .NET 6.0 SDK eller senare installerat  
* Visual Studio 2022 (eller någon IDE du föredrar)  
* **Aspose.Words for .NET** NuGet-paketet – det tillhandahåller `Document`-klassen som används i exemplet  

Du kan lägga till paketet med följande kommando:

```bash
dotnet add package Aspose.Words
```

## Steg 1: Förbered Word-mallen

Skapa ett Word-dokument (`Template.docx`) som innehåller platshållare där dynamisk data ska visas. En vanlig konvention är dubbla måsvingar:

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Spara filen i en mapp som du kan referera till från koden, till exempel `C:\Docs\Template.docx`.

## Steg 2: Ladda mall-dokumentet

Den första programatiska åtgärden är att ladda mallen i minnet. `Document`-konstruktorn läser filen och bygger en objektmodell som du kan manipulera.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Varför detta är viktigt:** Att ladda filen skapar en ren kopia varje gång, så den ursprungliga mallen förblir orörd för framtida körningar.

## Steg 3: Ersätt platshållare med faktiska data

Aspose.Words tillhandahåller en enkel `Range.Replace`-metod som skannar dokumentet efter en specifik sträng och ersätter den. Wrappa anropet i en hjälpfunktion för att hålla huvudflödet prydligt.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**Hur det fungerar:** `Range.Replace` går igenom varje stycke, tabellcell, sidhuvud och sidfot, och säkerställer att alla förekomster av token uppdateras. Detta är det mest pålitliga sättet att **how to replace placeholder**-text i en DOCX-fil.

### Hantera flera förekomster och saknade token

* Om en platshållare visas mer än en gång, uppdaterar `Replace` automatiskt alla instanser.  
* Om en platshållare saknas, gör metoden helt enkelt ingenting – inget undantag kastas.  
* För stora dokument kan du förbättra prestandan genom att inaktivera `doc.UpdateFields()` tills alla ersättningar är klara.

## Steg 4: Spara det ifyllda dokumentet

När alla platshållare har ersatts, skriv resultatet till en ny fil. Att hålla utdata separat bevarar den ursprungliga mallen för framtida körningar.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultat:** `FilledTemplate.docx` innehåller nu det personliga innehållet:

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Steg 5: Verifiera utdata (valfritt)

Om du vill programatiskt bekräfta att ersättningarna lyckades, kan du läsa den sparade filen igen och söka efter de förväntade värdena:

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

Att köra verifieringssteget skriver ut `true` när platshållaren har ersatts korrekt.

## Vanliga fallgropar och bästa‑praxis‑tips

| Problem | Varför det händer | Rekommenderad åtgärd |
|-------|----------------|-----------------|
| **Platshållare innehåller extra mellanslag** | `"{{ Name }}"` matchar inte `"{{Name}}"`. | Håll platshållartoken utan mellanslag, eller trimma båda sidor innan ersättning. |
| **Word lägger till dold formatering** | Word kan lagra platshållaren uppdelad i flera körningar, vilket får `Replace` att missa den. | Använd `Document.Range.Replace` med `FindReplaceOptions` satt till `MatchCase = false` och `FindWholeWordsOnly = false`. |
| **Stora dokument orsakar långsamhet** | Att ersätta token en åt gången triggar en fullständig dokumentsökning varje gång. | Gör batch-ersättningar i ett enda pass genom att anropa `Range.Replace` för varje token innan du sparar. |
| **Spara till en skrivskyddad mapp** | `doc.Save` kastar ett `UnauthorizedAccessException`. | Säkerställ att målkatalogen har skrivrättigheter, eller välj en användarskrivbar sökväg (t.ex. `%TEMP%`). |

## Fullt fungerande exempel

Nedan är det kompletta, fristående programmet som du kan kopiera, klistra in och köra.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Förväntad konsolutmatning**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Öppna `FilledTemplate.docx` i Microsoft Word för att se den personliga texten.

## Slutsats

Du vet nu hur du **generate document template**, **populate word template**, och **fill docx template**-filer genom att **how to replace placeholder**-token med riktiga data. Metoden fungerar för valfritt antal platshållare och skalar till stora dokument när du följer bästa‑praxis‑tipsen.

### Vad blir nästa?

* **Dynamiska tabeller:** Använd `DocumentBuilder` för att infoga rader baserat på samlingar.  
* **Villkorliga sektioner:** Dölj eller visa delar av mallen med `IF`-fält.  
* **PDF-export:** Anropa `doc.Save("output.pdf")` för att skapa en PDF-version av det ifyllda dokumentet.  

Experimentera med dessa variationer för att bygga en fullutrustad dokumentgenereringsmotor för fakturor, kontrakt eller vilken återkommande rapport som helst.

---


## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Word-dokument - Hitta och ersätt text](/words/english/net/find-and-replace-text/)
- [Generera Word-dokument](/words/english/java/word-processing/generate-word-document/)
- [Återställ korrupt DOCX – Öppna & läs Word-dokument](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}