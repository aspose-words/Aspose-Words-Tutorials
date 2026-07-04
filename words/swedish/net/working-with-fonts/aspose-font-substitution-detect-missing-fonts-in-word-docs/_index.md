---
category: general
date: 2026-05-04
description: Lär dig hur du använder Aspose teckensnittssubstitution för att upptäcka
  saknade teckensnitt när du laddar ett Word‑dokument och hämta detaljer om de saknade
  teckensnitten – steg‑för‑steg‑guide.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: sv
og_description: Behärska Aspose teckensnittssubstitution för att upptäcka saknade
  teckensnitt när du laddar ett Word-dokument och hämta information om saknade teckensnitt
  med komplett C#‑kod.
og_title: Aspose teckensnittssubstitution – Upptäck saknade teckensnitt i Word-dokument
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose teckensnittssubstitution: Upptäck saknade teckensnitt i Word-dokument'
url: /sv/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Upptäck saknade teckensnitt i Word-dokument

Har du någonsin undrat varför ett Word-dokument ser felaktigt ut på en annan maskin? Ofta är boven ett saknat teckensnitt, och **Aspose font substitution** är verktyget som låter dig upptäcka dessa luckor innan de blir en visuell katastrof. I den här handledningen går vi igenom hur du **upptäcker saknade teckensnitt** så snart du **laddar ett Word-dokument**, och sedan **hämtar information om saknade teckensnitt** så att du kan åtgärda eller ersätta dem.

Vi kommer att gå igenom allt från att konfigurera varnings‑callbacken till att hämta en ren lista över saknade teckensnitt. I slutet har du ett färdigt C#‑exempel som exakt talar om vilka teckensnitt som saknades, och du förstår varför detta är viktigt för dokumentets integritet.

---

## Förutsättningar – Vad du behöver innan du börjar

- **Aspose.Words for .NET** (v23.12 eller senare rekommenderas).  
- En .NET‑utvecklingsmiljö (Visual Studio, Rider eller `dotnet`‑CLI).  
- Ett exempel‑DOCX som medvetet använder ett teckensnitt du inte har installerat—kalla det `DocumentWithMissingFont.docx`.  
- Grundläggande C#‑kunskaper—inget avancerat, bara förmågan att köra ett konsolprogram.

Om någon av dessa är obekanta, pausa och installera NuGet‑paketet:

```bash
dotnet add package Aspose.Words
```

Det är allt. Inga extra teckensnitt, inga externa tjänster.

## Steg 1: Ladda Word-dokumentet (och utlösa teckensnittskontroller)

Det första du gör är att **ladda ett Word-dokument**. Aspose.Words analyserar filen och om den inte kan hitta ett refererat teckensnitt, köar den en *FontSubstitution*-varning. Här är koden som laddar dokumentet:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Varför detta är viktigt:** Att ladda dokumentet tidigt ger Aspose möjlighet att skanna varje textkörning, stil och inbäddat objekt. Om ett teckensnitt inte hittas på systemet eller i den anpassade teckensnittsmappen får du en varning senare.

## Steg 2: Anslut en varnings‑callback för att fånga substitutionshändelser

Aspose.Words använder en callback‑mekanism för att informera dig om problem som saknade teckensnitt. Genom att tilldela en implementation av `IWarningCallback` till `doc.WarningCallback` kan du fånga varje varning när den inträffar.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Proffstips:** Du kan ansluta flera callbacks (t.ex. loggning, UI‑uppdateringar) genom att omsluta dem i ett kompositmönster, men för den här handledningen håller en enda callback saker tydliga.

## Steg 3: Implementera Font Substitution‑varningscallbacken

Nu definierar vi klassen som faktiskt utför arbetet. Callbacken får ett `WarningInfo`‑objekt; vi filtrerar på `WarningType.FontSubstitution` och sparar beskrivningen för senare användning.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Vad som händer:** När Aspose stöter på ett saknat teckensnitt skapar den en varning som “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Vår callback skriver ut den raden och sparar den.

## Steg 4: Bearbeta dokumentet (valfritt) och samla saknade teckensnitt

