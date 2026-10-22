---
category: general
date: 2026-08-10
description: Formatera fotnotseparator i C# med Aspose.Words för att anpassa fot-
  och slutnotlinjer. Lär dig C#‑fotnotformatering på några minuter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: sv
lastmod: 2026-08-10
og_description: Formatera fotnotseparator i C# med Aspose.Words. Följ den här handledningen
  för att snabbt och pålitligt formatera fotnot- och slutnotseparatorer.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Formatera fotnotseparator i C# – komplett Aspose.Words‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Formatera fotnotseparator i C# med Aspose.Words
url: /sv/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatera fotnotseparator i C# med Aspose.Words

Om du behöver **formatera fotnotseparator** i ett Word‑dokument visar den här guiden hur du gör det med Aspose.Words för .NET. Du får ett komplett, körbart exempel som ändrar justeringen och färgen på separator‑paragrafen, och du lär dig hur du tillämpar samma teknik på slutnotseparatorer.

Handledningen täcker varje steg—från att läsa in källfilen till att spara det modifierade dokumentet—så att du kan kopiera‑klistra koden i ditt eget projekt utan ytterligare research.

## Vad du behöver

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
* En giltig Aspose.Words för .NET-licens (gratis provversion fungerar för utvärdering)
* En Word‑fil som innehåller minst en fotnot eller slutnot (t.ex. `Footnotes.docx`)
* Visual Studio 2022 eller någon C#‑IDE du föredrar

Att ha dessa saker redo låter dig fokusera på logiken för **C#‑fotnotformatering** istället för miljöinställningar.

## Steg 1: Läs in dokumentet som innehåller fotnoter och slutnoter

Den första operationen är att skapa ett `Document`‑objekt som pekar på din källfil. Aspose.Words läser in hela DOCX‑paketet i minnet och ger dig full åtkomst till fotnot‑ och slutnot‑noder.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Varför detta är viktigt*: Att läsa in dokumentet är en förutsättning för all manipulation. Om filsökvägen är fel kastar Aspose.Words ett `FileNotFoundException`, så kontrollera sökvägen innan du fortsätter.

## Steg 2: Hämta separator‑ och fortsättningsseparator‑noderna

Fotnot- och slutnotseparatorer lagras som speciella noder i samlingarna `Footnotes` och `Endnotes`. Varje samling exponerar egenskaperna `Separator` och `ContinuationSeparator` som returnerar en `Node`‑referens.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Varför detta är viktigt*: `Separator`‑noden representerar den linje som visuellt separerar huvudtexten från fotnotblocket. Genom att få en referens kan du ändra dess styckeformat, teckensnitt eller till och med ersätta noden helt.

## Steg 3: Ändra den visuella stilen för fotnotseparatorn

I de flesta Word‑dokument är separatorn ett enskilt stycke som innehåller ett bindestreck eller en asterisk. Koden nedan kontrollerar om separatorn är ett `Paragraph` och, om så är fallet, centrerar den och ändrar dess textfärg till grå.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Formatera fortsättningsseparatorn (valfritt)

Fortsättningsseparatorn visas när en fotnot sträcker sig över flera sidor. Du kan formatera den på liknande sätt:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Varför detta är viktigt*: Att justera separatorn förbättrar läsbarheten, och att ändra färgen skiljer den från vanlig stycketext. Du kan ersätta `ParagraphAlignment.Center` med `Left` eller `Right` för att matcha ditt dokuments designriktlinjer.

## Steg 4: Spara det modifierade dokumentet

Efter att ha tillämpat den önskade stilen skriver du dokumentet tillbaka till disk. Du kan skriva över originalfilen eller skapa en ny version.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

När du öppnar `Footnotes_Styled.docx` i Microsoft Word visas fotnotseparatorn centrerad och grå, exakt som koden specificerade.

## Avancerade varianter

### Formatera slutnotseparatorn

Om ditt dokument också använder slutnoter kan du tillämpa samma logik på `Endnotes`‑samlingen:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Använd en anpassad sträng för separatorn

Ibland vill du att separatorn ska vara en serie asterisker (`***`). Ersätt de befintliga run‑erna med ett nytt run:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Hantera dokument utan en separatornod

Ett sällsynt kantfall är ett dokument som saknar separatornoden (t.ex. när författaren har raderat den). I det scenariot returnerar `document.Footnotes.Separator` `null`. Skydda mot detta:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Vanliga fallgropar och hur du undviker dem

| Fallgropar | Varför det händer | Lösning |
|------------|-------------------|---------|
| **Separator är inte ett `Paragraph`** | Vissa Word‑mallar använder en `Table` eller `Shape` som separator. | Kontrollera nodtypen med `is Paragraph` innan du castar. |
| **`Runs`‑samlingen är tom** | Separatorn kan vara ett tomt stycke. | Verifiera `Runs.Count > 0` innan du åtkommer `Runs[0]`. |
| **Licensen har inte tillämpats** | Utan en licens lägger Aspose.Words in ett vattenstämpel och kan begränsa API‑användning. | Anropa `License license = new License(); license.SetLicense("Aspose.Words.lic");` i början av ditt program. |
| **Spara till en skrivskyddad mapp** | `Save`‑metoden kastar ett `UnauthorizedAccessException`. | Säkerställ att mål‑katalogen har skrivrättigheter. |

Att åtgärda dessa problem tidigt förhindrar körningsfel och säkerställer en smidig **modifiering av fotnotseparator**‑upplevelse.

## Komplett, körbart exempel

Nedan är en fristående konsolapplikation som demonstrerar varje steg som diskuteras ovan. Kopiera koden till ett nytt .NET‑konsolprojekt, ersätt filsökvägarna och kör den.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Förväntat resultat**  

När du öppnar `Footnotes_Styled.docx`:

* Fotnotseparatorlinjen är centrerad under huvudtexten.
* Dess färg visas som ljusgrå, vilket gör den visuellt distinkt.
* Om dokumentet innehåller slutnoter är deras separatorer också centrerade och färgade grå (eller skiffer

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}