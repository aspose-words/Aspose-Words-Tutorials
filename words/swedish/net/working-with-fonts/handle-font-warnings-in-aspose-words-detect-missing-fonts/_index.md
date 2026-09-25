---
category: general
date: 2026-02-28
description: Lär dig hur du hanterar teckensnittsvarningar och upptäcker saknade teckensnitt
  i Aspose.Words med C#. Komplett steg‑för‑steg‑guide med fullständig kod.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: sv
og_description: Hantera teckensnittsvarningar i Aspose.Words och upptäck saknade teckensnitt
  med ett färdigt C#‑exempel. Följ stegen och se resultatet.
og_title: Hantera teckensnittsvarningar i Aspose.Words – Komplett guide
tags:
- Aspose.Words
- C#
- Document Loading
title: Hantera teckensnittsvarningar i Aspose.Words – Upptäck saknade teckensnitt
url: /sv/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hantera teckensnittsvarningar i Aspose.Words – Upptäck saknade teckensnitt

Har du någonsin behövt **hantera teckensnittsvarningar** när du laddar ett Word‑dokument och undrat varför viss text ser konstig ut? Du är inte ensam. Saknade teckensnitt utlöser ersättningsvarningar som tyst kan förstöra den visuella layouten, och om du inte **upptäcker saknade teckensnitt** kommer du aldrig att veta vad som gick fel.

I den här handledningen visar vi dig ett praktiskt sätt att **hantera teckensnittsvarningar** med Aspose.Words `IWarningCallback`. I slutet av guiden kommer du kunna upptäcka varje teckensnitts‑ersättningshändelse, logga den och till och med bestämma om du ska avbryta inläsningen. Inga externa dokument, bara ett enda, kopiera‑och‑klistra‑klart exempel.

## Vad du kommer att lära dig

- Skapa en anpassad varningshanterare som endast reagerar på teckensnitts‑ersättningsvarningar.  
- Fäst hanteraren på `LoadOptions` så att varje dokumentladdning går igenom den.  
- Verifiera utskriften i konsolen och förstå vad varje varning betyder.  

**Förutsättningar**

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.6+).  
- Aspose.Words för .NET installerat via NuGet (`Install-Package Aspose.Words`).  
- En Word‑fil som refererar till ett teckensnitt som inte är installerat på din maskin (t.ex. ett anpassat företags‑teckensnitt).  

Om du saknar någon av dessa, hämta dem nu – annars, låt oss köra igång.

## Så hanterar du teckensnittsvarningar i Aspose.Words

Nedan är det kompletta, körbara programmet. Det innehåller allt från `using`‑satserna till `Main`‑metoden, så du kan klistra in det i en konsolapp och trycka **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Förväntad konsolutskrift** (förutsatt att dokumentet använder ett teckensnitt du inte har installerat):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Om dokumentet innehåller **inga saknade teckensnitt**, visas aldrig varningsraden – så du har effektivt **upptäckt saknade teckensnitt** endast när det behövs.

### Varför detta fungerar

Aspose.Words kastar en `WarningInfo` för varje icke‑kritisk fråga den stöter på när den parsar en fil. Genom att implementera `IWarningCallback` får du en krok in i den pipeline. Flaggan `WarningType.FontSubstitution` talar exakt om när biblioteket var tvunget att ersätta ett begärt teckensnitt med ett reservteckensnitt. Detta är det mest pålitliga sättet att **hantera teckensnittsvarningar** eftersom det körs *under* inläsningen, innan du ens rör dokumentets objektmodell.

## Upptäck saknade teckensnitt utan att krascha din app

Ibland kan du vilja behandla ett saknat teckensnitt som ett kritiskt fel – kanske förbjuder dina varumärkesriktlinjer någon ersättning. Du kan ändra hanteraren så att den kastar ett undantag istället för att bara logga:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Nu kommer `try…catch`‑blocket runt `new Document(...)` att fånga problemet, så att du kan bestämma om du ska avbryta, använda en reserv eller fråga användaren.

## Bonus: Visualisera varningar i en UI‑applikation

Om du bygger en WinForms‑ eller WPF‑app, ersätt `Console.WriteLine` med ett UI‑vänligt anrop:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

På så sätt ser slutanvändarna varningen omedelbart, och du **hanterar fortfarande teckensnittsvarningar** konsekvent på alla plattformar.

## Vanliga fallgropar & pro‑tips

- **Fallgrop:** Glömmer att sätta `WarningCallback`. Standardbeteendet är att ignorera teckensnittsvarningar, så du kommer aldrig att se dem.  
  **Pro‑tips:** Skapa alltid en `LoadOptions`‑instans även om du bara behöver varningshanteraren. Det är billigt och explicit.  

- **Fallgrop:** Använder fel sökvägsseparator på icke‑Windows‑OS.  
  **Pro‑tips:** Använd `Path.Combine` eller en rå strängliteral (`@"C:\Docs\MissingFont.docx"` fungerar på Windows; på Linux använd `"/home/user/docs/MissingFont.docx"`).  

- **Fallgrop:** Antar att varningen triggas för inbäddade teckensnitt.  
  **Pro‑tips:** Inbäddade teckensnitt anses vara närvarande, så ingen ersättningsvarning visas. Testa med verkligen *saknade* teckensnitt för att se hanteraren i aktion.  

- **Fallgrop:** Överloggning av alla varningstyper.  
  **Pro‑tips:** Filtrera på `WarningType.FontSubstitution` som visat – detta håller konsolen ren och fokuserar på **upptäcka saknade teckensnitt**‑scenariot.  

## Fullständigt fungerande exempel – sammanfattning

Här är hela programmet igen, den här gången utan kommentarer för dem som föredrar en ren vy:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Kopiera, klistra in, kör – din konsol kommer nu att **hantera teckensnittsvarningar** och **upptäcka saknade teckensnitt** automatiskt.

## Nästa steg

- **Logga till en fil:** Ersätt `Console.WriteLine` med en logger (t.ex. NLog) för produktionsklassad spårning.  
- **Batch‑bearbetning:** Loopa igenom en mapp med dokument och samla alla teckensnitts‑ersättningshändelser i en CSV‑rapport.  
- **Automatisk teckensnittsinstallation:** Koppla in i varningshanteraren för att ladda ner saknade teckensnitt från ett företagsarkiv innan inläsningen fortsätter.  

Var och en av dessa utökningar bygger på kärnidén att **hantera teckensnittsvarningar** på ett rent, återanvändbart sätt.

---

*Lycklig kodning! Om du stöter på några konstigheter när du försöker **upptäcka saknade teckensnitt**, lämna en kommentar nedan. Jag hjälper gärna till att felsöka.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}