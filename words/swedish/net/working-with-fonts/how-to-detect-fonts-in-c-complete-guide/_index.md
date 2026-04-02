---
category: general
date: 2026-04-02
description: Hur man upptäcker typsnitt i C#-dokument med Aspose.Words. Lär dig att
  konfigurera teckensnittsinställningar och hantera saknade typsnitt effektivt.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: sv
og_description: Hur man upptäcker typsnitt i C#‑dokument med Aspose.Words. Denna guide
  visar hur du konfigurerar teckensnittsinställningar och hanterar saknade typsnitt.
og_title: Hur man upptäcker typsnitt i C# – Komplett guide
tags:
- C#
- Aspose.Words
- Document Processing
title: Hur man upptäcker typsnitt i C# – Komplett guide
url: /sv/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man upptäcker teckensnitt i C# – Komplett guide

Har du någonsin funderat **hur man upptäcker teckensnitt** som saknas eller ersätts när du laddar ett Word‑dokument i .NET? Du är inte ensam – utvecklare stöter ständigt på problemet när ett dokument refererar till ett teckensnitt som inte är installerat på servern. Den goda nyheten är att Aspose.Words ger dig ett rent, programatiskt sätt att identifiera dessa luckor.

I den här handledningen går vi igenom ett praktiskt exempel som inte bara visar **hur man upptäcker teckensnitt**, utan också demonstrerar hur man **konfigurerar teckensnittsinställningar** och **hanterar saknade teckensnitt** på ett smidigt sätt. I slutet har du ett färdigt kodexempel som skriver ut varje varning om teckensnittsersättning, så att du kan logga, larma eller ersätta teckensnitt efter behov.

---

## Vad du behöver

- **Aspose.Words for .NET** (senaste versionen fungerar bäst; koden nedan riktar sig mot .NET 6+)
- En .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code)
- Ett exempel‑`.docx`‑dokument som refererar till ett teckensnitt du inte har installerat (perfekt för test)

Inga extra NuGet‑paket utöver Aspose.Words behövs, och lösningen fungerar på Windows, Linux och macOS.

---

## Steg 1: Installera och referera Aspose.Words

Börja med att lägga till biblioteket i ditt projekt. NuGet‑kommandot är enkelt:

```bash
dotnet add package Aspose.Words
```

> **Proffstips:** Om du kör på en CI‑server, lås paketversionen för att undvika oväntade brytande förändringar.

---

## Steg 2: Konfigurera teckensnittsinställningar (och förbered Load‑alternativ)

Innan du öppnar ett dokument kan du tala om för Aspose.Words var den ska leta efter reservteckensnitt. Detta är delen **konfigurera teckensnittsinställningar** som förhindrar att motorn tyst byter teckensnitt du kanske inte vill ha.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Varför bry sig? Om dokumentet refererar till *Comic Sans* men din server bara har *Calibri*, kommer Aspose.Words att ersätta *Calibri* och ge en varning. Genom att konfigurera sökvägen minskar du oönskade överraskningar.

---

## Steg 3: Ladda dokumentet med de förberedda alternativen

Nu öppnar vi faktiskt filen. `LoadOptions` som vi byggde i föregående steg skickas direkt till `Document`‑konstruktorn.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Om filen inte kan hittas eller är korrupt kastas ett undantag – så du kanske vill omsluta detta med try/catch i produktionskod.

---

## Steg 4: Skanna dokumentvarningarna för teckensnittsersättningar

Aspose.Words samlar en lista med varningar medan den parsar. Bland dem visar `FontSubstitutionWarning` exakt vilket teckensnitt som byttes.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

`Warnings`‑samlingen kan också innehålla andra objekt (t.ex. `DocumentStructureWarning`). Genom att filtrera på `FontSubstitutionWarning` säkerställer vi att vi bara rapporterar scenariot **hantera saknade teckensnitt** som vi är intresserade av.

---

## Steg 5: Sätt ihop allt – Ett komplett, körbart exempel

Nedan är hela programmet. Kopiera‑klistra in det i en ny konsolapp och kör; du kommer att se varje saknat teckensnitt skrivet till konsolen.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Förväntad output** (exempel):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Om dokumentet endast använder teckensnitt som finns på maskinen, kommer du istället att se raden “No font substitutions detected”.

---

## Edge Cases & Vanliga frågor

### Vad händer om dokumentet innehåller **inga varningar** alls?

Det betyder helt enkelt att varje refererat teckensnitt hittades i de sökmappar du konfigurerade. Flaggan `anySubstitutions` i exemplet hanterar detta fall.

### Kan jag **logga** varningar till en fil istället för konsolen?

Absolut. Byt ut `Console.WriteLine`‑anropen mot en logger du föredrar (Serilog, NLog osv.). `WarningInfo`‑objektet exponerar också `WarningType` och `WarningMessage` om du behöver mer detaljer.

### Hur **ignorerar** jag vissa teckensnitt, som ett företagsvarumärkes‑teckensnitt som aldrig får bytas?

Du kan lägga till en anpassad ersättningsregel:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Nu kommer Aspose.Words endast att ersätta *MyBrandFont* med de listade alternativen, och du får fortfarande en varning som du kan agera på.

### Fungerar detta i **Linux**‑containrar?

Ja – se bara till att du monterar en mapp med de nödvändiga `.ttf`/`.otf`‑filerna och pekar `SetFontsFolder` mot den. Aspose.Words är inte beroende av OS‑installerade teckensnitt.

---

## Visuell översikt

![how to detect fonts flowchart](detect-fonts.png "Diagram som visar stegen för att upptäcka teckensnitt i ett dokument")

*Bildtext:* **hur man upptäcker teckensnitt**‑flödesschema som illustrerar konfiguration, laddning och varningsinspektion.

---

## Sammanfattning – Vad vi har lärt oss

- **Hur man upptäcker teckensnitt** som saknas eller ersätts med hjälp av Aspose.Words‑varningar.  
- Hur man **konfigurerar teckensnittsinställningar** för att peka på egna teckensnittsmappar och ange en standardfallback.  
- Strategier för att **hantera saknade teckensnitt**, från loggning till anpassade ersättningsregler.

Allt detta ryms i en kompakt, självständig konsolapp som du kan släppa in i vilken .NET‑lösning som helst.

---

## Nästa steg & Relaterade ämnen

- **Bädda in teckensnitt** direkt i utdata‑dokumentet för att undvika framtida ersättningar (`SaveOptions` med `EmbedFullFonts`).  
- **Programmatisk teckensnittsbyte** – ersätt saknade teckensnitt med ett specifikt alternativ innan du sparar.  
- **Prestandaoptimering** – cacha `FontSettings` när du bearbetar många dokument i ett batch‑flöde.  

Om du är intresserad av dessa ämnen, sök efter *configure font settings* och *handle missing fonts* – de leder dig till djupare guider om teckensnittshantering med Aspose.Words.

---

Happy coding! Got a weird font edge case? Drop a comment, and we’ll troubleshoot together.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}