Om du bara behöver **upptäcka saknade teckensnitt** räcker laddningssteget—varningarna avfyras automatiskt. Många utvecklare behöver dock **hämta information om saknade teckensnitt** efter att ha utfört vissa operationer (t.ex. spara, konvertera). Nedan tvingar vi en liten operation—spara till PDF—för att säkerställa att alla varningar avges, och sedan hämtar vi de samlade meddelandena.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Förväntad konsolutmatning** (exempel):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Observera hur varje rad tydligt anger det ursprungliga teckensnittet och det reservteckensnitt som Aspose valde. Det är kärnan i **aspose font substitution**‑rapporteringen.

## Steg 5: Avancerat – Använda anpassade teckensnittskällor för att minska substitutioner

Ibland *har* du de saknade teckensnitten, bara inte i standardsystemmappen. Aspose.Words låter dig peka på en anpassad katalog via `FontSettings`. Att lägga till detta steg kan kraftigt minska antalet substitutionsvarningar.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Varför lägga till detta?** Om du distribuerar dokument över maskiner, säkerställer att paketera de nödvändiga teckensnitten i en känd mapp samma visuella utseende överallt. Det gör också din **detect missing fonts**‑rutin mer exakt eftersom Aspose kontrollerar den mappen innan den faller tillbaka.

## Komplett fungerande exempel

När allt sätts ihop, här är ett enda, kopiera‑och‑klistra‑klart konsolprogram. Spara det som `Program.cs` och kör det med `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Vad du bör se:** Om källdokumentet DOCX refererar till teckensnitt du inte har, skriver konsolen ut varje substitutionsrad följt av en kort sammanfattning. Om alla teckensnitt finns, får du meddelandet “No missing fonts were detected.”

## Vanliga fallgropar & hur man undviker dem

| Problem | Varför det händer | Lösning |
|-------|----------------|-----|
| **Inga varningar visas** | Dokumentet använder bara systemteckensnitt, eller så har du redan lagt till en anpassad mapp som innehåller de saknade teckensnitten. | Verifiera att DOCX verkligen refererar till ett otillgängligt teckensnitt. Du kan öppna det i Word och ändra ett stycke till ett sällsynt teckensnitt (t.ex. “Papyrus”). |
| **Duplicerade meddelanden** | Samma teckensnitt används i flera körningar, vilket orsakar flera varningar. | Av‑duplicera listan med `Distinct()` om du bara behöver en unik uppsättning. |
| **Prestandaproblem på stora dokument** | Varje varning bearbetas på UI‑tråden. | Kör laddningen i en bakgrundsuppgift eller använd `Parallel.ForEach` för efterbehandling. |
| **Fel reservteckensnitt** | Asposes standardreservteckensnitt kanske inte matchar ditt varumärke. | Ställ in `FontSettings.SubstitutionSettings.DefaultFontName` till ett föredraget reservteckensnitt (t.ex. “Calibri”). |

## Utöka lösningen – Exportera saknade teckensnitt till JSON

Om du bygger en webbtjänst som behöver rapportera saknade teckensnitt tillbaka till en klient, är serialisering av listan trivialt:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Nu kan ditt API returnera en ren JSON‑payload som ett annat system kan konsumera.

## Slutsats

I den här guiden demonstrerade vi **Aspose font substitution** från början till slut: ladda ett Word-dokument, ansluta en varnings‑callback, fånga varje *detect missing fonts*-händelse, och slutligen **retrieve missing font**‑information för rapportering eller åtgärd. Genom att lägga till valfria anpassade teckensnittsmappar kan du minska listan över substitutioner, och med några extra rader kan du till och med exportera resultaten som JSON.

Kom ihåg att den visuella integriteten i dina dokument beror på de teckensnitt de använder. Med tekniken som visas här blir du aldrig överraskad av ett oväntat reservteckensnitt igen.  

Redo att ta nästa steg? Försök integrera denna logik i en större dokument‑bearbetningspipeline, eller utforska Aspose.Words andra funktioner som teckensnitts‑inbäddning (`doc.FontSettings.EmbeddedFonts`). Möjligheterna är oändliga, och dina användare kommer att tacka dig för det polerade resultatet.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}