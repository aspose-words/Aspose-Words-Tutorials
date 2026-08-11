---
category: general
date: 2026-08-10
description: Formatteer de voetnootscheiding in C# met Aspose.Words om voet- en eindnootregels
  aan te passen. Leer C#-voetnootopmaak in enkele minuten.
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
language: nl
lastmod: 2026-08-10
og_description: Formatteer de voetnootseparator in C# met Aspose.Words. Volg deze
  tutorial om voetnoot- en eindnootseparators snel en betrouwbaar te stylen.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Opmaak van voetnootseparator in C# – volledige Aspose.Words-gids
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
title: Formateer voetnootscheidingsteken in C# met Aspose.Words
url: /nl/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opmaak van voetnootseparator in C# met Aspose.Words

Als je de **voetnootseparator** in een Word‑document moet **opmaken**, laat deze gids zien hoe je dat doet met Aspose.Words voor .NET. Je ziet een volledig, uitvoerbaar voorbeeld dat de uitlijning en kleur van de separator‑paragraaf wijzigt, en je leert hoe je dezelfde techniek toepast op eindnoot‑separators.

De tutorial behandelt elke stap — van het laden van het bronbestand tot het opslaan van het gewijzigde document — zodat je de code kunt kopiëren‑plakken in je eigen project zonder extra onderzoek.

## Wat je nodig hebt

Zorg ervoor dat je het volgende hebt:

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
* Een geldige Aspose.Words voor .NET‑licentie (de gratis proefversie werkt voor evaluatie)
* Een Word‑bestand dat minstens één voetnoot of eindnoot bevat (bijv. `Footnotes.docx`)
* Visual Studio 2022 of een andere C#‑IDE naar keuze

Met deze zaken klaar kun je je concentreren op de **C#‑voetnootopmaak**‑logica in plaats van op de omgeving.

## Stap 1: Laad het document dat voetnoten en eindnoten bevat

De eerste handeling is het aanmaken van een `Document`‑object dat naar je bronbestand wijst. Aspose.Words leest het volledige DOCX‑pakket in het geheugen, waardoor je volledige toegang krijgt tot voetnoot‑ en eindnoot‑knopen.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Waarom dit belangrijk is*: Het document laden is de voorwaarde voor elke manipulatie. Als het bestandspad onjuist is, gooit Aspose.Words een `FileNotFoundException`, dus controleer het pad voordat je verdergaat.

## Stap 2: Haal de separator‑ en continuation‑separator‑knopen op

Voetnoot‑ en eindnoot‑separators worden opgeslagen als speciale knopen binnen de collecties `Footnotes` en `Endnotes`. Elke collectie biedt de eigenschappen `Separator` en `ContinuationSeparator` die een `Node`‑referentie teruggeven.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Waarom dit belangrijk is*: De `Separator`‑knoop vertegenwoordigt de lijn die visueel de hoofdtekst scheidt van het voetnoot‑blok. Door een referentie te verkrijgen, kun je de alinea‑opmaak, het lettertype of zelfs de knoop volledig vervangen.

## Stap 3: Wijzig de visuele stijl van de voetnootseparator

In de meeste Word‑documenten is de separator een enkele alinea die een streepje of een sterretje bevat. De onderstaande code controleert of de separator een `Paragraph` is en centreert deze vervolgens en verandert de tekstkleur naar grijs.

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

### Stijlen van de continuation‑separator (optioneel)

De continuation‑separator verschijnt wanneer een voetnoot zich over meerdere pagina’s uitstrekt. Je kunt deze op dezelfde manier stijlen:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Waarom dit belangrijk is*: Het uitlijnen van de separator verbetert de leesbaarheid, en het wijzigen van de kleur maakt deze onderscheidend ten opzichte van gewone alinea‑tekst. Je kunt `ParagraphAlignment.Center` vervangen door `Left` of `Right` om aan de ontwerp‑richtlijnen van je document te voldoen.

## Stap 4: Sla het gewijzigde document op

Nadat je de gewenste stijl hebt toegepast, schrijf je het document terug naar de schijf. Je kunt het originele bestand overschrijven of een nieuwe versie maken.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Wanneer je `Footnotes_Styled.docx` opent in Microsoft Word, verschijnt de voetnootseparator gecentreerd en grijs, precies zoals de code heeft opgegeven.

## Geavanceerde variaties

### Opmaak van de eindnootseparator

Als je document ook eindnoten gebruikt, kun je dezelfde logica toepassen op de `Endnotes`‑collectie:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Een aangepaste tekenreeks voor de separator gebruiken

Soms wil je dat de separator een reeks sterretjes (`***`) is. Vervang de bestaande runs door een nieuwe run:

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

### Documenten zonder separator‑knoop afhandelen

Een zeldzame randgeval is een document dat de separator‑knoop weglaten (bijv. wanneer de auteur deze heeft verwijderd). In dat scenario geeft `document.Footnotes.Separator` `null` terug. Bescherm je code hiertegen:

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

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|-----------|
| **Separator is geen `Paragraph`** | Sommige Word‑templates gebruiken een `Table` of `Shape` als separator. | Controleer het knooptype met `is Paragraph` vóór het casten. |
| **`Runs`‑collectie is leeg** | De separator kan een lege alinea zijn. | Controleer `Runs.Count > 0` vóór toegang tot `Runs[0]`. |
| **Licentie niet toegepast** | Zonder licentie voegt Aspose.Words een watermerk toe en kan API‑gebruik beperkt worden. | Roep `License license = new License(); license.SetLicense("Aspose.Words.lic");` aan het begin van je programma aan. |
| **Opslaan naar een alleen‑lezen map** | De `Save`‑methode gooit een `UnauthorizedAccessException`. | Zorg dat de doelmap schrijfrechten heeft. |

Deze problemen vroegtijdig aanpakken voorkomt runtime‑exceptions en zorgt voor een soepele **wijziging van voetnootseparator**‑ervaring.

## Volledig, uitvoerbaar voorbeeld

Hieronder vind je een zelfstandige console‑applicatie die elke stap uit de tutorial demonstreert. Kopieer de code naar een nieuw .NET‑console‑project, vervang de bestandspaden, en voer het uit.

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

**Verwacht resultaat**  

Wanneer je `Footnotes_Styled.docx` opent:

* De lijn van de voetnootseparator staat gecentreerd onder de hoofdtekst.
* De kleur verschijnt als lichtgrijs, waardoor hij visueel onderscheidend is.
* Als het document eindnoten bevat, zijn hun separators ook gecentreerd en grijs gekleurd (of slate

## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}