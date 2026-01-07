---
category: general
date: 2026-01-06
description: Lär dig hur du får varningar när du laddar dokument och hur du övervakar
  teckensnitt med Aspose.Words. Denna guide täcker varningsåteruppringningar och spårning
  av teckensnittssubstitution.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: sv
og_description: Hur får du varningar i Aspose.Words? Följ den här steg‑för‑steg‑handledningen
  för att övervaka teckensnitt och fånga substitutionsmeddelanden när du laddar dokument.
og_title: Hur man får varningar i Aspose.Words – övervaka teckensnitt
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Hur man får varningar i Aspose.Words – övervaka teckensnitt i C#
url: /sv/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man får varningar i Aspose.Words – Övervaka teckensnitt i C#

Har du någonsin undrat **hur man får varningar** när ett Word‑dokument innehåller teckensnitt som du inte har installerade? Det är ett vanligt problem – din app byter tyst ut saknade teckensnitt och du får aldrig veta vad som förändrades. Den goda nyheten är att du kan knyta dig till Aspose.Words varningssystem och **övervaka teckensnitt** i realtid.

I den här handledningen visar vi exakt hur du fångar de varningar som gäller teckensnitts‑substitution, varför det är viktigt och vad du kan göra med informationen när du har den. Inga externa dokument, bara ett komplett, körbart exempel som du kan klistra in i Visual Studio just nu.

> **Pro tip:** Om du bygger en dokument‑konverteringspipeline sparar loggning av saknade teckensnitt tidigt dig från obehagliga layout‑överraskningar längre ner i kedjan.

---

## Vad du behöver

- **Aspose.Words for .NET** (senaste versionen; API‑et har inte förändrats sedan v23.10)
- En .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code med C#‑tillägget)
- Ett exempel‑`.docx`‑dokument som refererar till ett teckensnitt du inte har installerat (t.ex. **“NonExistentFont”**)

Det är allt – inga extra NuGet‑paket utöver Aspose.Words.

---

## Steg 1 – Skapa en varningssamling (Primary Keyword in Header)

Det första du behöver är en plats att lagra varningar när de uppstår. Aspose.Words tillhandahåller egenskapen `WarningCallback` på `LoadOptions` just för detta ändamål.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Varför detta är viktigt:**  
När biblioteket stöter på ett saknat teckensnitt kastar det inte ett undantag; det avger ett `WarningInfo`‑objekt. Genom att koppla en samlare får du full insyn i varje substitutions‑händelse, vilket låter dig **övervaka teckensnitt** utan att förorena konsolen med irrelevanta meddelanden.

---

## Steg 2 – Läs in dokumentet med varningsaktiverade alternativ

Nu läser vi faktiskt in filen. `LoadOptions` som vi förberedde i föregående steg säkerställer att alla teckensnittsrelaterade varningar fångas.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Vad som händer under huven?**  
Aspose.Words parsar Word‑filen, löser upp teckensnitt och när det inte kan hitta ett begärt teckensnitt faller det tillbaka på ett substitut (vanligtvis Arial). Detta substitut triggar en `WarningType.FontSubstitution`‑varning, som hamnar i `warningCollector`.

---

## Steg 3 – Inspektera de insamlade varningarna (Primary Keyword Appears Again)

Efter att dokumentet har lästs in itererar vi helt enkelt över `warningCollector` och skriver ut eventuella teckensnitts‑substitutions‑meddelanden.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Förväntad utskrift** (förutsatt att det saknade teckensnittet är *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Om dokumentet innehåller flera okända teckensnitt ser du en rad per substitution – perfekt för loggning eller avisering.

---

## Steg 4 – Valfritt: Logga eller spara varningsinformationen

I produktion vill du förmodligen ha mer än ett `Console.WriteLine`. Här är ett snabbt exempel som skriver varningarna till en JSON‑fil för senare analys.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Nu har du en permanent post som du kan föra in i en övervaknings‑dashboard, eller till och med trigga en automatiserad begäran om de saknade teckensnitts‑filerna.

---

## Steg 5 – Verifiera resultatet och rensa upp

Kör programmet. Om du ser substitutions‑meddelandena har du lyckats **få varningar** och övervakar nu aktivt **teckensnitt**. Om inget visas, dubbelkolla att testdokumentet verkligen refererar till ett teckensnitt som inte är installerat på maskinen.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

En noll‑räkning betyder oftast antingen:

1. Alla teckensnitt löstes (kanske är teckensnittet *installerat* lokalt), eller
2. Dokumentet innehöll inga teckensnittsreferenser som behövde substitution.

---

## Vanliga fallgropar & hur du undviker dem

| Fallgrop | Varför det händer | Lösning |
|----------|-------------------|---------|
| **Inga varningar visas** | Teckensnittet finns faktiskt på systemet, eller dokumentet använder bara inbyggda teckensnitt. | Byt namn på teckensnittet i källfilen till något omöjligt (t.ex. `XYZ123`) och försök igen. |
| **För många varningar (brus)** | Du laddar många dokument i en loop utan att rensa samlaren. | Skapa en ny `WarningInfoCollection` för varje dokument, eller anropa `warningCollector.Clear()` efter bearbetning. |
| **Prestandapåverkan** | Överdriven loggning till disk kan sakta ner batch‑bearbetning. | Buffra varningar i minnet och skriv dem i bulk, eller använd asynkron fil‑I/O. |
| **Saknad `using Aspose.Words.Loading;`** | Klassen `LoadOptions` finns i detta namnrum. | Lägg till den saknade `using`‑direktivet, som visas i Steg 1. |

---

## Utöka lösningen – Övervaka andra varningstyper

Medan teckensnitts‑substitution är den mest synliga, kan Aspose.Words avge varningar för:

- **Föråldrade funktioner** (`WarningType.Deprecated`),
- **Möjlig dataförlust** (`WarningType.DataLoss`),
- **Ej stödda filformat** (`WarningType.UnsupportedFileFormat`).

Du kan bredda filtret i Steg 3 för att fånga dessa också:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

På så sätt handlar det inte bara om **hur man övervakar teckensnitt**, utan också **hur man får varningar** för alla scenarier din applikation kan stöta på.

---

## Fullt fungerande exempel (Kopiera‑klistra redo)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Kör det:** Bygg projektet, kör det, och du kommer att se varningarna skrivas ut och sparas. Det är det kompletta svaret på **hur man får varningar** och **hur man övervakar teckensnitt** med Aspose.Words.

---

## Slutsats

Du vet nu **hur man får varningar** från Aspose.Words, specifikt för teckensnitts‑substitution, och du har lärt dig **hur man övervakar teckensnitt** genom hela dokument‑laddningsprocessen. Genom att koppla en `WarningCallback`, iterera de insamlade `WarningInfo`‑objekten och eventuellt persistera datan får du full transparens över saknade‑teckensnitt‑händelser – en väsentlig funktion för alla dokument‑bearbetningspipeline.

Nästa steg? Prova att utöka varningsfiltret för att täcka data‑förlust eller föråldrade‑funktion‑varningar, eller integrera JSON‑loggen i en övervakningsdashboard som Grafana. Samma mönster fungerar för alla varningstyper, så du är väl rustad att hålla ett öga på alla problem som Aspose.Words kan kasta din väg.

Lycka till med kodningen, och må dina dokument alltid renderas exakt som du förväntar dig! 

---

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}