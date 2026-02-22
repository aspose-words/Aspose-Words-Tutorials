---
category: general
date: 2026-02-21
description: Lär dig hur du aktiverar varningar, upptäcker saknade teckensnitt och
  hur du laddar docx säkert med Aspose.Words i C#. Följ den steg‑för‑steg‑guiden.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: sv
og_description: Hur man aktiverar varningar, upptäcker saknade typsnitt och korrekt
  laddar docx-filer med Aspose.Words. Komplett kodexempel inkluderat.
og_title: Hur man aktiverar varningar och upptäcker saknade teckensnitt när man laddar
  DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Hur man aktiverar varningar och upptäcker saknade teckensnitt när man laddar
  DOCX-filer
url: /sv/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

, preserving formatting.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to enable warnings and detect missing fonts when loading DOCX files

Har du någonsin undrat **how to enable warnings** för saknade teckensnitt innan de tyst förstör din dokumentrendering? Du är inte ensam—de flesta utvecklare antar att biblioteket bara “gör det rätta”, bara för att senare upptäcka att ett teckensnitt byttes ut utan någon ledtråd.  

I den här handledningen visar vi dig exakt **how to enable warnings**, hur man **detect missing fonts**, och det korrekta sättet **how to load docx** med Aspose.Words för .NET. I slutet har du ett färdigt exempel som skriver ut varje varning om teckensnittssubstitution till konsolen, så att du aldrig behöver gissa vad som hände i filen.

## Prerequisites

- .NET 6.0 eller senare (koden fungerar även på .NET Framework 4.7+)  
- Visual Studio 2022 eller någon C#‑IDE du föredrar  
- **Aspose.Words**‑paketet från NuGet (`Install-Package Aspose.Words`)  
- En DOCX‑fil som kan innehålla teckensnitt som inte är installerade på din maskin (vi kallar den `input.docx`)

> **Pro tip:** Om du inte har en testfil, öppna bara ett Word‑dokument som använder ett anpassat företags‑teckensnitt och spara det som `input.docx`. Det kommer att utlösa varningen vi vill fånga.

## Overview of the solution

1. **Create** ett `LoadOptions`‑objekt med `FontSubstitutionWarnings` aktiverat.  
2. **Load** DOCX‑filen med de alternativen.  
3. **Inspect** `WarningCallback`‑samlingen för eventuella `FontSubstitution`‑poster.  
4. **React** – du kan logga, visa eller till och med ersätta det saknade teckensnittet programatiskt.

Nedan bryter vi ner varje steg, förklarar *varför* det är viktigt, och ger dig ett komplett, körbart kodexempel.

---

## Step 1: Install Aspose.Words and set up the project

Innan vi kan **how to enable warnings**, behöver vi biblioteket som faktiskt stödjer dem.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Eller, i Visual Studio Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Why this step?**  
> Utan paketet finns inte `LoadOptions`, `Document` och varningsinfrastrukturen. Att lägga till NuGet‑referensen säkerställer att du hämtar den senaste stabila versionen (vid skrivande stund, 24.5).

## Step 2: Create load options that enable font‑substitution warnings

Kärnan i **how to enable warnings** finns i `LoadOptions`‑klassen. Genom att sätta `FontSubstitutionWarnings` till `true` talar du om för motorn att registrera varje gång den måste ersätta ett saknat teckensnitt.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Why enable this flag?**  
> Som standard byter Aspose.Words tyst ut saknade teckensnitt mot ett reservteckensnitt (vanligtvis Arial). Det kan leda till layoutförändringar, osynliga tecken eller varumärkesbrott. Att slå på flaggan ger dig full insyn.

## Step 3: Load the DOCX file using the configured options

Nu när vi vet **how to load docx** med varningar påslagna, utför vi själva laddningen.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **What happens under the hood?**  
> När DOCX‑filen parsas kontrollerar Aspose.Words varje `<w:rFonts>`‑element. Om det angivna teckensnittet inte är installerat registreras en `FontSubstitution`‑varning och ett reservteckensnitt används. Eftersom vi har aktiverat varningar hamnar dessa poster i `document.WarningCallback.Warnings`.

## Step 4: Retrieve and display font substitution warnings

`WarningCallback`‑egenskapen innehåller en `WarningInfoCollection`. Loopa igenom den, filtrera på `WarningType.FontSubstitution` och skriv ut meddelandena.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Expected output** (example):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **What to do with these messages?**  
> Du kan logga dem till en fil, visa dem i ett UI eller till och med trigga en anpassad teckensnittsfallback‑rutin. Nyckeln är att du nu *detect missing fonts* istället för att gissa senare.

## Step 5: (Optional) Replace missing fonts with a specific fallback

Om du har ett företags‑teckensnitt som du vill tvinga igenom, kan du hantera varningarna och ersätta dem i farten.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Why consider this?**  
> Det garanterar visuell konsistens i alla genererade dokument, vilket är avgörande för varumärkesöverensstämmelse.

## Full, runnable example

Nedan är en enda C#‑fil som du kan kopiera‑klistra in i en konsolapp. Den täcker allt—från att installera paketet till att skriva ut varningar.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Run it**: `dotnet run` från projektmappen. Om några teckensnitt saknas ser du varningarna skrivas ut, och den valfria ersättningen kommer att tillämpas innan filen sparas.

## Frequently asked questions

### Does this work with PDF conversion too?

Ja. Efter att du har hanterat varningarna kan du anropa `doc.Save("output.pdf")` så visas de ersatta teckensnitten i PDF‑filen precis som i DOCX.

### What if I need to suppress warnings for a specific font?

Du kan filtrera bort dem i loopen—hoppa bara över `WarningInfo` vars `Message` innehåller teckensnittets namn du vill ignorera.

### Is `FontSubstitutionWarnings` available in older Aspose.Words versions?

Den introducerades i version 20.5. Om du sitter fast på en äldre version, uppgradera via NuGet; API‑ändringen är bakåtkompatibel.

## Conclusion

Vi har gått igenom **how to enable warnings**, visat dig **detect missing fonts**, och demonstrerat det korrekta sättet **how to load docx** med Aspose.Words samtidigt som du behåller full insyn i teckensnittssubstitutioner. Genom att inspektera `document.WarningCallback.Warnings` får du en pålitlig revisionsspårning—inga fler tysta ersättningar.

Nästa steg? Försök att koppla varningslogiken till ett loggningsramverk som Serilog, eller bygg ett UI som markerar saknade teckensnitt innan du levererar dokumentet till användare. Du kan också utforska `FontSettings`‑klassen för mer detaljerad kontroll över teckensnittssubstitutionspolicyer.

Lycka till med kodningen, och må dina dokument alltid renderas exakt som du tänkt! 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}