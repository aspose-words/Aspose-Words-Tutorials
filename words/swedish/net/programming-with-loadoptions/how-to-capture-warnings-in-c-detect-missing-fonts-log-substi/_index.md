---
category: general
date: 2026-04-04
description: Lär dig hur du fångar varningar, upptäcker saknade teckensnitt och loggar
  ersättningshändelser med Aspose.Words LoadOptions i C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: sv
og_description: Hur man fångar varningar, upptäcker saknade teckensnitt och loggar
  ersättningsevent med Aspose.Words LoadOptions i C#.
og_title: Hur man fångar varningar i C# – Upptäck saknade typsnitt och logga ersättning
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Hur man fångar varningar i C# – Upptäck saknade typsnitt och logga ersättning
url: /sv/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man fångar varningar i C# – Upptäcker saknade typsnitt & loggar ersättningar

Har du någonsin undrat **hur man fångar varningar** som dyker upp när du laddar ett Word‑dokument med saknade typsnitt? Du är inte ensam. I många verkliga projekt går typsnitt förlorade under migrering, och den tysta reservlösningen kan förstöra din layout. Den goda nyheten? Aspose.Words ger dig ett rent sätt att lyssna på dessa varningar, upptäcka saknade typsnitt och till och med logga varje ersättning så att du kan åtgärda källan senare.

I den här handledningen går vi igenom en komplett, färdig‑att‑köra‑lösning som visar **hur man fångar varningar**, demonstrerar **upptäckt av saknade typsnitt** och förklarar **hur man loggar ersättnings**‑händelser. I slutet har du en återanvändbar varningshanterare, ett fullt konfigurerat `LoadOptions`‑objekt och ett exempel på konsolutdata som du kan verifiera.

> **Förutsättning:** Du behöver Aspose.Words för .NET (v24.x eller senare) installerat via NuGet och en grundläggande C#‑utvecklingsmiljö (Visual Studio 2022 eller VS Code fungerar bra).

---

## Hur man fångar varningar vid inläsning av dokument

Kärnan i lösningen är en klass som implementerar `IWarningCallback`. Aspose.Words anropar detta återuppringnings‑callback automatiskt för varje varning som genereras under dokumentinläsning, inklusive varningar om typsnittsersättning.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Varför detta steg?**  
> Genom att filtrera på `WarningType.FontSubstitution` undviker vi röran från orelaterade varningar (som föråldrade funktioner). Detta gör loggen fokuserad på det exakta problemet du bryr dig om—saknade typsnitt.

---

## Upptäck saknade typsnitt med Aspose.Words

När ett dokument refererar till ett typsnitt som inte är installerat på maskinen, ersätter Aspose.Words det närmaste matchande typsnittet och ger en varning. Vår hanterare ovan fångar varje förekomst, vilket effektivt **upptäcker saknade typsnitt**.

För att se det i praktiken måste vi konfigurera `LoadOptions` och fästa hanteraren:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tips:** Om du föredrar att samla varningar för senare bearbetning (t.ex. skriva till en fil), ersätt `Console.WriteLine` med kod som lägger till meddelandet i en `List<string>`.

---

## Hur man loggar ersättningshändelser

Loggning är så enkelt som att rikta varningsutdata till ett beständigt lagringsställe. Nedan är ett snabbt exempel som skriver varje ersättningsvarning till en textfil med namnet `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Varför logga till en fil?**  
> Beständiga loggar låter dig granska typsnittsproblem över flera körningar, automatisera varningar eller mata in data i en bygg‑pipeline‑kontroll.

---

## Fullt fungerande exempel

När vi sätter ihop allt, här är en fristående konsolapplikation som du kan kopiera, klistra in och köra. Den demonstrerar **hur man fångar varningar**, **upptäcker saknade typsnitt** och **hur man loggar ersättningar** i ett svep.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Förväntad konsolutdata

Om `input.docx` refererar till ett typsnitt som inte är installerat, kommer du att se något liknande:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Om du bytte till `FileLoggingWarningHandler` kommer samma rader att visas i `font-warnings.log` med tidsstämplar.

![hur man fångar varningskonsolutdata](image-placeholder.png)

---

## Vanliga frågor & kantfall

### Vad händer om jag behöver fånga *alla* varningar, inte bara typsnittsersättningar?

Ta helt enkelt bort `if (info.Type == WarningType.FontSubstitution)`‑kontrollen. Callback‑metoden kommer att ta emot varje varningstyp (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, etc.). Du kan sedan grena på `info.Type` för att hantera varje fall på olika sätt.

### Fungerar detta med PDF‑filer eller bara Word‑dokument?

`LoadOptions` och `IWarningCallback` är en del av Aspose.Words, så de gäller för Word‑kompatibla format (`.docx`, `.doc`, `.rtf`, `.html`). För PDF‑filer använder du Aspose.PDF:s egna varningsmekanismer.

### Hur kan jag undertrycka varningar istället för att logga dem?

Sätt `LoadOptions.WarningCallback = null` eller implementera callback‑metoden men låt metodkroppen vara tom. Biblioteket kommer fortfarande att utföra ersättningen tyst.

### Vad gäller trådsäkerhet?

Callback‑instansen anropas på samma tråd som laddar dokumentet, så du behöver ingen extra synkronisering såvida du inte delar hanteraren över parallella laddningar. I så fall skydda delade resurser (t.ex. loggfilen) med en låsning eller använd samtidiga samlingar.

---

## Slutsats

Vi har gått igenom **hur man fångar varningar** från Aspose.Words, visat dig hur **man upptäcker saknade typsnitt**, och förklarat **hur man loggar ersättnings**‑händelser för senare analys. Genom att ansluta en enkel `IWarningCallback`‑implementation till `LoadOptions` får du full insyn i typsnittsrelaterade problem utan att skräpa ner din kodbas.

Nästa steg? Prova att utöka loggern för att skicka e‑post, integrera med Azure Monitor eller automatiskt installera saknade typsnitt på en byggserver. Du kan också utforska andra varningstyper—`WarningType.DegradedDocument` kan varna dig för funktioner som inte överlevde konverteringsprocessen.

Har du fler frågor om typsnittshantering eller Aspose.Words i allmänhet? Lämna en kommentar eller öppna ett nytt ärende på Aspose‑forumet. Lycka till med kodningen, och må dina dokument alltid renderas med rätt teckensnitt!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}