---
category: general
date: 2026-08-07
description: Jämför Word-dokument i C# med Aspose.Words. Lär dig hur du jämför docx-filer,
  genererar en jämförelsrapport och hanterar revisioner effektivt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- compare word documents
- word document comparison
- how to compare docx
- compare docx files
- compare word files
language: sv
lastmod: 2026-08-07
og_description: Jämför Word-dokument i C# med Aspose.Words. Den här handledningen
  visar hur du jämför docx-filer, inkluderar revisioner och sparar en detaljerad rapport
  för granskning.
og_image_alt: Comparison report when you compare word documents using Aspose.Words
og_title: Jämför Word-dokument i C# med Aspose.Words – fullständig guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Compare word documents in C# with Aspose.Words. Learn how to compare
    docx files, generate a comparison report, and handle revisions efficiently.
  headline: Compare word documents in C# using Aspose.Words
  type: TechArticle
- description: Compare word documents in C# with Aspose.Words. Learn how to compare
    docx files, generate a comparison report, and handle revisions efficiently.
  name: Compare word documents in C# using Aspose.Words
  steps:
  - name: '**Define comparison options** – decide whether to show revisions, ignore
      formatting, etc.'
    text: '**Define comparison options** – decide whether to show revisions, ignore
      formatting, etc.'
  - name: '**Execute the comparison** – the library returns a `ComparisonResult` object.'
    text: '**Execute the comparison** – the library returns a `ComparisonResult` object.'
  - name: '**Save the report** – the result can be saved as a new `.docx` that highlights
      insertions, deletions, and moves.'
    text: '**Save the report** – the result can be saved as a new `.docx` that highlights
      insertions, deletions, and moves.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Comparison
- docx
title: Jämför Word-dokument i C# med Aspose.Words
url: /sv/net/compare-documents/compare-word-documents-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jämför Word-dokument i C# med Aspose.Words

Om du behöver **jämföra Word-dokument** programatiskt gör Aspose.Words det enkelt. Denna guide visar **hur du jämför docx**‑filer, genererar en jämförelsrapport och anpassar alternativ som att visa revisioner.

Dokumentjämförelse är ett vanligt krav för juridiska granskningar, kontraktsförhandlingar och innehållsversionering. I slutet av den här handledningen kommer du att kunna:

* Ladda två `.docx`‑filer och köra en **word document comparison**.  
* Inkludera eller exkludera revisioner i resultatet.  
* Spara resultatet som en ny Word‑fil som markerar förändringar.  

Inga externa tjänster krävs – allt körs lokalt i en .NET‑applikation.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare installerat.  
* En licensierad kopia av **Aspose.Words for .NET** (gratis provversion fungerar för testning).  
* Två Word‑filer (`Original.docx` och `Modified.docx`) placerade i en känd katalog.  

Om du ännu inte har lagt till Aspose.Words i ditt projekt, kör:

```bash
dotnet add package Aspose.Words
```

## Jämför Word-dokument – övergripande arbetsflöde

Jämförelseprocessen består av tre logiska steg:

1. **Definiera jämförelsalternativ** – bestäm om du vill visa revisioner, ignorera formatering osv.  
2. **Utför jämförelsen** – biblioteket returnerar ett `ComparisonResult`‑objekt.  
3. **Spara rapporten** – resultatet kan sparas som en ny `.docx` som markerar insättningar, borttagningar och flyttningar.

Nedan finns ett komplett, körbart exempel som följer dessa steg.

```csharp
using Aspose.Words.LowCode;

namespace DocumentComparisonDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Define comparison options (e.g., include revisions in the result)
            ComparisonOptions comparisonOptions = new ComparisonOptions
            {
                ShowRevisions = true // Show insertions/deletions as tracked changes
            };

            // Step 2: Compare the original and modified documents
            // This is the core of the word document comparison.
            ComparisonResult comparisonResult = Comparer.Compare(
                "YOUR_DIRECTORY/Original.docx",   // path to the original file
                "YOUR_DIRECTORY/Modified.docx",   // path to the modified file
                comparisonOptions);

            // Step 3: Save the comparison report
            // The report will be a new .docx that visually marks all differences.
            comparisonResult.SaveReport("YOUR_DIRECTORY/ComparisonReport.docx");

            // Optional: Inform the user that the process completed.
            System.Console.WriteLine("Comparison report created successfully.");
        }
    }
}
```

### Varför varje del är viktig

* **ComparisonOptions** – styr detaljnivån i jämförelsen. Att sätta `ShowRevisions = true` speglar Words inbyggda “Track Changes”-vy, vilket är avgörande för granskare som behöver se varje redigering.  
* **Comparer.Compare** – utför det tunga arbetet. Metoden läser båda källfilerna, bygger en intern diff‑modell och returnerar ett `ComparisonResult`.  
* **SaveReport** – skriver en ny `.docx` som innehåller diffen som spårade förändringar, vilket gör det enkelt att öppna i Microsoft Word eller någon kompatibel visare.

## Alternativ för Word-dokumentjämförelse

Aspose.Words erbjuder flera ytterligare flaggor som du kan kombinera med `ComparisonOptions`:

