---
category: general
date: 2026-06-08
description: Lär dig hur du använder LoadOptions i Aspose.Words för att upptäcka saknade
  teckensnitt vid dokumentimport. Steg‑för‑steg‑guide med kod, förklaringar och bästa
  praxis.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: sv
og_description: Hur man använder LoadOptions i Aspose.Words och upptäcker saknade
  teckensnitt vid inläsning av ett dokument. Komplett guide med kod och praktiska
  tips.
og_title: Hur man använder LoadOptions för att upptäcka saknade teckensnitt
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Hur man använder LoadOptions för att upptäcka saknade teckensnitt
url: /sv/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man använder LoadOptions för att upptäcka saknade teckensnitt

Har du någonsin undrat **hur man använder LoadOptions** när man laddar ett Word‑dokument med Aspose.Words? I den här handledningen visar vi exakt **hur man använder LoadOptions** för att **upptäcka saknade teckensnitt** och hantera dem på ett smidigt sätt. Oavsett om du bygger en dokumentkonverteringstjänst eller en rapportmotor, kan saknade teckensnitt orsaka oväntade layout‑överraskningar, så att fånga dem tidigt är ett måste.

Vi går igenom varje steg—från att koppla en varnings‑callback till att tolka resultaten—så att du får ett fullt fungerande C#‑exempel som du kan lägga in i vilket .NET‑projekt som helst. Inga externa dokument, bara en självständig lösning. I slutet vet du varför varningssystemet finns, hur du aktiverar det och vad du ska göra när callbacken triggas.

## Förutsättningar

- **Aspose.Words for .NET** (valfri nyare version; API‑et vi använder är stabilt sedan 2022).
- En .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code med C#‑tillägget).
- En exempel‑Word‑fil (`input.docx`) som refererar till ett teckensnitt du *inte* har installerat på maskinen.

Det är allt—inga extra NuGet‑paket utöver Aspose.Words.

## Så här använder du LoadOptions med Aspose.Words

**LoadOptions**‑klassen är porten till att anpassa hur ett dokument läses. Genom att ansluta en varnings‑callback till den kan du **upptäcka saknade teckensnitt** så snart Aspose.Words analyserar filen. Låt oss gå igenom det.

### Steg 1: Skapa en varningshanterare

Aspose.Words använder `IWarningCallback`‑gränssnittet för att meddela dig om icke‑kritiska problem, såsom teckensnittssubstitution. Implementera gränssnittet och bestäm vad som ska göras när en varning anländer.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Varför detta är viktigt:**  
Utan en callback byter Aspose.Words tyst ut saknade teckensnitt mot ett standardteckensnitt (vanligtvis Arial). Genom att fånga `FontSubstitution`‑varningen kan du logga problemet, varna användaren eller till och med ersätta det saknade teckensnittet med en egen reserv.

### Steg 2: Anslut hanteraren till LoadOptions

Nu skapar vi en `LoadOptions`‑instans och talar om för den att använda vår `FontWarningHandler`. Det är här **hur man använder LoadOptions** verkligen lyser.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Varför detta är viktigt:**  
`LoadOptions` är en allt‑i‑ett‑lösning för många import‑tidsinställningar (kodning, lösenord osv.). Genom att sätta `WarningCallback` aktiverar du en lättviktig, händelse‑driven mekanism som fungerar för alla dokument du laddar med dessa alternativ.

### Steg 3: Ladda dokumentet med de konfigurerade alternativen

Till sist matar vi `LoadOptions` i `Document`‑konstruktorn. Om källfilen refererar till ett teckensnitt som inte är installerat, kommer Aspose.Words att avfyra varningen och din hanterare kommer att skriva ut ett meddelande.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Vad du kommer att se:**  
Om vi antar att `input.docx` använder ett teckensnitt som heter *“MyCustomFont”* som inte finns på maskinen, kommer konsolutdata att se ut så här:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Om alla teckensnitt finns, förblir callbacken tyst—ingen utskrift, ingen prestandapåverkan.

## Upptäck saknade teckensnitt med en varnings‑callback (sekundärt nyckelord i aktion)

Frasen **detect missing fonts** förekommer naturligt i rubriken ovan, vilket förstärker det sekundära nyckelordet. Låt oss utforska några variationer du kan stöta på i riktiga projekt.

### Flera dokument i en loop

Ofta bearbetar du en mängd filer. Samma `LoadOptions`‑instans kan återanvändas, men kom ihåg att `WarningCallback` kvarstår mellan laddningar. Om du behöver isolering per dokument, skapa en ny `LoadOptions` för varje iteration.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Anpassad logik för teckensnittssubstitution

Istället för att bara logga kan du vilja ersätta ett specifikt saknat teckensnitt med ett företags‑godkänt alternativ. Utöka hanteraren:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Nu upptäcker du inte bara **detect missing fonts**, du bestämmer också hur du ska ersätta dem.

### Tysta oönskade varningar

Om du bara bryr dig om teckensnittsproblem och vill undertrycka allt annat, filtrera på `WarningType` som visas. Omvänt, för att logga *alla* varningar, ta bort `if`‑kontrollen och skriv ut `info.WarningType` tillsammans med `info.Description`.

## Fullständigt, körbart exempel

Genom att sätta ihop allt får du ett komplett program som du kan kompilera och köra. Ersätt `"YOUR_DIRECTORY/input.docx"` med sökvägen till din testfil.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Förväntad konsolutdata (när ett teckensnitt saknas):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Om inga teckensnitt saknas ser du helt enkelt:

```
Document loaded successfully.
```

## Vanliga fallgropar & pro‑tips

- **Fallgrop:** Glömmer att sätta `WarningCallback`. API‑et kommer fortfarande att ersätta teckensnitt, men du får aldrig veta att det hände.  
  **Pro‑tips:** Anslut alltid en hanterare när du behöver teckensnittstrohet; det kostar praktiskt taget inget.

- **Fallgrop:** 

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man upptäcker teckensnitt i Aspose.Words – Hantera varningar & inställningar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Hur man fångar teckensnitt i Aspose.Words – Komplett guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Hur man laddar DOCX och upptäcker saknade teckensnitt – Komplett C#‑guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}