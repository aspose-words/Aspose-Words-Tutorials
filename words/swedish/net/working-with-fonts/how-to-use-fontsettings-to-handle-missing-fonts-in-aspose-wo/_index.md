---
category: general
date: 2026-03-16
description: Lär dig hur du använder FontSettings i Aspose.Words för att hantera saknade
  teckensnitt på ett smidigt sätt—fullständig kod, händelsehantering och bästa praxis‑tips.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: sv
og_description: Hur du använder FontSettings i Aspose.Words för att hantera saknade
  teckensnitt – steg‑för‑steg‑guide med komplett C#‑exempel och praktiska tips.
og_title: Hur du använder FontSettings för att hantera saknade teckensnitt i Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: Hur man använder FontSettings för att hantera saknade teckensnitt i Aspose.Words
url: /sv/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så använder du FontSettings för att hantera saknade typsnitt i Aspose.Words

Har du någonsin undrat **hur du använder FontSettings** när dina Word-dokument refererar till typsnitt som inte är installerade på servern? Du är inte ensam. Saknade typsnitt kan leda till fula ersättningar eller till och med kasta undantag, och de flesta utvecklare ignorerar helt enkelt problemet tills det dyker upp i produktion.  

I den här handledningen visar vi dig exakt **hur du använder FontSettings** för att **hantera saknade typsnitt** i Aspose.Words, fånga detaljerade varningar och hålla din dokumentrendering förutsägbar. I slutet har du ett färdigt C#‑exempel, förstår varför varje rad är viktig och vet hur du anpassar lösningen för större projekt.

## Vad den här guiden täcker

- Konfigurera **FontSettings** och prenumerera på `SubstitutionWarning`‑händelsen.  
- Koppla inställningarna till `LoadOptions` så att de respekteras när ett dokument laddas.  
- Köra ett testdokument som medvetet saknar typsnitt och läsa konsolutdata.  
- Tips för loggning, inaktivering av automatisk ersättning och hantering av kantfall som flera saknade typsnitt.  

Ingen extern dokumentation krävs—allt du behöver finns här.

## Förutsättningar

- .NET 6+ (eller .NET Framework 4.6.2+).  
- Aspose.Words för .NET 23.9 eller senare (API:et vi använder är stabilt över de senaste versionerna).  
- En enkel `.docx`‑fil som refererar till ett typsnitt du vet inte är installerat (t.ex. *Comic Sans MS* i en Linux‑container).  

Det är allt—inga extra NuGet‑paket utöver Aspose.Words.

## Varför hantering av saknade typsnitt är viktigt

När ett dokument refererar till ett typsnitt som runtime‑miljön inte kan hitta, ersätter Aspose.Words automatiskt det närmaste matchande typsnittet. Den ersättningen är ofta acceptabel, men ibland behöver du **logga** vilka typsnitt som saknades (för efterlevnad) eller **förhindra** ersättningen helt (t.ex. för varumärkes‑specifika PDF‑filer). Genom att utnyttja `FontSettings.SubstitutionWarning` får du full insyn och kontroll.

## Steg 1: Skapa FontSettings och prenumerera på Substitution‑Warning‑händelsen

Det första du gör är att instansiera `FontSettings`. Detta objekt innehåller all typsnittsrelaterad konfiguration för biblioteket. Den avgörande delen är att koppla `SubstitutionWarning`‑händelsen, som avfyras **varje gång** Aspose.Words inte kan hitta ett begärt typsnitt.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Varför detta är viktigt:**  
- **Synlighet:** Du får omedelbart veta vilka typsnitt som saknas.  
- **Spårbarhet:** Konsolen (eller en logger) kan omdirigeras till en fil för efterlevnadsrapporter.  
- **Kontroll:** Senare kan du välja att ersätta substitutionen med ett eget anpassat typsnitt.

> **Proffstips:** Om du föredrar ett loggningsramverk (Serilog, NLog, etc.), ersätt `Console.WriteLine`‑anropen med `logger.Information(...)`.

## Steg 2: Koppla FontSettings till LoadOptions

`LoadOptions` är verktyget som talar om för Aspose.Words hur filen ska behandlas under inläsningsfasen. Genom att tilldela `FontSettings`‑objektet säkerställer du att varningshanteraren är aktiv *innan* något innehåll analyseras.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Varför detta är viktigt:**  
- Om du laddar ett dokument utan att skicka med `LoadOptions` aktiveras standardhanteringen av typsnitt och du missar varningarna.  
- Detta tillvägagångssätt låter dig också justera andra inläsningsbeteenden (t.ex. lösenordsskydd) i samma objekt.

