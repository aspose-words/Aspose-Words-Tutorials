---
category: general
date: 2026-04-05
description: Aspose guide för teckensnittssubstitution för att upptäcka saknade teckensnitt
  vid inläsning av ett Word‑dokument. Lär dig att konfigurera teckensnittsinställningar
  och hantera saknade teckensnitt effektivt.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: sv
og_description: Aspose guide för teckensnittssubstitution för att upptäcka saknade
  teckensnitt när du laddar ett Word-dokument. Lär dig att konfigurera teckensnittinställningar
  och hantera saknade teckensnitt effektivt.
og_title: Aspose teckensnittssubstitution – Detektera saknade teckensnitt i Word‑dokument
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose teckensnittssubstitution – Upptäck saknade teckensnitt i Word-dokument
url: /sv/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Upptäck saknade teckensnitt i Word-dokument

Har du någonsin stött på en Word‑fil som ser perfekt ut på en maskin men visar märkliga teckensnittsförändringar på en annan? Det är det klassiska **aspose font substitution**‑problemet, och det betyder vanligtvis att vissa teckensnitt saknas på målsystemet. I den här handledningen visar vi dig, steg‑för‑steg, hur du **upptäcker saknade teckensnitt** när du **läser in ett Word‑dokument**, hur du **konfigurerar teckensnittsinställningar**, och vad du ska göra för att **hantera saknade teckensnitt** på ett smidigt sätt.

Vi går igenom ett komplett, körbart C#‑exempel, förklarar varför varje rad är viktig och visar även konsolutdata du kan förvänta dig. När du är klar kan du identifiera teckensnittssubstitutioner i samma ögonblick som ett dokument läses in – utan gissningar.

## What You’ll Learn

- Hur du aktiverar Aspose.Words diagnostiksamlaren för teckensnittsvarningar.  
- Den exakta koden som behövs för att **ladda ett Word‑dokument** med anpassade **teckensnittsinställningar**.  
- Hur du itererar över `WarningInfo`‑objekt för att lista varje ersatt teckensnitt.  
- Tips för att undertrycka oönskade varningar eller tillhandahålla reservteckensnitt.  
- Ett färdigt exempel du kan kopiera‑klistra in i Visual Studio.

### Prerequisites

- .NET 6.0 eller senare (API‑et fungerar likadant på .NET Framework).  
- Aspose.Words for .NET (NuGet‑paket `Aspose.Words`).  
- En Word‑fil som refererar till ett teckensnitt du inte har installerat (t.ex. `MissingFont.docx`).  

Om du har detta, låt oss dyka ner.

## Step 1 – Enable the Diagnostic Collector (Configure Font Settings)

First things first: Aspose.Words only records font substitution warnings if you tell it to. That’s done by creating a `FontSettings` object and assigning it to a `LoadOptions` instance. Think of this as turning on the “debug lights” for font handling.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Why?**  
Utan ett `FontSettings`‑objekt förblir varningssamlaren tyst, och du får aldrig veta vilka teckensnitt som byttes ut. Genom att initiera det tomt låter vi Aspose använda standard‑systemteckensnitten *och* hålla reda på eventuella substitutioner.

> **Pro tip:** Om du vet att en specifik mapp innehåller företagets teckensnitt, peka `FontSettings` dit med `SetFontsFolder("path")`. Det kan minska antalet varningar om saknade teckensnitt.

## Step 2 – Load the Document with the Configured Options (Load Word Document)

Now that the collector is active, load your `.docx` file using the same `LoadOptions`. This is the moment where Aspose scans the document, looks for every font reference, and decides whether a substitution is needed.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Why does this matter?**  
Om du bara anropar `new Document("MissingFont.docx")` skulle standardinställningarna tillämpas *och* varningslistan förbli tom. Att skicka med `loadOptions` garanterar att diagnostiksamlaren är kopplad till laddningsprocessen.

## Step 3 – Retrieve and Display Font Substitution Warnings (Detect Missing Fonts)

After the document is in memory, Aspose stores any warnings in `document.WarningCallback.Warnings`. Loop through that collection, filter for `WarningType.FontSubstitution`, and print the description. Each description tells you which font was missing and which one was used instead.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Expected console output**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

That output tells you exactly which fonts are missing on the machine running the code. You can now decide whether to install the missing fonts, embed them in the document, or keep the substitution.

![Console output showing aspose font substitution warnings](/images/aspose-font-substitution-console.png)

*Image alt text:* aspose font substitution – console output listing substituted fonts

## Step 4 – Optional: Customize the Substitution Behavior (Handle Missing Fonts)

Sometimes you don’t just want to know *that* a substitution happened—you want to control *how* it happens. Aspose.Words lets you register a custom `IFontSubstitutionRule`. Below is a quick example that forces any missing font to fall back to `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**When would you use this?**  
Om du genererar PDF‑filer för en webbtjänst och vet att alla klienter kan rendera `Tahoma`, garanterar en tvingad reservteckensnitt visuell konsistens utan att behöva distribuera dussintals teckensnittsfiler.

## Full Working Example (All Steps Combined)

Here’s the entire program you can paste into a new console project. It compiles as‑is, assuming you’ve installed the Aspose.Words NuGet package.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Run the program, watch the console, and you’ll see every missing‑font event printed out. From there you can decide whether to install the missing fonts, embed them, or keep the fallback.

## Frequently Asked Questions

**Q: Does this work with PDF conversion?**  
Ja. När du senare anropar `doc.Save("output.pdf")` kommer alla teckensnitt som ersattes under inläsning att vara de som bäddas in i PDF‑filen. Så att fånga varningarna tidigt hjälper dig att undvika oväntade teckensnittsförändringar i den slutgiltiga PDF‑filen.

**Q: What if I have many documents to process?**  
Packa in laddningslogiken i ett try‑catch‑block och återanvänd ett enda `FontSettings`‑objekt för flera dokument. Det minskar overhead och håller varningssamlaren aktiv för varje fil.

**Q: Can I suppress the warnings entirely?**  
Du kan sätta `loadOptions.WarningCallback = null;` innan du laddar, men du förlorar möjligheten att **upptäcka saknade teckensnitt** – vilket vanligtvis inte är önskvärt.

## Conclusion

Vi har gått igenom allt du behöver för att bemästra **aspose font substitution**: aktivera diagnostiksamlaren, ladda ett Word‑dokument med anpassade **teckensnittsinställningar**, extrahera listan över saknade teckensnitt, och till och med åsidosätta standardregeln för att **hantera saknade teckensnitt** på ditt eget sätt. Med bara några rader C# får du full insyn i teckensnittsproblem som annars gömmer sig bakom subtila layoutförändringar.

Nästa steg? Prova att bädda in de ursprungliga teckensnitten i dokumentet med `FontSettings.SetFontsFolder` eller utforska `FontSourceBase` för att ladda teckensnitt från en databas. Du kan också experimentera med `Document.BuiltInStyle`‑samlingen för att se hur stil‑nivå teckensnittsförändringar sprider sig.

Har du fler frågor om Aspose.Words eller teckensnittshantering? Lämna en kommentar, utforska den officiella Aspose‑dokumentationen, eller starta ett nytt projekt och lek med koden ovan. Lycka till med kodningen, och må dina dokument alltid renderas exakt som avsett!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}