| Alternativ | Beskrivning | Typiskt användningsfall |
|------------|-------------|--------------------------|
| `ShowRevisions` | Behåller förändringar som spårade revisioner. | Juridiska team som granskar kontraktsändringar. |
| `IgnoreFormatting` | Ignorerar skillnader i teckensnitt, stil eller avstånd. | Innehålls‑endast jämförelse där layout inte är viktig. |
| `IgnoreHeadersFooters` | Hoppar över ändringar i sidhuvud/sidfot. | När endast brödtexten är relevant. |
| `IgnoreCaseChanges` | Behandlar stora/små bokstäver som lika. | Utkast där skiftläge inte är betydelsefullt. |

Du kan aktivera flera alternativ så här:

```csharp
ComparisonOptions options = new ComparisonOptions
{
    ShowRevisions = true,
    IgnoreFormatting = true,
    IgnoreHeadersFooters = true
};
```

## Så jämför du docx‑filer med revisioner

När du behöver **jämföra docx‑filer** och behålla en fullständig revisionsspårning är flaggan `ShowRevisions` oumbärlig. Den resulterande rapporten kommer att innehålla Words inbyggda förändringsstaplar, vilket gör den omedelbart igenkännbar för slutanvändare.

```csharp
ComparisonOptions revOptions = new ComparisonOptions { ShowRevisions = true };
ComparisonResult revResult = Comparer.Compare("A.docx", "B.docx", revOptions);
revResult.SaveReport("RevisionReport.docx");
```

Öppna `RevisionReport.docx` i Microsoft Word så ser du insättningar markerade i grönt och borttagningar i rött, exakt som om du hade använt Words inbyggda “Compare”-funktion.

## Jämför docx‑filer i bulk

Om du har många dokumentpar att utvärdera, omslut jämförelselogiken i en loop:

```csharp
string[] originals = Directory.GetFiles("Originals", "*.docx");
string[] modified  = Directory.GetFiles("Modified", "*.docx");

for (int i = 0; i < originals.Length; i++)
{
    var result = Comparer.Compare(originals[i], modified[i], comparisonOptions);
    string reportPath = Path.Combine("Reports", $"Report_{i + 1}.docx");
    result.SaveReport(reportPath);
    Console.WriteLine($"Report {i + 1} saved.");
}
```

Detta mönster låter dig **jämföra docx‑filer** i stora satser utan manuell inblandning.

## Jämför Word‑filer – bästa praxis och fallgropar

* **Filvägar måste vara absoluta eller relativa till den körande processen.** Att använda en relativ sökväg som `"YOUR_DIRECTORY/Original.docx"` fungerar när arbetskatalogen är korrekt inställd; annars ange `Path.GetFullPath`.  
* **Stora dokument (>100 MB) kan förbruka betydande minne.** Överväg att strömma filerna eller öka processens minnesgräns om du stöter på `OutOfMemoryException`.  
* **Säkerställ att båda filerna använder samma docx‑version.** Att blanda äldre `.doc`‑filer kan ge oväntade resultat; konvertera dem först till `.docx` med `Document.Save(..., SaveFormat.Docx)`.  
* **När `ShowRevisions` är falskt blir resultatet ett rent dokument utan förändringsmarkörer.** Använd detta läge om du bara behöver en sammanfattning av skillnader (t.ex. en ren‑text diff‑rapport).  

## Förväntat resultat

Efter att ha kört exempel­koden hittar du `ComparisonReport.docx` i mål‑mappen. När du öppnar den i Word visas:

* **Insättningar** – markerade i grönt med en vänsterställd förändringsstapel.  
* **Borttagningar** – visade i röd genomstruken text.  
* **Flyttad text** – indikerad med en dubbel‑pil‑markör.

Dessa visuella ledtrådar gör det enkelt för granskare att godkänna eller avvisa varje förändring.

![Comparison report showing differences between original and modified documents](comparison-report.png "Comparison report when you compare word documents using Aspose.Words")

*Bilden ovan illustrerar den typiska layouten för en jämförelsrapport som genereras av koden.*

## Slutsats

Du vet nu hur du **jämför Word‑dokument** i C# med Aspose.Words, från att ställa in jämförelsalternativ till att generera en polerad rapport som markerar varje förändring. Detta tillvägagångssätt fungerar för enskilda filpar såväl som för bulk‑operationer, och du kan anpassa jämförelsen för att ignorera formatering, sidhuvuden eller skiftläge efter behov.

Nästa steg du kan utforska:

* Integrera jämförelselogiken i ett webb‑API så att användare kan ladda upp två filer och få en rapport direkt.  
* Kombinera **compare docx files** med SharePoint eller OneDrive för automatiserad dokumentstyrning.  
* Använd `ComparisonResult`‑API:t för att extrahera en ren‑text‑sammanfattning av skillnader för loggning eller notifieringar.

Genom att behärska dessa tekniker kan du automatisera dokumentgranskningsarbetsflöden och minska manuellt arbete.

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Compare Options In Word Document](/words/english/net/compare-documents/compare-options/)
- [Compare For Equal In Word Document](/words/english/net/compare-documents/compare-for-equal/)
- [How to Compare Two Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}