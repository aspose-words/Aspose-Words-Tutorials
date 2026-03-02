---
category: general
date: 2026-03-01
description: Maak FontSettings in C# om ontbrekende lettertypen te detecteren, lettertype‑berichten
  vast te leggen en ontbrekende lettertypen af te handelen met Aspose.Words. Stapsgewijze
  handleiding voor ontwikkelaars.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: nl
og_description: Maak FontSettings in C# om ontbrekende lettertypen te detecteren,
  lettertypeberichten vast te leggen en ontbrekende lettertypen af te handelen met
  Aspose.Words. Complete tutorial met code.
og_title: Maak FontSettings in C# – Detecteer ontbrekende lettertypen & Leg lettertypeberichten
  vast
tags:
- Aspose.Words
- C#
- Font Management
title: FontSettings maken in C# – Detecteer ontbrekende lettertypen & Leg lettertypeberichten
  vast
url: /nl/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# FontSettings maken in C# – Ontbrekende lettertypen detecteren & lettertype‑meldingen vastleggen

Heb je ooit **FontSettings** moeten **maken** in een .NET‑project, maar wist je niet hoe je lettertypen kunt opsporen die niet op de doelmachine zijn geïnstalleerd? Je bent niet de enige. In veel real‑world apps—denk aan geautomatiseerde rapportgeneratoren of documentconverters—kunnen ontbrekende lettertypen stilletjes de lay‑out breken, en merk je het pas als de PDF er vreemd uitziet.  

Wat als je **ontbrekende lettertypen kunt detecteren**, **lettertype‑meldingen kunt vastleggen**, en **ontbrekende lettertypen kunt afhandelen** voordat ze je output verpesten? Het goede nieuws is dat Aspose.Words dit kinderspel maakt. In deze tutorial lopen we het volledige proces door, van het instellen van het `FontSettings`‑object tot het koppelen van een waarschuwing‑callback die je precies vertelt welke glyphs zijn vervangen.

> **TL;DR:** Aan het einde heb je een kant‑klaar C#‑console‑applicatie die elke lettertype‑substitutie logt, zodat je kunt beslissen of je een vervanging wilt insluiten of de gebruiker wilt waarschuwen.

---

## Prerequisites

- .NET 6 SDK (of een recente .NET‑versie)  
- Visual Studio 2022 of VS Code met C#‑extensies  
- Een Aspose.Words for .NET‑licentie (gratis proefversie werkt voor deze demo)  
- Een voorbeeld‑DOCX die een lettertype refereert dat je niet geïnstalleerd hebt (bijv. *Comic Sans MS* op een Linux‑machine)  

Er zijn geen speciale NuGet‑pakketten nodig naast `Aspose.Words`.

---

## Step 1 – Install Aspose.Words and Set Up the Project

First things first, create a new console project and bring the Aspose.Words library into the mix.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Als je al een oplossing hebt, voeg het pakket dan toe via de NuGet Package Manager UI—dat maakt versie‑tracking makkelijker.

---

## Step 2 – Create FontSettings (Primary Keyword Appears Here)

The **create FontSettings** step is the cornerstone of any font‑related workflow. `FontSettings` tells Aspose.Words where to look for fonts, whether to use system folders, and how to fall back when something is missing.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Waarom is dit belangrijk? Zonder een goed geconfigureerde `FontSettings` vervangt de engine stilletjes ontbrekende glyphs door het standaard‑systeemlettertype, en zie je nooit een waarschuwing.

---

## Step 3 – Wire Up LoadOptions with the FontSettings

`LoadOptions` lets you pass the `FontSettings` into the document loader. This is the bridge that lets the engine **detect missing fonts** during the `Document` construction phase.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Nu zal elke keer dat je een DOCX laadt met `loadOptions`, Aspose.Words de `FontSettings` raadplegen die we eerder hebben ingesteld.

---

## Step 4 – Attach a Warning Callback to **Capture Font Messages**

Aspose.Words emits warnings for a variety of conditions—font substitution being a common one. By providing an implementation of `IWarningCallback`, you can **capture font messages** in real time.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### The Warning Handler Class

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Het veld `info.Description` bevat een mens‑leesbare melding zoals *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Dit is precies het soort output dat je nodig hebt om **ontbrekende lettertypen** op een nette manier af te handelen.

---

## Step 5 – Load the Document and Let the Callback Do Its Job

With everything wired, loading the document is straightforward. If the source file references a font absent from the system, our warning handler will fire.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Wanneer je het programma uitvoert, zie je console‑output vergelijkbaar met:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Die output is het **capture font messages**‑deel van onze workflow. Je kunt de handler uitbreiden om naar een bestand te loggen, telemetrie te sturen, of zelfs de conversie af te breken als kritieke lettertypen ontbreken.

---

## Step 6 – Full Working Example (All Pieces Together)

Below is a complete, copy‑paste‑ready program. Paste it into `Program.cs`, adjust the file paths, and hit `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Expected Output

Running the program on a machine that lacks *Comic Sans MS* will print something like:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Je krijgt ook een `Result.pdf` die de vervangen lettertypen gebruikt, waardoor de conversie nooit crasht.

---

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if I want the conversion to fail instead of substituting?** | Inside `FontSubstitutionWarningHandler`, throw an exception when `info.Description` contains a critical font name. |
| **Can I embed a replacement font automatically?** | Yes. After detecting a missing font, you can load a fallback `FontInfo` from a known path and add it to `fontSettings` via `fontSettings.SetFontsFolder`. |
| **Does this work on Linux/macOS?** | Absolutely. `FontSettings` works cross‑platform; just make sure the fallback folder contains the appropriate `.ttf` or `.otf` files. |
| **Is the warning callback thread‑safe?** | The callback runs on the same thread that loads the document, so you don’t need extra synchronization for console logging. For multi‑threaded scenarios, guard shared resources. |
| **How do I log warnings to a file?** | Replace `Console.WriteLine` with `File.AppendAllText("font_warnings.log", ...)` or use any logging framework (Serilog, NLog). |

---

## Pro Tips for Production‑Ready Font Handling

1. **Cache Font Lookups** – Re‑using the same `FontSettings` instance across multiple document loads avoids repeated filesystem scans.  
2. **Whitelist Critical Fonts** – If your brand requires a specific font, verify its presence early and abort with a clear error message.  
3. **Use `SetFontFolder` Recursively** – Setting `recursive: true` ensures subfolders are scanned, which is handy when you ship a whole font collection.  
4. **Combine with `FontSubstitutionSettings`** – You can fine‑tune substitution rules (e.g., prefer fonts with the same family name).  

---

## Conclusion

We’ve just **created FontSettings**, configured `LoadOptions` to **detect missing fonts**, attached a callback that **captures font messages**, and demonstrated how to **handle missing fonts** in a clean, production‑ready way. The entire flow fits into a few dozen lines of C#, yet it gives you full visibility into the font landscape of any DOCX you process.

Next, you might explore:

- **Embedding fallback fonts** directly into the output PDF (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** based on corporate branding rules.  
- **Integrating with a CI pipeline** to automatically flag documents that use unauthorized fonts.

Give it a spin, tweak the warning handler to suit your needs, and let your document pipelines run with confidence—no more mysterious layout glitches caused by invisible font swaps.

Veel plezier met coderen! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}