---
category: general
date: 2026-04-21
description: Lär dig hur du upptäcker teckensnitt, fångar varningar, konfigurerar
  återanrop och enumererar varningar med Aspose.Words i C#. Steg‑för‑steg‑guide för
  pålitlig teckensnittshantering.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: sv
og_description: Hur upptäcker man teckensnitt i Aspose.Words? Den här handledningen
  visar hur du fångar varningar, konfigurerar en återuppringning och enumererar varningar
  i C#.
og_title: Hur man upptäcker typsnitt i Aspose.Words – Komplett guide
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man upptäcker teckensnitt i Aspose.Words – Komplett guide
url: /sv/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så upptäcker du teckensnitt i Aspose.Words – Komplett guide

Har du någonsin funderat **hur man upptäcker teckensnitt** som saknas när du laddar ett Word‑dokument? Det är ett scenario som dyker upp oftare än du kanske vill, särskilt när du arbetar med äldre filer eller tvär‑plattform‑distributioner. I den här handledningen går vi igenom ett komplett, körbart exempel som **fångar varningar**, **konfigurerar en callback** och **enumererar varningar** så att du alltid vet vilka teckensnitt som ersattes.

Vi kommer att använda Aspose.Words for .NET (v24.9 vid skrivandet) och ren C#. Inga externa tjänster, ingen magi – bara API‑et och några rader kod. När du är klar kan du identifiera varje teckensnittssubstitution, logga den och till och med bestämma om du ska avbryta inläsningen om ett kritiskt teckensnitt saknas.  

### Vad du behöver
- **Aspose.Words for .NET** (installera via NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 eller senare (koden fungerar även på .NET Framework)
- Ett exempel‑DOCX som refererar till ett teckensnitt som inte finns på maskinen (t.ex. “MyCustomFont.ttf”)
- Visual Studio, Rider eller någon annan C#‑editor du föredrar

> **Pro tip:** Om du inte har ett dokument med saknade teckensnitt, byt helt enkelt namn på en teckensnittsfil på ditt system eller redigera DOCX‑XML‑filen så att den refererar till en icke‑existerande teckensnittsfamilj.

---

## Så upptäcker du teckensnitt med Aspose.Words

Kärnidén är att knyta in dig i Aspose.Words varningssystem. När biblioteket inte kan hitta ett efterfrågat teckensnitt, skickar det en varning av typen `WarningType.FontSubstitution`. Genom att tillhandahålla en egen implementation av `IWarningCallback` kan du **upptäcka teckensnitt** som byttes ut under inläsningsprocessen.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Why this works:** Aspose.Words calls the `Warning` method for every non‑critical issue. By storing the `WarningInfo` objects you get full access to the type, message, and context, which is exactly what you need to **detect fonts** that were substituted.

---

## Så fångar du varningar när du laddar ett dokument

Nu när vi har en samlare måste vi tala om för `LoadOptions` att använda den. Detta är **hur man fångar varningar**‑delen av pusslet.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Edge case:** If you load a document from a stream (`new Document(stream, loadOptions)`), the same callback works—just pass the stream instead of a file path.

I det här skedet är dokumentet helt inläst, men eventuella varningar om teckensnittssubstitution har säkert lagrats i `warningCollector.Warnings`.

---

## Så enumererar du varningar och rapporterar teckensnittssubstitutioner

Till sist går vi igenom de insamlade varningarna och **enumererar varningar** som specifikt handlar om teckensnittssubstitution. Detta steg omvandlar rådata till en läsbar rapport.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Förväntad utskrift** (exempel):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Om dokumentet inte innehåller några saknade teckensnitt så producerar loopen helt enkelt ingen utskrift – inget att oroa sig för.

---

## Fullt fungerande exempel (Alla steg i en fil)

Nedan finns det kompletta programmet som du kan kopiera‑klistra in i ett konsolprojekt. Det binder ihop **hur man upptäcker teckensnitt**, **hur man fångar varningar**, **hur man konfigurerar callback** och **hur man enumererar varningar** i ett enda, sammanhållet flöde.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Kör detta program** så skrivs varje teckensnitt som Aspose.Words var tvungen att ersätta ut. Du kan omdirigera utskriften till en loggfil, skicka ett larm eller till och med avbryta inläsningen om ett kritiskt teckensnitt saknas.

---

## Vanliga frågor & fallgropar

### Vad händer om jag behöver stoppa laddningen när ett obligatoriskt teckensnitt saknas?
Du kan inspektera `WarningInfo`‑objekten i callback‑metoden och kasta ett undantag när ett specifikt teckensnittsnamn dyker upp. Undantaget avbryter inläsningen och ger dig full kontroll.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Fungerar detta med PDF‑filer eller andra format?
Ja. Aspose.Words använder samma varningsinfrastruktur för PDF, RTF och HTML. Byt bara filändelsen så är resten av koden identisk.

### Hur kan jag logga varningar till en fil istället för konsolen?
Byt ut `Console.WriteLine` mot vilket loggningsramverk du föredrar (`Serilog`, `NLog` osv.). Klassen `WarningInfo` exponerar `Message`, `Source` och `Exception` för detaljerade loggar.

### Kommer detta att påverka prestanda?
Överheaden är försumbar – Aspose.Words genererar redan varningarna internt. Att lägga till en callback lagrar dem bara i en lista, vilket är O(n) i antalet varningar. För vanliga dokument är påverkan långt under 1 % av total laddningstid.

---

## Visuell sammanfattning

![Hur man upptäcker teckensnitt i Aspose.Words – varningsflödesdiagram](https://example.com/images/font-detection-diagram.png "hur man upptäcker teckensnitt")

*Alt text:* **hur man upptäcker teckensnitt** – diagram som visar varnings‑callback, samling och enumereringssteg.

---

## Sammanfattning

Vi har gått igenom **hur man upptäcker teckensnitt** i Aspose.Words genom att **fånga varningar**, **konfigurera en callback** och **enumerera varningar**. Det kompletta kodexemplet visar ett produktionsklart mönster som du kan använda i vilken .NET‑applikation som helst.  

Nästa steg kan vara att utforska:

- **Hur man fångar varningar** för andra problem (t.ex. bildkonverteringsfel)
- **Hur man konfigurerar callback** för egna loggningsramverk
- **Hur man enumererar varningar** över flera dokument i ett batch‑jobb
- Att använda **Aspose.Words.Fonts.FontSettings** för att ange reserv‑teckensnittsmappar, vilket kan minska antalet substitutioner från början.

Prova det, anpassa samlaren efter din loggningsstil, så blir du aldrig förvånad över en oväntad teckensnittssubstitution igen. Om du stöter på några knasigheter, lämna en kommentar nedan – happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}