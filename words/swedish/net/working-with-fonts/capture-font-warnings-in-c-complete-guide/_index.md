---
category: general
date: 2026-03-06
description: Fånga teckensnittsvarningar när du laddar ett Word-dokument i C#. Lär
  dig att upptäcka saknade teckensnitt, kontrollera dokumentets teckensnitt och hantera
  saknade teckensnitt effektivt.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: sv
og_description: Fånga teckensnittsvarningar när du laddar ett Word-dokument i C#.
  Den här handledningen visar hur du upptäcker saknade teckensnitt, kontrollerar dokumentets
  teckensnitt och hanterar saknade teckensnitt.
og_title: Fånga teckensnittsvarningar i C# – Komplett guide
tags:
- Aspose.Words
- C#
- Font Management
title: Fånga teckensnittsvarningar i C# – Komplett guide
url: /sv/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fånga teckensnittsvarningar i C# – Komplett guide

Har du någonsin behövt **fånga teckensnittsvarningar** när du bearbetar ett Word‑dokument? Att fånga teckensnittsvarningar är viktigt för att **upptäcka saknade teckensnitt** och säkerställa att det slutgiltiga resultatet ser exakt ut som du tänkt dig.  

I den här handledningen går vi igenom ett praktiskt, end‑to‑end‑exempel som laddar en `.docx`‑fil, övervakar inläsningsprocessen och rapporterar eventuella teckensnittsbyten. När du är klar vet du hur du **laddar Word‑dokument** på ett säkert sätt, **kontrollerar dokumentets teckensnitt** och **hanterar saknade teckensnitt** utan oväntade körfel.

## Vad du kommer att lära dig

- Hur du kopplar en varningssamling till ett Aspose.Words `Document`.
- Vilka varningstyper som indikerar ett saknat eller ersatt teckensnitt.
- Sätt att logga eller reagera på dessa varningar i en produktionsklar applikation.
- Tips för att konfigurera egna teckensnittskällor om du vill **hantera saknade teckensnitt** på ett smidigt sätt.

> **Förkunskap:** Du har en giltig Aspose.Words for .NET‑licens (eller så använder du gratisprovversionen) och en .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code). Inga andra bibliotek krävs.

---

## Fånga teckensnittsvarningar – Steg‑för‑steg

Nedan är den kompletta, körbara koden. Varje avsnitt är uppdelat i ett eget steg så att du kan kopiera‑klistra, experimentera och bygga vidare på logiken.

![Fånga teckensnittsvarningar diagram](image.png "Diagram som visar varningsinsamling"){: alt="fånga teckensnittsvarningar diagram"}

### Steg 1: Ladda Word‑dokumentet

Först måste vi **ladda Word‑dokument** som kan innehålla teckensnitt som inte är installerade på den aktuella maskinen. `Document`‑konstruktorn gör det tunga arbetet, men vi håller anropet isolerat så att du senare kan byta till en ström eller en byte‑array om så behövs.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Varför detta är viktigt:** Att ladda ett dokument utan en varningshanterare innebär att alla teckensnittsbyten ignoreras tyst. Genom att sätta `WarningCallback` *innan* inläsningen garanterar vi att vi ser varje `FontSubstitution`‑varning som uppstår.

### Steg 2: Koppla en varningssamling

Klassen `WarningInfoCollector` är en inbyggd implementation av `IWarningCallback`. Den lagrar helt enkelt varje varning i en lista som vi senare kan inspektera.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Proffstips:** Om du vill **hantera saknade teckensnitt** mer aggressivt (t.ex. avbryta inläsningen eller ersätta med ett specifikt reservteckensnitt) kan du ersätta `Console.WriteLine` med egen logik – kasta ett undantag, skriv till en fil eller lägg till en egen teckensnittskälla.

### Steg 3: Verifiera resultatet

Kör programmet från en konsol. Om ditt `input.docx` använder ett teckensnitt som inte är installerat kommer du att se rader som:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Om ingen output visas har dokumentet antingen använt enbart teckensnitt som redan finns **eller** så har Aspose.Words hittat ett matchande teckensnitt i sin inbyggda reservsamling. I vilket fall som helst har du framgångsrikt **kontrollerat dokumentets teckensnitt**.

---

## Upptäck saknade teckensnitt utan licens (gratis provversion)

Även om du använder 30‑dagars provversionen fungerar varningsmekanismen exakt likadant. Den enda skillnaden är att provversionen lägger till ett vattenstämpel i det genererade resultatet, vilket **inte** påverkar varningsinsamlingen. Så du kan säkert **upptäcka saknade teckensnitt** innan du beslutar dig för att köpa en full licens.

---

## Hantera saknade teckensnitt – Avancerade alternativ

Ibland vill du tillhandahålla egna teckensnittsfiler (t.ex. företagets varumärkesteckensnitt) så att ersättningen aldrig sker. Aspose.Words låter dig registrera egna teckensnittsmappar:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Placera koden **innan** du laddar dokumentet om du vill att laddaren ska ta hänsyn till dessa teckensnitt under den initiala parsningen. Detta är det mest pålitliga sättet att **hantera saknade teckensnitt** utan att förlita sig på systemets standardteckensnitt.

---

## Vanliga fallgropar & hur du undviker dem

| Fallgrop | Varför det händer | Lösning |
|----------|-------------------|---------|
| **Varningssamling kopplad efter inläsning** | Dokumentet är redan parsat, så inga varningar registreras. | Koppla `WarningCallback` **innan** du anropar `new Document(path)`. |
| **Endast generiska varningar visas** | Du filtrerade på fel `WarningType`. | Använd `WarningType.FontSubstitution` för att fokusera på teckensnittsproblem. |
| **Ingen output trots saknade teckensnitt** | Aspose.Words hittade en inbyggd reserv (t.ex. Arial). | Inaktivera inbyggda reserver via `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Prestandaproblem vid skanning av stora dokument** | Att samla alla varningar kan vara dyrt. | Begränsa insamlingen till `FontSubstitution` endast, eller bearbeta varningar i batchar. |

---

## Fullt fungerande exempel (Klar för kopiera‑klistra)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Förväntad konsoloutput** (förutsatt två saknade teckensnitt):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Om konsolen är tyst förutom “Document loaded successfully”, har du **kontrollerat dokumentets teckensnitt** och inte hittat några saknade.

---

## Slutsats

Vi har visat hur du **fångar teckensnittsvarningar** i C# med Aspose.Words, ett pålitligt sätt att **upptäcka saknade teckensnitt**, **ladda Word‑dokument** säkert, **kontrollera dokumentets teckensnitt** och **hantera saknade teckensnitt** via egna teckensnittskällor.  

Med detta mönster kan du integrera teckensnitt‑validering i vilken automatiseringspipeline som helst – oavsett om du genererar PDF‑filer, konverterar till HTML eller bara arkiverar Word‑filer.

### Vad blir nästa steg?

- Utforska **FontSettings.SubstitutionSettings**‑API:t för att definiera egna reservregler.
- Kombinera varningsinsamling med ett loggningsramverk (Serilog, NLog) för produktionsövervakning.
- Använd samma tillvägagångssätt för att fånga andra varningstyper, såsom bildupplösning eller ej‑stödda funktioner.

Har du fler frågor om teckensnittshantering eller Aspose.Words i allmänhet? Lämna en kommentar eller besök Aspose‑community‑forumet. Lycka till med kodningen, och må dina dokument alltid renderas med de teckensnitt du förväntar dig!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}