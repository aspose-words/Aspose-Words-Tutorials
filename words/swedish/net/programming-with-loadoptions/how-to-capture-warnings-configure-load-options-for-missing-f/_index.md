---
category: general
date: 2026-03-30
description: hur man fångar varningar vid inläsning av en DOCX-fil – lär dig att upptäcka
  saknade teckensnitt, konfigurera teckensnittsinställningar och ange inläsningsalternativ
  i C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: sv
og_description: hur man fångar varningar vid inläsning av en DOCX‑fil – steg‑för‑steg‑guide
  för att upptäcka saknade typsnitt och konfigurera teckensnittsinställningar i C#
og_title: hur man fångar varningar – konfigurera laddningsalternativ för saknade typsnitt
tags:
- Aspose.Words
- C#
- Font management
title: hur man fångar varningar – konfigurera laddningsalternativ för saknade teckensnitt
url: /sv/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hur man fångar varningar – konfigurera laddningsalternativ för saknade teckensnitt

Har du någonsin undrat **hur man fångar varningar** som dyker upp när ett dokument försöker använda ett teckensnitt du inte har installerat? Det är ett scenario som får många utvecklare som arbetar med ordbehandlingsbibliotek att snubbla, särskilt när du behöver **upptäcka saknade teckensnitt** innan de bryter din PDF‑exportpipeline.

I den här handledningen visar vi dig en praktisk, färdig‑att‑köra lösning som **konfigurerar teckensnittsinställningar**, **sätter laddningsalternativ**, och skriver ut varje ersättningsvarning till konsolen. När du är klar vet du exakt hur du **hanterar saknade teckensnitt** på ett sätt som gör din applikation robust och dina användare nöjda.

## Vad du kommer att lära dig

- Hur man **sätter laddningsalternativ** så att biblioteket rapporterar teckensnittproblem istället för att tyst byta dem.
- De exakta stegen för att **konfigurera teckensnittsinställningar** för varningsfångst.
- Sätt att **upptäcka saknade teckensnitt** programatiskt och reagera därefter.
- Ett komplett, copy‑paste C#‑exempel som fungerar med den senaste Aspose.Words för .NET (v24.10 vid skrivande stund).
- Tips för att utöka lösningen för att logga varningar, falla tillbaka till egna teckensnitt, eller avbryta bearbetning när kritiska teckensnitt saknas.

> **Förutsättning:** Du behöver Aspose.Words för .NET NuGet‑paketet installerat (`Install-Package Aspose.Words`). Inga andra externa beroenden krävs.

---

## Steg 1: Importera namnrymder och förbered projektet

Först, lägg till de nödvändiga `using`‑direktiven. Detta är inte bara boilerplate; det talar om för kompilatorn var `LoadOptions`, `FontSettings` och `Document` finns.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Proffstips:** Om du använder .NET 6+ kan du aktivera *global using*-satser för att undvika att upprepa dessa rader i varje fil.

---

## Steg 2: Sätt laddningsalternativ och aktivera varningar för teckensnittsersättning

Kärnan i **hur man fångar varningar** ligger i `LoadOptions`‑objektet. Genom att skapa en ny `FontSettings`‑instans och fästa en händelsehanterare på `SubstitutionWarning` talar du om för biblioteket att ropa varje gång det inte kan hitta ett begärt teckensnitt.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Varför detta är viktigt:** Utan händelseprenumerationen faller Aspose.Words tyst tillbaka till ett standardteckensnitt, och du får aldrig veta vilka glyfer som byttes. Genom att lyssna på `SubstitutionWarning` får du en fullständig revisionsspårning—avgörande för miljöer med tung efterlevnad.

---

## Steg 3: Ladda dokumentet med de konfigurerade alternativen

Nu när varningarna är kopplade, ladda ditt DOCX (eller något annat stödd format) med de `loadOptions` du just förberedde. `Document`‑konstruktorn kommer omedelbart att trigga teckensnittskontrolllogiken.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Om filen refererar, säg, *“Comic Sans MS”* på en maskin som bara har *“Arial”*, kommer du att se något i stil med:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Den raden skrivs direkt till konsolen på grund av den händelsehanterare vi fäste tidigare.

