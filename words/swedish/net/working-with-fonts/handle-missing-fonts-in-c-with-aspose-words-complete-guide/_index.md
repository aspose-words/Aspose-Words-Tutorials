---
category: general
date: 2026-02-26
description: Hantera saknade teckensnitt i C# med Aspose.Words. Lär dig att fånga
  varningar om teckensnittssubstitution, implementera IWarningCallback och se till
  att dina dokument ser rätt ut.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: sv
og_description: Hantera saknade typsnitt i C# snabbt. Den här guiden visar hur du
  fångar varningar om typsnittsbyte med Aspose.Words, implementerar IWarningCallback
  och verifierar resultaten.
og_title: Hantera saknade teckensnitt i C# – Steg‑för‑steg Aspose.Words‑handledning
tags:
- Aspose.Words
- C#
- Document Processing
title: Hantera saknade teckensnitt i C# med Aspose.Words – Komplett guide
url: /sv/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hantera saknade teckensnitt i C# med Aspose.Words – Komplett guide

Har du någonsin behövt **hantera saknade teckensnitt** när du läser in ett Word‑dokument i C# och undrat varför resultatet ser konstigt ut? Du är inte ensam. När en källfil refererar till ett teckensnitt som inte är installerat på maskinen, ersätter Aspose.Words tyst ett annat, vilket kan förstöra din layout eller ditt varumärke.  

Den goda nyheten? Genom att koppla en **warning callback** kan du fånga varje teckensnittssubstitutions‑händelse, logga den och bestämma om du ska tillhandahålla ett ersättnings‑teckensnitt. I den här handledningen går vi igenom hela processen – från att sätta upp projektet till att verifiera konsolutdata – så att du aldrig blir överraskad av ett osynligt teckensnitt igen.

> **Vad du får**: En färdig‑att‑köra C#‑konsolapp som rapporterar varje saknat teckensnitt, förklarar varför varningen uppstår, och visar hur du kan utöka hanteraren för anpassad logik.

---

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar både på .NET Core och .NET Framework)
- Visual Studio 2022 (eller någon annan C#‑IDE du föredrar)
- En **licens** för Aspose.Words för .NET (gratis provversion fungerar för testning)
- Ett Word‑dokument som refererar till ett teckensnitt du inte har installerat (t.ex. *Comic Sans MS* på en Linux‑maskin)

Om du har detta, låt oss dyka ner.

---

## Steg 1: Skapa ett nytt konsolprojekt och lägg till Aspose.Words

För att hålla allt ordnat, börja med ett nytt konsolprojekt.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Proffstips**: Använd flaggan `--framework net6.0` om du vill rikta in dig på en specifik runtime.

Det här hämtar det senaste Aspose.Words‑NuGet‑paketet, som innehåller typerna `LoadOptions` och `IWarningCallback` som vi kommer att behöva.

## Steg 2: Implementera en varningshanterare (IWarningCallback)

Aspose.Words genererar ett `WarningInfo`‑objekt för varje icke‑kritisk fråga den stöter på när ett dokument läses in. Genom att implementera `IWarningCallback` bestämmer du vad som ska göras med dessa varningar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Varför detta är viktigt**: Utan en hanterare ignoreras varningar om teckensnittssubstitution tyst. Genom att skriva ut dem får du omedelbar insikt i vilka teckensnitt som saknas och vad Aspose.Words använde istället.

## Steg 3: Konfigurera LoadOptions med varnings‑callbacken

Nu kopplar vi hanteraren till dokument‑läsningsprocessen. `LoadOptions` låter dig ansluta callbacken innan filen parsas.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Obs**: Ersätt `YOUR_DIRECTORY` med den faktiska mappen som innehåller ditt test‑`.docx`. `LoadOptions`‑instansen måste skickas till `Document`‑konstruktorn; annars aktiveras det tysta standardbeteendet.

## Steg 4: Kör applikationen och verifiera utdata

Kompilera och kör:

```bash
dotnet run
```

Om dokumentet refererar till ett teckensnitt som inte finns på din maskin (t.ex. *Papyrus*), kommer du att se något liknande:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Den enda raden berättar exakt vilket teckensnitt som saknas och vilket reservteckensnitt Aspose.Words valde. Du kan nu bestämma dig för att bädda in det saknade teckensnittet, ändra källdokumentet eller acceptera substitutionen.

## Steg 5: Avancerat – Samla varningar för senare bruk

Ibland vill du lagra varningar istället för att skriva ut dem omedelbart. Nedan är en snabb justering av hanteraren som samlar meddelanden i en lista.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

Och uppdatera `Main` därefter:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Nu har du en återanvändbar lista som du kan skriva till en loggfil, skicka till en övervakningstjänst eller visa i ett UI.

## Steg 6: Vanliga fallgropar & hur du undviker dem

| Problem | Varför det händer | Lösning |
|-------|----------------|-----|
| **Inga varningar visas** | Callbacken var inte ansluten, eller så laddades dokumentet utan `LoadOptions`. | Se till att `LoadOptions.WarningCallback` är satt **innan** du anropar `Document`‑konstruktorn. |
| **Fel teckensnittsnamn i meddelandet** | Vissa teckensnitt är inbäddade i dokumentet; Aspose.Words rapporterar det *ursprungliga* namnet, inte det inbäddade. | Verifiera källdokumentets teckensnittsreferenser; inbäddning av teckensnitt eliminerar varningen helt. |
| **Prestandapåverkan** | Att samla varningar för tusentals dokument kan skapa extra belastning. | Använd en enkel `Console.WriteLine` för snabb felsökning; byt till en samlare endast när du behöver datan. |

## Visuell sammanfattning

![Illustration som visar hantering av saknade teckensnitt med varnings‑callback‑flöde](/images/handle-missing-fonts.png "Diagram över hantering av saknade teckensnitt med Aspose.Words")

*Diagrammet (alt‑texten innehåller huvudnyckelordet) visualiserar hur varnings‑callbacken avbryter teckensnittssubstitutions‑händelser under dokumentladdning.*

## Slutsats

Du vet nu **hur du hanterar saknade teckensnitt** i C# med Aspose.Words. Genom att koppla en `IWarningCallback` till `LoadOptions` får du full insyn i varje teckensnittssubstitutions‑händelse, kan logga eller agera på den, och i slutändan säkerställa att dina genererade dokument behåller det avsedda utseendet och känslan.

> **Snabb sammanfattning**:  
> 1. Lägg till Aspose.Words i en konsolapp.  
> 2. Implementera `FontWarningHandler` (eller en samlare).  
> 3. Skicka den via `LoadOptions` när du laddar dokumentet.  
> 4. Verifiera konsolutdata eller lagrade varningar.  

Härifrån kan du utforska **inbäddning av saknade teckensnitt** (`FontSettings.SubstitutionSettings`) eller **automatisk nedladdning från en företags‑teckensnittserver** – båda är naturliga utökningar av det mönster vi just byggt.

Har du fler frågor om **Aspose.Words‑teckensnittsvarning**, **C# LoadOptions**, eller **dokumentladdning med saknade teckensnitt**? Lämna en kommentar, och lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}