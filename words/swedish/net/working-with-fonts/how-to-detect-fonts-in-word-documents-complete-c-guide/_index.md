---
category: general
date: 2026-02-24
description: Hur man upptäcker teckensnitt i ett Word‑dokument med Aspose.Words. Lär
  dig hur du ställer in en återuppringning och laddar ett Word‑dokument med ett komplett
  kodexempel.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: sv
og_description: Hur man upptäcker teckensnitt i ett Word‑dokument med en varningsåteruppringning.
  Denna guide visar hur man ställer in återuppringning och laddar Word‑dokument med
  Aspose.Words.
og_title: Hur man upptäcker typsnitt i Word‑dokument – Steg‑för‑steg C#‑handledning
tags:
- C#
- Aspose.Words
- Document Processing
title: Hur man upptäcker teckensnitt i Word-dokument – Komplett C#-guide
url: /sv/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man upptäcker typsnitt i Word-dokument – Komplett C#-guide

Har du någonsin undrat **how to detect fonts** som saknas när du laddar en Word‑fil? Kanske har du stött på ett dokument som ser bra ut i redigeraren, men PDF‑filen du genererar byter ut några teckensnitt bakom kulisserna. Det är ett klassiskt symptom på typsnittssubstitution, och att fånga det tidigt kan rädda dig från otrevliga layout‑överraskningar.

I den här handledningen går vi igenom en praktisk lösning: att använda **Aspose.Words** för att läsa in en `.docx`, bifoga en varnings‑callback och **how to set callback** som rapporterar varje typsnittssubstitution. I slutet kommer du inte bara att veta **how to detect fonts** programatiskt, du kommer också att förstå **how to set callback** korrekt och **load word document** säkert – allt i ett enda körbart C#‑exempel.

> **Vad du får**
> * Ett komplett, copy‑paste‑klart kodexempel  
> * Steg‑för‑steg‑förklaring av varje rad  
> * Tips för att hantera kantfall som flera saknade typsnitt eller anpassade typsnittsmappningar  
> * Förväntad konsolutskrift så att du kan verifiera att allt fungerar

---

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Core)  
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)  
- En Word‑fil som avsiktligt refererar till ett typsnitt du inte har installerat (t.ex. `MissingFont.docx`)  
- Visual Studio, Rider eller någon annan editor du föredrar

Inga andra bibliotek behövs; allt annat är en del av den standard .NET‑runtime som följer med.

---

## Så upptäcker du typsnitt i ett Word‑dokument

### Steg 1: Skapa Load Options och bifoga en varnings‑callback

Det första vi gör är att tala om för Aspose.Words att vi vill bli meddelade om eventuella problem som uppstår när filen läses in. Det är här **how to set callback** kommer in i bilden.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Varför detta är viktigt:**  
`LoadOptions` är porten till att anpassa inläsningsprocessen. Genom att tilldela en instans av `FontWarningCollector` till `WarningCallback` kommer Aspose.Words att anropa vår `Warning`‑metod varje gång den ersätter ett saknat typsnitt med ett reservtypsnitt. Detta är kärnan i **how to detect fonts** som inte finns på maskinen.

### Steg 2: Förbered LoadOptions‑instansen

Nu skapar vi en instans av `LoadOptions` och kopplar vår callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Pro tip:** Om du behöver kontrollera *var* Aspose letar efter ersättningstypsnitt, kan du också sätta `loadOptions.FontSettings` här. Det är användbart när du har en privat typsnittsmapp på servern.

### Steg 3: Läs in Word‑dokumentet

Med alternativen klara, **load word document** vi slutligen. Detta är ögonblicket då Aspose parsar DOCX‑filen och, om några typsnitt saknas, triggas vår callback.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Vad händer under huven?**  
Aspose.Words läser XML‑delarna i DOCX‑filen, löser upp varje `<w:font>`‑referens och kontrollerar systemets typsnittssamling. När en referens inte kan uppfyllas ersätter den med det första matchande reservtypsnittet och avger en `FontSubstitution`‑varning.

### Steg 4: Verifiera utskriften

Kör programmet och titta på konsolen. För varje saknat typsnitt kommer du att se en rad som:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Om dokumentet inte innehåller några saknade typsnitt förblir konsolen tyst – vilket betyder att **how to detect fonts** inte returnerade några träffar.

### Steg 5: Fullt fungerande exempel (konsolapp)

Nedan är en självständig `Program.cs` som du kan släppa in i ett nytt konsolprojekt. Den innehåller alla delar vi diskuterat samt en liten hjälpfunktion för att hålla konsolfönstret öppet vid felsökning.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Förväntad konsolutskrift** (exempel):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Om du ersätter `MissingFont.docx` med en fil som bara använder installerade typsnitt, kommer du bara att se raden “Press any key…” – vilket bekräftar att detekteringslogiken fungerar som avsett.

---

## Vanliga frågor & kantfall

### Vad händer om jag behöver fånga *alla* varningar, inte bara typsnittssubstitution?

Ta bara bort `if (info.Type == WarningType.FontSubstitution)`‑villkoret. `WarningInfo`‑objektet innehåller en `Type`‑enum som du kan använda för andra scenarier (t.ex. `DocumentStructure`, `ImageLoading`).

### Kan jag logga varningar till en fil istället för konsolen?

Absolut. Ersätt `Console.WriteLine` med ett anrop till valfritt loggningsramverk (`Serilog`, `NLog` osv.). Callbacken körs på samma tråd som läser in dokumentet, så se till att din logger är trådsäker.

### Hur beter sig detta i en webbapplikation?

I ASP.NET Core skulle du vanligtvis injicera en singleton‑implementation av `IWarningCallback` och skicka den via `LoadOptions`. Kom ihåg att undvika att skriva direkt till svarströmmen – logga till en databas eller en minnes‑samling som du senare kan exponera via en API‑endpoint.

### Vad händer med anpassade typsnitt lagrade i en icke‑systemmapp?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Nu kommer Aspose.Words att söka i `C:\MyCustomFonts` innan den faller tillbaka på OS‑typsnitten, vilket minskar antalet substitutionsvarningar du ser.

---

## Visuell sammanfattning

![Upptäcka typsnitt varnings‑callback i Aspose.Words](/images/font-warning-callback.png "Hur man upptäcker typsnitt med en varnings‑callback")

*Skärmdumpen visar konsolutskriften när ett saknat typsnitt ersätts. Alt‑texten innehåller det primära nyckelordet för SEO.*

---

## Slutsats

Du har nu ett robust, produktionsklart mönster för **how to detect fonts** i vilken Word‑fil du än laddar med Aspose.Words. Genom att **how to set callback** får du insikt i realtid om saknade eller ersatta teckensnitt, och du har lärt dig det korrekta sättet att **load word document** samtidigt som du håller din kod ren och underhållbar.

Nästa steg? Prova att utöka callbacken så att den samlar varningar i en lista, och sedan visar dem i ett UI eller en automatiserad rapport. Du kan också utforska `FontSettings.SubstitutionSettings` för att styra *vilka* typsnitt som väljs som reservtypsnitt.

Känn dig fri att experimentera – byt ut dokumentet, lägg till fler saknade typsnitt, eller integrera logiken i en större dokument‑bearbetningspipeline. Om du stöter på problem, lämna en kommentar nedanför eller kontakta mig på GitHub.

Lycklig kodning, och må dina dokument alltid renderas med de typsnitt du förväntar dig!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}