---

## Steg 4: Verifiera och reagera på fångade varningar

Att fånga varningar är bara halva striden; du måste ofta bestämma vad du ska göra härnäst. Nedan är ett snabbt mönster som lagrar varningar i en lista för senare analys—perfekt om du vill logga dem till en fil eller avbryta importen när ett kritiskt teckensnitt saknas.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Hantering av kantfall:**  
- **Flera saknade teckensnitt:** Listan kommer att innehålla ett objekt per ersättning, så du kan iterera och bygga en detaljerad rapport.  
- **Egna reservteckensnitt:** Om du har egna teckensnitts‑filer, lägg till dem i `FontSettings` innan du laddar: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Varningarna kommer då att visa den egna reserven istället för systemstandard.

---

## Steg 5: Fullt fungerande exempel (kopiera‑klistra‑klart)

När vi sätter ihop allt, här är en självständig konsolapp som du kan kompilera och köra direkt nu.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Förväntad konsolutmatning** (när DOCX‑filen refererar till ett saknat teckensnitt):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Om ett *kritiskt* teckensnitt som “Times New Roman” saknas, kommer du att se avbrytningsmeddelandet istället.

---

## Vanliga frågor & fallgropar

| Fråga | Svar |
|----------|--------|
| **Behöver jag anropa `SetFontsFolder` för att fånga varningar?** | Nej. Varningshändelsen fungerar med standardsystemteckensnitten. Använd `SetFontsFolder` endast när du vill tillhandahålla extra reservteckensnitt. |
| **Fungerar detta på .NET Core / .NET 5+?** | Absolut. Aspose.Words 24.10 stödjer alla moderna .NET‑runtime. Se bara till att NuGet‑paketet matchar ditt mål‑ramverk. |
| **Vad händer om jag vill logga varningar till en fil istället för konsolen?** | Byt ut `Console.WriteLine(msg);` mot ett anrop till valfri loggningsramverk, t.ex. `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Kan jag undertrycka varningar för specifika teckensnitt?** | Ja. Inuti händelsehanteraren kan du filtrera: `if (e.FontName == "SomeFont") return;`. Detta ger fin‑granulerad kontroll. |
| **Finns det ett sätt att behandla saknade teckensnitt som fel?** | Kasta ett undantag manuellt i händelsehanteraren när ett villkor uppfylls, eller sätt en flagga och avbryt efter `Document`‑konstruktion som visas i exemplet. |

---

## Slutsats

Du har nu ett robust, produktionsklart mönster för **hur man fångar varningar** som uppstår när du laddar dokument med saknade teckensnitt. Genom att **upptäcka saknade teckensnitt**, **konfigurera teckensnittsinställningar**, och **sätta laddningsalternativ** på rätt sätt får du full insyn i teckensnittsersättningshändelser och kan besluta om du vill logga, falla tillbaka eller avbryta.

Ta nästa steg genom att integrera denna logik i din PDF‑konverteringspipeline, lägga till egna reservteckensnitt, eller mata in varningslistan i ett övervakningssystem. Tillvägagångssättet skalar från små verktyg till företagsklassade dokumentbehandlingstjänster.

### Vidare läsning & nästa steg

- **Utforska fler FontSettings‑funktioner** – inbäddning av egna teckensnitt, styrning av reservordning och licensfrågor.  
- **Kombinera med PDF‑konvertering** – efter att ha fångat varningar, anropa `doc.Save("output.pdf");` och verifiera att PDF‑filen använder de förväntade teckensnitten.  
- **Automatisera testning** – skriv enhetstester som laddar dokument med kända saknade teckensnitt och verifiera att varningslistan innehåller de förväntade meddelandena.  

Om du stöter på problem eller har idéer för förbättringar, tveka inte att lämna en kommentar. Lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}