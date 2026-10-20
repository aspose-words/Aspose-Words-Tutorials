---
category: general
date: 2026-06-24
description: Hur man använder IWarningCallback för att upptäcka saknade teckensnitt
  i Aspose.Words‑dokument. Lär dig ett komplett, körbart exempel och bästa praxis.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: sv
og_description: Hur du använder IWarningCallback för att upptäcka saknade teckensnitt
  i Aspose.Words. Följ den steg‑för‑steg‑guiden för en komplett, produktionsklar lösning.
og_title: Hur man använder IWarningCallback – Upptäck saknade typsnitt
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Hur man använder IWarningCallback – Upptäck saknade teckensnitt med Aspose.Words
url: /sv/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så använder du IWarningCallback – Upptäck saknade teckensnitt med Aspose.Words

Att använda **IWarningCallback** är avgörande när du arbetar med Aspose.Words och behöver **upptäcka saknade teckensnitt** i en DOCX‑fil. I den här guiden går vi igenom ett komplett, kopiera‑och‑klistra‑exempel som visar exakt hur du använder IWarningCallback för att fånga varningar om teckensnittssubstitution, varför det är viktigt och vad du ska göra när du har fångat dem.

Om du någonsin har öppnat ett dokument och sett förvrängd text eftersom ett anpassat teckensnitt saknades, känner du igen frustrationen. I slutet av den här tutorialen har du ett pålitligt sätt att programatiskt identifiera de problemen, logga dem eller till och med automatiskt tillämpa ett reservteckensnitt.

## Vad du kommer att lära dig

- Syftet med **IWarningCallback** och när du ska använda den.  
- Hur du implementerar en egen varningssamling som isolerar **detect missing fonts**‑händelser.  
- Hur du kopplar samlaren till **LoadOptions** så att varje dokumentladdning övervakas.  
- Hur du verifierar resultatet och hanterar kantfall (flera saknade teckensnitt, tysta varningar osv.).  

### Förutsättningar

- .NET 6.0 eller senare (koden fungerar också på .NET Framework 4.6+).  
- Aspose.Words för .NET installerat via NuGet (`Install-Package Aspose.Words`).  
- En DOCX‑fil som refererar till ett teckensnitt som inte finns på maskinen (t.ex. `DocumentWithMissingFont.docx`).  

Inga extra bibliotek behövs – allt finns i Aspose.Words.

---

## Så använder du IWarningCallback för att upptäcka saknade teckensnitt i Aspose.Words

Nedan är det **fullständiga, körbara programmet**. Kopiera det till ett nytt konsolprojekt, justera filsökvägen och kör. Du kommer att se konsolutdata för varje varning om saknat teckensnitt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Förväntad utdata

Om `DocumentWithMissingFont.docx` refererar till ett teckensnitt som heter *“MyFancyFont”* som inte är installerat, får du något i stil med:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Varje rad som inleds med **[Missing Font]** genereras av vår **IWarningCallback**‑implementation, vilket bevisar att vi framgångsrikt **detect missing fonts**.

---

## Steg 1: Implementera IWarningCallback‑gränssnittet

Varför behöver vi en egen klass? Aspose.Words genererar **varningar** av olika anledningar – filformatproblem, föråldrade funktioner och, viktigast för oss, teckensnittssubstitution. Genom att implementera `IWarningCallback` får vi en krok som tar emot varje varning i realtid. Genom att filtrera på `WarningType.FontSubstitution` isolerar vi det specifika scenariot där ett teckensnitt saknas.

**Proffstips:** Om du vill fånga *alla* varningar för diagnostik, ta bara bort `if`‑kontrollen och logga varje `info.Type`.

---

## Steg 2: Anslut callback‑en till LoadOptions

`LoadOptions` är porten som talar om för Aspose.Words hur den inkommande dokumentet ska behandlas. Genom att sätta `WarningCallback` till en instans av vår samlare säkerställer du att callback‑en är aktiv under hela laddningsoperationen. Du kan återanvända samma `LoadOptions`‑objekt för flera dokument, vilket är praktiskt i batch‑processeringspipelines.

**Vanlig fråga:** *Vad händer om jag laddar ett dokument utan att ange LoadOptions?*  
Svar: Aspose.Words kommer fortfarande att generera varningar internt, men utan en callback kastas de tyst bort och du förlorar möjligheten att **detect missing fonts**.

---

## Steg 3: Ladda ett dokument och fånga varningar om saknade teckensnitt

`Document`‑konstruktorn som tar en filsökväg och `LoadOptions` gör det tunga lyftet. När filen parsas triggas vår `FontWarningCollector.Warning`‑metod för varje saknat teckensnitt. Konsolutdata bevisar att mekanismen fungerar.

**Kantfall:** Ett enda dokument kan referera till flera frånvarande teckensnitt. Callback‑en avfyras en gång per saknat teckensnitt, så du får flera rader – perfekt för att bygga en omfattande rapport.

---

## Varför använda IWarningCallback istället för manuella teckensnittskontroller?

Du skulle kunna skanna dokumentets `Run.Font`‑egenskaper manuellt efter laddning, men det kräver att dokumentet laddas framgångsrikt först – något som misslyckas om teckensnittet är helt otillgängligt. Varningssystemet fungerar **innan** någon substitution sker, vilket ger dig en sann bild av vad som saknas.

Dessutom körs callback‑en **som en del av laddningspipeline**, vilket betyder att du kan avbryta tidigt, ersätta teckensnitt i farten eller logga detaljerad diagnostik utan extra genomgångar av dokumentträdet.

---

## Hantera flera saknade teckensnitt på ett smidigt sätt

Om du förväntar dig många saknade teckensnitt, överväg att samla dem i en samling:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Efter laddning kan du iterera över `MissingFonts` och till exempel skriva dem till en CSV‑fil åt designteamet.

---

## Bonus: Logga varningar till en fil

Konsolutdata fungerar för demonstrationer, men produktkod loggar vanligtvis till ett beständigt lagringsställe. Byt ut anropet `Console.WriteLine` mot något i stil med:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Nu har du ett revisionsspår som kan granskas senare, vilket uppfyller efterlevnadskrav.

---

## Slutsats

Vi har gått igenom **hur du använder IWarningCallback** för att **detect missing fonts** i Aspose.Words, från att implementera callback‑en till att koppla den till `LoadOptions` och hantera de resulterande varningarna. Detta tillvägagångssätt ger dig insikt i realtid om teckensnittsrelaterade problem, så att du kan logga, ersätta eller varna användare innan dokumentet renderas.

Nästa steg du kan utforska:

- **Fallback fonts:** programmera in ett standardteckensnitt när en substitution sker.  
- **Batch processing:** loopa över en mapp med dokument och återanvänd samma `AggregatingFontCollector`.  
- **User feedback:** visa varningar om saknade teckensnitt i ett UI istället för i konsolen.

Prova i ditt eget projekt – ingen mer mystisk förvrängd text, bara tydlig, handlingsbar diagnostik. Lycka till med kodandet!

## Vad bör du lära dig härnäst?


Följande handledningar täcker nära besläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}