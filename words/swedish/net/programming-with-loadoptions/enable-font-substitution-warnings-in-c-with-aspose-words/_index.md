---
category: general
date: 2026-06-20
description: Aktivera varningar för teckensnittssubstitution i C# med Aspose.Words.
  Lär dig hur du konfigurerar LoadOptions, fångar varningar och hanterar saknade teckensnitt
  effektivt.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: sv
og_description: Aktivera varningar för teckensnittssubstitution i C# med Aspose.Words.
  Den här guiden visar hur du konfigurerar LoadOptions, läser WarningInfo och visar
  meddelanden om saknade teckensnitt.
og_title: Aktivera varningar för teckensnittssubstitution i C# – Komplett guide
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Aktivera varningar för teckensnittssubstitution i C# med Aspose.Words
url: /sv/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera varningar för teckensnittssubstitution i C# med Aspose.Words

Har du någonsin undrat hur du **aktiverar varningar för teckensnittssubstitution** när ett Word‑dokument refererar till ett teckensnitt som inte är installerat på servern? Du är inte ensam. Saknade teckensnitt kan tyst förstöra layouten i genererade PDF‑filer eller bilder, och det enda sättet att fånga det tidigt är att lyssna på de varningar som Aspose.Words avger.

I den här handledningen går vi igenom ett praktiskt exempel som visar exakt hur du slår på dessa varningar, hämtar dem från `WarningInfo`‑samlingen och skriver meningsfulla meddelanden till konsolen. I slutet kommer du att veta hur du konfigurerar **Aspose.Words LoadOptions**, hanterar **C# font substitution warnings**, och håller din dokument‑bearbetningspipeline vattentät.

Vi kommer också att beröra några kantfall — vad som händer om du undertrycker varningar, eller om du behöver logga dem istället för att skriva ut dem — och ge dig ett komplett, kopiera‑och‑klistra‑klart kodexempel som fungerar med den senaste Aspose.Words för .NET (från och med version 24.10).

## Vad du behöver

- .NET 6.0 eller senare (koden fungerar också på .NET Framework 4.7+)
- En NuGet‑referens till `Aspose.Words` (installera via `dotnet add package Aspose.Words`)
- En Word‑fil som refererar till ett teckensnitt du **inte** har installerat (t.ex. `DocumentWithMissingFont.docx`)
- En bra IDE (Visual Studio, Rider eller VS Code)

Det är allt — inga extra tjänster, inga proprietära verktyg. Är du redo? Låt oss dyka ner.

## Steg 1: Aktivera varningar för teckensnittssubstitution

Det första du måste göra är att tala om för Aspose.Words att du vill bli underrättad när det ersätter ett saknat teckensnitt. Detta görs via `FontSettings`‑egenskapen på ett `LoadOptions`‑objekt. Som standard är varningar **inaktiverade** för att hålla API‑et tyst, så vi måste slå på dem själva.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Varför detta fungerar:** När `FontSettings` inte är `null` fyller biblioteket automatiskt `Document.WarningInfo` med alla `WarningType.FontSubstitution`‑poster det stöter på när ett dokument laddas. Tänk på det som att slå på ett “debug‑läge” för teckensnitt.

## Steg 2: Ladda dokumentet med konfigurerade alternativ

Nu när varningssamlingen är aktiv, ladda ditt dokument med hjälp av `LoadOptions` som vi just förberedde. Om dokumentet innehåller ett saknat teckensnitt kommer Aspose.Words att ersätta det med ett reservteckensnitt och lägga till en varning i `WarningInfo`‑listan.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Proffstips:** Om du bearbetar många filer i en loop, återanvänd samma `LoadOptions`‑instans — att skapa den en gång sparar några millisekunder per iteration.

## Steg 3: Iterera över WarningInfo och visa meddelanden om teckensnittssubstitution

När dokumentet är laddat innehåller `WarningInfo`‑samlingen alla varningar som inträffade under inläsningen. Vi är bara intresserade av `WarningType.FontSubstitution`, så vi filtrerar därefter.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Att köra kodsnutten ovan mot ett dokument som refererar till det saknade teckensnittet “Papyrus” kan ge en utskrift som:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Det är **teckensnittssubstitutionsmeddelandena** du har letat efter — tydliga, handlingsbara och redo att loggas eller skickas till ett larmsystem.

## Fullständigt fungerande exempel

Nedan är ett fristående konsolprogram som sätter ihop allt. Kopiera‑och‑klistra in det i ett nytt `.csproj` och tryck på **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Förväntad utskrift

Om dokumentet refererar till teckensnitt som inte är installerade kommer du att se något liknande:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Om alla teckensnitt finns på maskinen kommer programmet bara att skriva ut:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Vanliga fallgropar & proffstips

| Issue | Why It Happens | How to Fix / Avoid |
|-------|----------------|--------------------|
| **Varningar försvinner** | Du rensade `FontSettings` eller använde ett `LoadOptions` utan den. | Instansiera alltid `FontSettings` även om du inte ändrar några egenskaper. |
| **För många varningar** | Dokumentet använder många exotiska teckensnitt. | Överväg att lägga till en anpassad teckensnittsmapp till `FontSettings` via `SetFontsFolder` för att minska substitutioner. |
| **Prestandapåverkan i en tight loop** | Att återskapa `LoadOptions` varje iteration ger extra overhead. | Återanvänd en enda `LoadOptions`‑instans för alla dokument. |
| **Saknad konsolutskrift** | Körs i en GUI‑app där `Console.WriteLine` ignoreras. | Ompek varningar till en logger (`ILogger`) eller skriv till en fil. |

### Hantera varningar i en verklig tjänst

I ett webb‑API vill du förmodligen inte skriva till konsolen. Istället, skicka varningarna till en strukturerad logg:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

På så sätt behåller du **hantering av dokumentvarningar** samtidigt som du håller din tjänst ren.

## Utöka exemplet

- **Fånga andra varningstyper** (t.ex. `WarningType.UnknownFileFormat`) genom att ta bort `if`‑filtret.
- **Spara en rapport** över alla varningar till JSON för efterföljande analys.
- **Tvinga ett specifikt reservteckensnitt** genom att sätta `FontSettings.SubstitutionSettings.DefaultFontName`.

Alla dessa är naturliga utökningar när du har bemästrat **aktivera varningar för teckensnittssubstitution**.

## Slutsats

Vi har visat dig hur du **aktiverar varningar för teckensnittssubstitution** i C# med Aspose.Words, från att konfigurera `LoadOptions` till att iterera över `WarningInfo` och skriva ut vänliga meddelanden. Genom att följa stegen ovan kan du skydda dina dokument‑bearbetningspipelines mot tysta layoutförändringar som orsakas av saknade teckensnitt.

Nästa steg, prova att lägga till en anpassad teckensnittsmapp, logga varningarna till en fil, eller till och med skicka dem till en övervakningsdashboard. Samma mönster fungerar för alla **hantering av dokumentvarningar**‑scenarier, oavsett om du konverterar till PDF, renderar bilder eller utför mail‑merge.

Har du frågor om **C# font substitution warnings** eller vill dela med dig av en smart lösning? Lägg en kommentar nedan — lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}