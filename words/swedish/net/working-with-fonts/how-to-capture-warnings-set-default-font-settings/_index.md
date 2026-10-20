---
category: general
date: 2026-03-19
description: Lär dig hur du fångar varningar i Aspose.Words, ställer in standardteckensnittinställningar
  och upptäcker saknade teckensnitt när du laddar ett Word-dokument.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: sv
og_description: Hur du fångar varningar i Aspose.Words, ställer in standardteckensnittsinställningar
  och upptäcker saknade teckensnitt när du laddar ett Word-dokument.
og_title: Hur man fångar varningar – Ställ in standardteckensnitt
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man fångar varningar – Ställ in standardteckensnitt
url: /sv/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man fångar varningar – Ställ in standard teckensnittinställningar

**How to capture warnings** är ett vanligt behov när du arbetar med Aspose.Words, särskilt om dina dokument är beroende av specifika teckensnitt som kanske inte finns på målmaskinen. Har du någonsin öppnat en DOCX och undrat varför layouten såg felaktig ut? Svaret är ofta gömt i en varning om ett saknat teckensnitt.  

I den här guiden går vi igenom **how to capture warnings** medan du **load word document**, konfigurerar **set default font settings**, och slutligen **detect missing fonts** så att du kan reagera programmässigt. Ingen onödig text—bara ett komplett, körbart exempel och resonemanget bakom varje rad.

> *Pro tip:* Att fånga varningar tidigt sparar dig från att felsöka mystiska layoutfel senare.

---

## Vad du behöver

- **Aspose.Words for .NET** (senaste versionen per 2026).  
- En .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code).  
- Ett exempel‑DOCX som refererar till ett teckensnitt du *inte* har installerat (t.ex. *Comic Sans MS* på en Linux‑maskin).  

Det är allt. Inga extra NuGet‑paket krävs utöver Aspose.Words.

---

## Steg 1 – Förstå varför du behöver fånga varningar

När Aspose.Words analyserar ett dokument kan det stöta på teckensnitt som inte är tillgängliga på värden. Som standard ersätter biblioteket tyst ett reservteckensnitt, vilket kan ändra radbrytningar, avstånd och till och med få text att försvinna.  

Genom att använda **WarningCallback** tillsammans med ett **FontSettings**‑objekt får du två saker:

1. **Visibility** – du får en `WarningInfo`‑post för varje ersättning.  
2. **Control** – du kan förkonfigurera ett standardteckensnitt för att minimera visuella överraskningar.

Tänk på det som att installera en “watchdog” som ropar varje gång motorn byter en del under huven.

---

## Steg 2 – Ställ in standard teckensnittinställningar

Det första sekundära nyckelordet, **set default font settings**, visas här. Du skapar en `FontSettings`‑instans och pekar eventuellt på en mapp som innehåller dina reservteckensnitt.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Varför?**  
> Om du inte specificerar ett reservteckensnitt väljer Aspose.Words det första systemteckensnittet som matchar stilen, vilket kan vara kraftigt annorlunda. Genom att ange ett känt standardteckensnitt garanterar du konsekvent rendering på olika maskiner.

---

## Steg 3 – Förbered en Warning Callback för att fånga varningar

Nu ska vi **how to capture warnings** genom att bifoga en `WarningInfoCollection` till laddningsalternativen. Denna samling kommer att lagra varje varning som genereras under laddningsprocessen.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` implementerar `IWarningCallback`, så Aspose.Words automatiskt skjuter varje varning till `warningInfos`. Ingen polling behövs.

---

## Steg 4 – Ladda Word-dokument med de konfigurerade alternativen

Här är där det andra sekundära nyckelordet, **load word document**, glänser. Vi skickar både `FontSettings` och `WarningCallback` via en `LoadOptions`‑instans.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Om dokumentet refererar till ett teckensnitt som inte är installerat, kommer varnings‑callbacken att fånga en `WarningType.FontSubstitution`‑post.

---

## Steg 5 – Upptäck saknade teckensnitt från insamlade varningar

Till sist svarar vi på det tredje sekundära nyckelordet, **detect missing fonts**, genom att iterera över de insamlade varningarna.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Typisk utskrift ser ut så här:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Den raden berättar exakt vilket teckensnitt som saknas och vilket reservteckensnitt som användes—information du kan logga, visa för användaren, eller till och med trigga en anpassad teckensnitts‑installationsrutin.

---

## Fullständigt körbart exempel

Nedan är hela programmet som du kan kopiera‑och‑klistra in i en konsolapplikation. Det demonstrerar **how to capture warnings**, **set default font settings**, **load word document**, och **detect missing fonts** i ett flöde.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Förväntat resultat:** När det angivna DOCX‑filen refererar till ett teckensnitt som inte är installerat, skriver konsolen ut en varning för varje ersättning. Om alla teckensnitt finns, ger loopen ingen utskrift.

---

## Vanliga fallgropar & kantfall

| Situation | Varför det händer | Hur man hanterar det |
|-----------|-------------------|----------------------|
| **Inga varningar visas** även om layouten ser felaktig ut | Dokumentet kan använda *inbäddade* teckensnitt, vilka Aspose.Words renderar utan ersättning. | Kontrollera `Document.HasEmbeddedFonts` och överväg att extrahera de inbäddade teckensnitten om du behöver dem på en annan maskin. |
| **Multiple warnings for the

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}