## Steg 3: Ladda dokumentet med de konfigurerade alternativen

Nu läser vi äntligen Word‑filen. Sökvägen kan vara absolut eller relativ; Aspose.Words kommer att respektera de `LoadOptions` vi just förberedde.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Om dokumentet innehåller ett typsnitt som inte är installerat, avfyras `SubstitutionWarning`‑händelsen, och du kommer att se en utskrift liknande exemplet nedan.

### Förväntad konsolutskrift

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Den exakta ersättningen kan variera beroende på operativsystemets typsnittsföljd, men **namnet på det saknade typsnittet** kommer alltid att rapporteras.

## Steg 4: Verifiera resultatet (valfri rendering)

Ofta vill du vara säker på att dokumentet fortfarande ser bra ut efter ersättningen. Ett snabbt sätt är att spara det som PDF och öppna resultatet.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Om du behöver **förhindra** ersättning helt, sätt `FontSettings.SubstitutionSettings.TableSubstitution = false` innan du laddar. Då kommer Aspose.Words att kasta ett undantag för saknade typsnitt, vilket du kan fånga och hantera.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Fullständigt fungerande exempel

Nedan är det kompletta, färdiga programmet. Klistra in det i en konsolapplikation, justera filvägen och tryck **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Vad du kan förvänta dig

- Konsolen skriver ut varje saknat typsnitt tillsammans med den valda ersättningen.  
- Den resulterande PDF‑filen (om du behöll den valfria sparningen) visar dokumentet med fallback‑typsnittet, vilket säkerställer layoutens integritet.

## Vanliga frågor & kantfall

| Question | Answer |
|----------|--------|
| **Vad händer om flera typsnitt saknas?** | Händelsen avfyras en gång per saknat typsnitt, så du får en separat loggrad för varje. |
| **Kan jag ersätta fallback‑typsnittet med ett eget typsnitt?** | Ja. Inuti händelsehanteraren kan du anropa `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **Utlöser varningen för inbäddade typsnitt som misslyckas med att laddas?** | Absolut—oavsett om typsnittet är externt eller inbäddat är varningsmekanismen densamma. |
| **Behöver jag avdisponera `Document`?** | `Document` implementerar `IDisposable`. Omge användningen med ett `using`‑block om du laddar många filer i en loop. |
| **Fungerar detta i Linux‑containers?** | Så länge Aspose.Words kan hitta systemtypsnitt (t.ex. via `fontconfig`) fungerar samma händelsemekanism. |

## Bästa praxis & proffstips

- **Centralisera loggning:** Skapa en hjälpfunktion som skriver både till konsolen och en beständig loggfil.  
- **Batch‑bearbetning:** När du konverterar dussintals dokument, återanvänd en enda `FontSettings`‑instans för att undvika repetitiva händelseprenumerationer.  
- **Prestanda:** Substitutionsvarningar lägger till försumbar overhead, men om du bearbetar tusentals filer, överväg att inaktivera dem efter att du verifierat typsnittssamlingen.  
- **Versionssäkerhet:** `SubstitutionWarning`‑API:et har varit stabilt sedan Aspose.Words 16.0, så du kan lita på det för framtida uppgraderingar.

## Slutsats

Vi har gått igenom **hur du använder FontSettings** i Aspose.Words för att **hantera saknade typsnitt** på ett elegant sätt. Genom att skapa ett `FontSettings`‑objekt, prenumerera på `SubstitutionWarning` och ladda dokument via `LoadOptions` får du full insyn i typsnittsproblem och kan besluta om du vill logga, ersätta eller avbryta vid saknade typsnitt.  

Från den enkla konsolutskriften till anpassad substitutionslogik, skalar mönstret till stora batch‑dokumentpipeline, vilket säkerställer att ditt resultat förblir konsekvent och spårbart.

**Next steps:**  

- Utforska **anpassad typsnittsersättning** genom att tilldela `e.SubstitutedFont` i händelsen.  
- Kombinera detta tillvägagångssätt med **dokumentrendering till bilder** för generering av miniatyrer.  
- Titta på **Aspose.PDF** om du behöver bädda in de ersatta typsnitten direkt i den slutgiltiga PDF‑filen för full portabilitet.

Lycka till med kodningen, och må dina dokument aldrig lida av ett lömskt saknat typsnitt igen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}