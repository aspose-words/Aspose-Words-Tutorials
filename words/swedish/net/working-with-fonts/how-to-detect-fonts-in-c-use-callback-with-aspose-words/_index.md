---
category: general
date: 2026-03-17
description: Hur man upptäcker teckensnitt i C# med Aspose.Words och en varningsåteruppringning.
  Lär dig hur du använder återuppringning för att fånga ersättningar av saknade teckensnitt
  när du laddar dokument.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: sv
og_description: Hur man upptäcker teckensnitt i C# med Aspose.Words. Denna guide visar
  hur man använder en återuppringning för att fånga varningar om saknade teckensnitt
  när ett dokument laddas.
og_title: Hur man upptäcker typsnitt i C# – Använd återanrop med Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man detekterar teckensnitt i C# – Använd återanrop med Aspose.Words
url: /sv/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

Aspose.Words warning callback". Should translate alt text but keep URL unchanged. Title also.

Also there is a link in the image title attribute. That's fine.

Also there are bullet lists.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så här upptäcker du teckensnitt i C# – Använd callback med Aspose.Words

Har du någonsin behövt **hur man upptäcker teckensnitt** i ett Word‑dokument programmässigt och undrat varför vissa tecken ser konstiga ut efter konvertering? Du är inte ensam. I många verkliga projekt—fakturageneratorer, rapportexportörer eller batch‑processeringspipeline—orsakar saknade teckensnitt tysta layout‑buggar som är svåra att felsöka.  

Den goda nyheten? Aspose.Words ger dig ett rent sätt att visa dessa problem med en varnings‑callback. I den här handledningen kommer du att se **hur du använder en callback** för att fånga varje teckensnittssubstitution som Aspose utför när ett dokument laddas, och du får ett färdigt exempel som skriver ut en tydlig rapport om saknade teckensnitt.

Vi går igenom:

* De minimala förutsättningarna (ett .NET‑projekt och Aspose.Words‑NuGet‑paketet).  
* Hur du implementerar `IWarningCallback` för att lyssna på `WarningType.FontSubstitution`.  
* Hur du kopplar callbacken till `LoadOptions` och laddar ett dokument.  
* Hur utdata ser ut, samt några praktiska tips för produktionskod.

När du är klar kan du automatiskt **upptäcka teckensnitt** i vilken DOCX-, DOC- eller RTF‑fil som helst och agera på information om saknade teckensnitt—oavsett om det innebär loggning, avisering av en användare eller att ersätta med ett reservteckensnitt.

---

![Hur man upptäcker teckensnitt i ett Word‑dokument med Aspose.Words varnings‑callback](https://example.com/images/detect-fonts.png "hur man upptäcker teckensnitt i ett Word‑dokument")

## Vad du behöver

* **.NET 6.0** eller senare (exemplet kompileras även med .NET Framework 4.6+).  
* **Aspose.Words for .NET** – installera via NuGet: `Install-Package Aspose.Words`.  
* En exempel‑Word‑fil som medvetet refererar ett teckensnitt du inte har installerat (t.ex. `MissingFont.docx`).  

Inga ytterligare bibliotek krävs; allt finns i Aspose‑namnutrymmet.

---

## Så här upptäcker du teckensnitt med en varnings‑callback

### Steg 1: Skapa en varnings‑callback‑klass

Callbacken implementerar `IWarningCallback`. När Aspose.Words stöter på ett teckensnitt som den inte kan hitta, höjer den ett `WarningInfo` med `WarningType.FontSubstitution`. Vår klass skriver helt enkelt en vänlig rad till konsolen.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Varför detta är viktigt:** Genom att filtrera på `WarningType.FontSubstitution` undviker vi brusiga varningar (som föråldrade funktioner) och håller loggen fokuserad på det exakta problemet du försöker lösa—**att upptäcka teckensnitt** som saknas på maskinen.

---

### Steg 2: Koppla callbacken till `LoadOptions`

`LoadOptions` låter dig anpassa hur ett dokument parsas. Genom att tilldela vår `FontWarningCollector` till egenskapen `WarningCallback` talar du om för Aspose att anropa den varje gång ett saknat teckensnitt påträffas.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tips:** Du kan också sätta `LoadOptions.FontSettings` här om du vill tillhandahålla ett reservteckensnitt programmässigt. Det är ett avancerat scenario som vi nämner senare.

---

### Steg 3: Ladda dokumentet och observera utdata

Nu laddar vi faktiskt filen. Så snart Aspose parsar dokumentet triggar varje teckensnitt den inte kan hitta vår callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Förväntad konsolutskrift** (förutsatt att dokumentet refererar *Comic Sans MS* som inte är installerat):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Om dokumentet innehåller flera saknade teckensnitt ser du en rad per teckensnitt—precis den **hur man upptäcker teckensnitt**‑information du behöver.

---

## Så här använder du callback för mer komplexa scenarier

### Logga till en fil istället för konsolen

I produktion vill du förmodligen ha en bestående logg. Byt ut `Console.WriteLine` mot en `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Samla varningar för senare analys

Ibland behöver du listan över saknade teckensnitt efter att dokumentet har laddats, kanske för att visa en UI‑dialog. Lagra varningarna i en `List<string>` och exponera den:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Tillhandahålla ett reservteckensnitt programmässigt

Om du har ett företags‑teckensnitt du vill tvinga fram, kan du lägga till det i `FontSettings` innan du laddar:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Nu ersätter Aspose saknade teckensnitt med *Arial Unicode MS* samtidigt som den rapporterar substitutionen via callbacken. Detta är ett smidigt sätt att **hur man använder callback** för både upptäckt och automatisk åtgärd.

---

## Vanliga fallgropar och pro‑tips

| Fallgrop | Varför det händer | Hur du undviker det |
|----------|-------------------|----------------------|
| **Glömmer att referera `Aspose.Words.Warnings`** | `IWarningCallback`‑gränssnittet finns där. | Lägg till `using Aspose.Words.Warnings;` högst upp. |
| **Laddar ett dokument utan `LoadOptions`** | Standardladdaren ersätter tyst teckensnitt utan någon notifikation. | Skapa alltid en `LoadOptions`‑instans och tilldela din callback. |
| **Kör på en server med begränsade rättigheter** | Skrivning till en loggfil kan kasta `UnauthorizedAccessException`. | Använd en skrivbar mapp (t.ex. appens datakatalog) eller håll dig till minnes‑samlingar. |
| **Flera trådar delar samma collector** | `FontWarningCollector` är inte trådsäker som standard. | Skapa en separat collector per tråd eller skydda listan med en lås. |
| **Förutsätter att callbacken avfyras för inbäddade teckensnitt** | Inbäddade teckensnitt finns redan i dokumentet; ingen varning ges. | Om du vill verifiera integriteten hos inbäddade teckensnitt, inspektera `FontInfo` via `FontSettings`. |

---

## Fullt fungerande exempel (Kopiera‑klistra‑klart)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Vad du bör se** (förutsatt att filen refererar två frånvarande teckensnitt):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Om filen bara använder installerade teckensnitt skriver konsolen bara:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Avslutning

Vi har gått igenom **hur man upptäcker teckensnitt** i ett Word‑dokument genom att koppla en anpassad varnings‑callback till Aspose.Words. Metoden är lättviktig, kräver

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}