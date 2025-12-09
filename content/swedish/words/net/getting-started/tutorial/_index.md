---
language: sv
url: /swedish/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Upptäck saknade teckensnitt i Aspose.Words‑dokument – Komplett C#‑guide

Har du någonsin funderat på hur du **upptäcker saknade teckensnitt** när du laddar en Word‑fil med Aspose.Words? I mitt dagliga arbete har jag stött på några PDF‑filer som såg felaktiga ut eftersom originaldokumentet använde ett teckensnitt jag inte hade installerat. Den goda nyheten? Aspose.Words kan berätta exakt när det ersätter ett teckensnitt, och du kan fånga den informationen med ett enkelt varnings‑callback.

I den här handledningen går vi igenom ett **komplett, körbart exempel** som visar hur du loggar varje teckensnittsersättning, varför callbacken är viktig, och ett par extra knep för robust upptäckt av saknade teckensnitt. Inga onödiga utsvävningar, bara koden och resonemanget du behöver för att få det att fungera idag.

---

## Vad du kommer att lära dig

- Hur du implementerar **Aspose.Words varnings‑callback** för att fånga teckensnittsersättnings‑händelser.  
- Hur du konfigurerar **LoadOptions C#** så att callbacken anropas när ett dokument laddas.  
- Hur du verifierar att upptäckten av saknade teckensnitt verkligen fungerade, och hur konsolutdata ser ut.  
- Valfria justeringar för stora batcher eller huvudlösa miljöer.  

**Förkunskaper** – Du behöver en aktuell version av Aspose.Words för .NET (koden testades med 23.12), .NET 6 eller senare, och en grundläggande förståelse för C#. Om du har detta är du redo att köra.

---

## Upptäck saknade teckensnitt med en varnings‑callback

Kärnan i lösningen är en implementation av `IWarningCallback`. Aspose.Words avfyrar ett `WarningInfo`‑objekt för många situationer, men vi är bara intresserade av `WarningType.FontSubstitution`. Låt oss se hur vi kopplar in det.

### Steg 1: Skapa en teckensnitt‑varningssamling

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Varför detta är viktigt*: Genom att filtrera på `WarningType.FontSubstitution` undviker vi skräp från orelaterade varningar (som föråldrade funktioner). `info.Description` innehåller redan det ursprungliga teckensnittets namn och ersättningen, vilket ger dig ett tydligt revisionsspår.

---

## Konfigurera LoadOptions för att använda callbacken

Nu säger vi åt Aspose.Words att använda vår samlare när den laddar en fil.

### Steg 2: Ställ in LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Varför detta är viktigt*: `LoadOptions` är den enda platsen där du kan ansluta callbacken, krypteringslösenord och andra laddningsbeteenden. Att hålla den separerad från `Document`‑konstruktorn gör koden återanvändbar för många filer.

---

## Ladda dokumentet och fånga saknade teckensnitt

Med callbacken på plats är nästa steg helt enkelt att ladda dokumentet.

### Steg 3: Ladda ditt DOCX (eller något annat stödd format)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

När `Document`‑konstruktorn parsar filen triggas vår `FontWarningCollector` för varje saknat teckensnitt. Konsolen visar rader som:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Den raden är det konkreta beviset på att **upptäcka saknade teckensnitt** fungerade.

---

## Verifiera utdata – Vad du kan förvänta dig

Kör programmet från en terminal eller Visual Studio. Om källdokumentet innehåller ett teckensnitt du inte har installerat kommer du att se minst en rad med “Font substituted”. Om dokumentet bara använder installerade teckensnitt förblir callbacken tyst och du får bara meddelandet “Document loaded successfully.”

**Tips**: För att dubbelkolla, öppna Word‑filen i Microsoft Word och titta på teckensnittlistan. Alla teckensnitt som visas i *Replace Fonts* under *Home → Font*‑gruppen är kandidater för ersättning.

---

## Avancerat: Upptäck saknade teckensnitt i bulk

Ofta behöver du skanna dussintals filer. Samma mönster skalar bra:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Eftersom `FontWarningCollector` skriver till konsolen varje gång den anropas får du en per‑fil‑rapport utan extra kod. För produktionsscenarier kanske du vill logga till en fil eller en databas – byt helt enkelt ut `Console.WriteLine` mot din föredragna logger.

---

## Vanliga fallgropar & Pro‑tips

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| **Inga varningar visas** | Dokumentet innehåller faktiskt bara installerade teckensnitt. | Verifiera genom att öppna filen i Word eller genom att medvetet ta bort ett teckensnitt från ditt system. |
| **Callbacken anropas inte** | `LoadOptions.WarningCallback` tilldelades aldrig eller en ny `LoadOptions`‑instans användes senare. | Behåll ett enda `LoadOptions`‑objekt och återanvänd det för varje laddning. |
| **För många orelaterade varningar** | Du filtrerade inte på `WarningType.FontSubstitution`. | Lägg till villkoret `if (info.Type == WarningType.FontSubstitution)` som visas. |
| **Prestandaförsämring på stora filer** | Callbacken körs för varje varning, vilket kan vara många för stora dokument. | Inaktivera andra varningstyper via `LoadOptions.WarningCallback` eller sätt `LoadOptions.LoadFormat` till en specifik typ om du vet den. |

---

## Fullt fungerande exempel (Kopiera‑klistra‑klart)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Förväntad konsolutdata** (när ett saknat teckensnitt påträffas):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Om ingen ersättning sker ser du bara framgångsmeddelandet.

---

## Slutsats

Du har nu ett **komplett, produktionsklart sätt att upptäcka saknade teckensnitt** i vilket dokument som helst som bearbetas av Aspose.Words. Genom att utnyttja **Aspose.Words varnings‑callback** och konfigurera **LoadOptions C#**, kan du logga varje teckensnittsersättning, felsöka layout‑problem och säkerställa att dina PDF‑filer behåller det avsedda utseendet.

Från en enskild fil till en massiv batch förblir mönstret detsamma – implementera `IWarningCallback`, anslut den till `LoadOptions`, och låt Aspose.Words göra det tunga lyftet.

Redo för nästa steg? Prova att kombinera detta med **font embedding** eller **fallback font families** för att automatiskt åtgärda problemet, eller utforska **DocumentVisitor**‑API:t för djupare innehållsanalys. Lycka till med kodningen, och må alla dina teckensnitt stanna där du förväntar dig dem!

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}