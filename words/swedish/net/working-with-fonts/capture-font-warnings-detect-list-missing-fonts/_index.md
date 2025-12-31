---
category: general
date: 2025-12-31
description: Fånga teckensnittsvarningar i Aspose.Words för att upptäcka saknade teckensnitt
  och lista saknade teckensnitt i din .NET‑app. Lär dig en steg‑för‑steg C#‑lösning.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: sv
og_description: Fånga teckensnittsvarningar i Aspose.Words för att upptäcka saknade
  teckensnitt och lista saknade teckensnitt. Komplett C#‑guide med kod och tips.
og_title: Fånga teckensnittsvarningar – Upptäck och lista saknade teckensnitt
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Fånga teckensnittsvarningar – Upptäck och lista saknade teckensnitt
url: /sv/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fånga teckensnittsvarningar – Upptäck & lista saknade teckensnitt

Har du någonsin behövt **fånga teckensnittsvarningar** när du laddar ett Word‑dokument men inte vet hur du ska visa detaljerna om saknade teckensnitt? Du är inte ensam. I många verkliga projekt orsakar saknade teckensnitt layout‑problem, och utan rätt varningar får du jaga spöklika buggar.  

I den här handledningen visar vi hur du **upptäcker saknade teckensnitt** och **listar saknade teckensnitt** med Aspose.Words för .NET. I slutet har du ett färdigt C#‑exempel som skriver ut varje ersättningsvarning, så att du kan logga, larma eller till och med byta teckensnitt automatiskt.

---

## Varför det är viktigt att fånga teckensnittsvarningar

När Aspose.Words öppnar en DOCX som refererar till ett teckensnitt som inte är installerat på servern, ersätter den tyst med ett reservteckensnitt. Dokumentet ser bra ut, men den visuella integriteten är komprometterad – tänk dig ett företagslogotyp som visas i fel typsnitt.  

Att fånga dessa varningar låter dig:

* **Behålla varumärkeskonsekvens** – du vet exakt vilka teckensnitt som saknas.
* **Automatisera åtgärder** – ersätt saknade teckensnitt programmässigt.
* **Granska efterlevnad** – generera rapporter för juridiska eller designgranskningar.

Kort sagt, **fånga teckensnittsvarningar** är den första försvarslinjen mot tyst teckensnittsersättning.

---

## Ställ in LoadOptions för att upptäcka saknade teckensnitt

Nyckeln för att visa varningarna är egenskapen `LoadOptions.FontSubstitutionWarning`. Som standard är den satt till `None`, vilket betyder att Aspose.Words sväljer meddelandena. Att byta till `All` får biblioteket att registrera varje ersättningstillfälle.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Proffstips:** Om du redan har en egen teckensnittsmapp, tilldela den med `FontSettings.SetFontsFolder("path")` innan du laddar dokumentet. På så sätt kan du **upptäcka saknade teckensnitt** som inte finns i systemkatalogen.

---

## Ladda dokumentet och lista saknade teckensnitt

Nu när `LoadOptions` är konfigurerade är nästa steg att ladda Word‑filen. Konstruktorn accepterar options‑objektet, och varje ersättning registreras i dokumentets `WarningInfoCollection`.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Om filen refererar till teckensnitt som inte är tillgängliga, skapar varje saknat teckensnitt ett `WarningInfo`‑objekt. Du kan **lista saknade teckensnitt** genom att iterera över den samlingen.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Typisk utskrift ser ut så här:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Varje rad visar exakt vilket teckensnitt som saknades, vilket uppfyller kravet **lista saknade teckensnitt**.

---

## Läs och tolka WarningInfoCollection

`WarningInfoCollection` kan innehålla olika varningstyper (t.ex. `DocumentStructure`, `ImageLoading`). För att fokusera enbart på teckensnittsproblem, filtrera på `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Varför filtrera? För stora dokument kan även varningar om korrupta bilder eller ej‑stödda funktioner dyka upp. Genom att begränsa samlingen undviker du brus och håller **fånga teckensnittsvarningar**‑utdata ren.

---

## Fullt fungerande exempel – Fånga teckensnittsvarningar i praktiken

Nedan är ett komplett, självständigt program som du kan klistra in i vilket .NET‑konsolprojekt som helst. Det demonstrerar varje steg från konfiguration av `LoadOptions` till utskrift av en prydlig lista över saknade teckensnitt.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Förväntad konsolutskrift**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Om dokumentet inte innehåller några saknade teckensnitt får du se:

```
All referenced fonts are available – no warnings captured.
```

---

## Vanliga kantfall & hur du hanterar dem

| Situation | Varför det händer | Rekommenderad åtgärd |
|-----------|-------------------|----------------------|
| **Dokumentet använder ett inbäddat OpenType‑teckensnitt** | Aspose.Words kan läsa inbäddade teckensnitt, men bara om filen inte är korrupt. | Verifiera DOCX‑filen i Word först; bädda in teckensnittet på nytt om det behövs. |
| **Stort antal varningar** (t.ex. 200+ saknade teckensnitt) | Bulk‑import från äldre system refererar ofta till ett brett teckensnittspalett. | Batch‑processa varningarna: lagra dem i en databas och kör sedan ett skript för teckensnittsinstallation. |
| **WarningInfoCollection är tom** | Antingen har dokumentet alla teckensnitt, eller så är `FontSubstitutionWarning` kvar på `None`. | Dubbelkolla din `LoadOptions`‑konfiguration och se till att du laddar rätt filsökväg. |
| **Anpassade teckensnitt på en nätverksdelning** | Nätverkslatens kan orsaka time‑outs under teckensnittssökning. | För‑ladda teckensnitten i `FontSettings` med `SetFontsFolder` och sätt `CacheFontData = true`. |

Dessa tips hjälper dig att **upptäcka saknade teckensnitt** på ett pålitligt sätt, även i komplexa miljöer.

---

## Bildillustration

![exempel på fånga teckensnittsvarningar](https://example.com/images/capture-font-warnings.png "exempel på fånga teckensnittsvarningar")

*Skärmbilden visar ett konsolkörning där två saknade teckensnitt rapporteras.*

---

## Nästa steg – Gå bortom enkel rapportering

Nu när du kan **fånga teckensnittsvarningar**, fundera på att automatisera åtgärder:

1. **Automatisk teckensnittsersättning** – Ersätt saknade teckensnitt med ett företag‑godkänt reservteckensnitt genom att ändra `FontSettings.SubstitutionSettings`.
2. **Loggning till ett övervakningssystem** – Skicka varningsmeddelandena till Serilog, ELK eller Azure Application Insights.
3. **Användarrapporter** – Generera en HTML‑ eller PDF‑sammanfattning för formgivare att granska vilka teckensnitt som behöver installeras.

Alla dessa utökningar bygger på samma grund som vi gick igenom: konfigurera `LoadOptions`, ladda dokumentet och läsa `WarningInfoCollection`.

---

## Slutsats

Du har just lärt dig hur du **fångar teckensnittsvarningar** i Aspose.Words, **upptäcker saknade teckensnitt** och **listar saknade teckensnitt** med en ren, konsolvänlig utskrift. Metoden är enkel, kräver bara några rader C#, och fungerar med alla .NET‑versioner som stödjer Aspose.Words 23.x eller senare.  

Prova på ett exempel‑DOCX som refererar till ett teckensnitt du medvetet avinstallerar – du kommer omedelbart att se varningarna. Därefter kan du bestämma om du vill installera de saknade teckensnitten, ersätta dem programmässigt eller bara logga problemet för senare granskning.

Lycka till med kodandet, och må dina dokument alltid renderas med rätt teckensnitt!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}