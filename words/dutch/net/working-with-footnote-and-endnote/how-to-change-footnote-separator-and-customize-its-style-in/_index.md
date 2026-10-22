---
category: general
date: 2026-10-13
description: Hoe de voetnootscheiding in een Word‑document te wijzigen met Aspose.Words.
  Leer hoe u de letterkleur in een Word‑document programmatically kunt wijzigen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: nl
lastmod: 2026-10-13
og_description: Hoe de voetnootscheiding in een Word‑document te wijzigen met Aspose.Words.
  Deze tutorial laat zien hoe je de letterkleur in een Word‑document wijzigt met C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Hoe je de voetnootscheiding in een Word‑document wijzigt – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Hoe de voetnootscheiding te wijzigen en de stijl ervan aan te passen in een
  Word‑document
url: /nl/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe de scheidingsteken van voetnoten te wijzigen en de stijl ervan aan te passen in een Word‑document

Als je **hoe je de scheidingsteken van voetnoten kunt wijzigen** in een Word‑document, geeft deze gids je een complete, kant‑klaar oplossing. Met Aspose.Words for .NET kun je ook **de letterkleur in een Word‑document wijzigen** voor elementen zoals voetnoot‑ en eindnootscheidingstekens, zodat het uiteindelijke bestand overeenkomt met je huisstijl of stijlgids.

Documentauteurs vragen vaak: *Waarom ziet de standaard voetnootscheiding er eenvoudig uit, en hoe kan ik deze laten opvallen?* Het antwoord is om rechtstreeks toegang te krijgen tot de scheidingsteken‑paragraafobjecten, hun lettereigenschappen aan te passen en het resultaat op te slaan. Deze tutorial leidt je door elke stap, van het laden van een .docx‑bestand tot het opslaan van de gestylede output.

Je leert hoe je:

* Een Word‑bestand laadt dat al voetnoten en eindnoten bevat.  
* De voetnoot‑ en eindnootscheidingsteken‑paragrafen vindt.  
* De letterkleur van elk scheidingsteken wijzigt (rood voor voetnoten, blauw voor eindnoten).  
* Het gewijzigde document opslaat zonder bestaande inhoud te verliezen.

Er zijn geen externe tools nodig, behalve de Aspose.Words‑bibliotheek en een .NET‑ontwikkelomgeving.

## Vereisten

* .NET 6.0 SDK of later (de code werkt ook met .NET Framework 4.7+).  
* Visual Studio 2022, Rider, of elke C#‑editor die je verkiest.  
* Aspose.Words for .NET NuGet‑pakket (`Aspose.Words`).  
* Een voorbeeld‑Word‑bestand (`Footnotes.docx`) dat minstens één voetnoot en één eindnoot bevat.

> **Pro tip:** Als je geen voorbeeldbestand hebt, maak dan een nieuw Word‑document, voeg een voetnoot toe (`References → Insert Footnote`) en een eindnoot (`References → Insert Endnote`). Sla het op als `Footnotes.docx` in een map die je vanuit code kunt refereren.

## Hoe de voetnootscheiding te wijzigen met Aspose.Words

De kern van de taak is het ophalen van de speciale paragrafen die Aspose.Words blootlegt als *separator*‑nodes. Deze nodes zijn van het type `Paragraph` en kunnen worden opgemaakt zoals elke andere paragraaf.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Waarom elke regel belangrijk is

* **Loading the document** (`new Document`) geeft je een in‑memory‑representatie die Aspose.Words kan manipuleren.  
* **`GetChild` with `ParagraphNodeType.FootnoteSeparator`** retourneert de verborgen paragraaf die Word gebruikt om de lijn te tekenen die voetnoten van de hoofdtekst scheidt. Dezelfde methode werkt voor de eindnootscheiding.  
* **Changing `Font.Color`** beïnvloedt direct het uiterlijk van de lijn omdat Word de scheiding weergeeft als een paragraaf met één “‑”‑teken. Het instellen van de kleur op `Color.Red` (of een andere `System.Drawing.Color`) werkt de visuele stijl bij.  
* **Saving** schrijft de wijzigingen terug naar een .docx‑bestand dat elke tekstverwerker kan openen.

### Verwachte output

Wanneer je `FootnoteSeparatorsStyled.docx` opent in Microsoft Word:

* De voetnootscheiding verschijnt **rood**.  
* De eindnootscheiding verschijnt **blauw**.  

Alle oorspronkelijke voetnoot‑ en eindnootinformatie blijft onaangeroerd.

## Letterkleur wijzigen in Word‑document met C#

De hierboven gedemonstreerde bewerking is een specifiek geval van een bredere mogelijkheid: **de letterkleur in een Word‑document wijzigen** programmatically. Zodra je een `Paragraph`, `Run` of een andere `Node` hebt die tekst bevat, kun je de eigenschap `Font.Color` aanpassen.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Deze snippet doorloopt elke paragraaf, controleert of deze de stijl `Heading 1` gebruikt, en stelt de letterkleur in.  
* Je kunt de voorwaarde aanpassen om voetnoten, tabellen of elk ander node‑type te targeten.

## Stapsgewijze uiteenzetting

### 1. Installeer Aspose.Words

Open een terminal in je projectmap en voer uit:

```bash
dotnet add package Aspose.Words
```

Het pakket bevat alle assemblies die nodig zijn voor de eerder getoonde code.

### 2. Bereid het invoerbestand voor

Plaats `Footnotes.docx` in een bekende directory (bijv. `C:\Docs`). Zorg ervoor dat het bestand minstens één voetnoot en één eindnoot bevat zodat de scheidingsteken‑nodes bestaan.

### 3. Schrijf het C#‑programma

Maak een nieuw console‑project (`dotnet new console -n FootnoteStyler`) en vervang de gegenereerde `Program.cs` door het volledige code‑blok uit de **Hoe de voetnootscheiding te wijzigen**‑sectie. Vergeet niet de bestands‑paden aan te passen aan jouw omgeving.

### 4. Uitvoeren en verifiëren

Voer het programma uit:

```bash
dotnet run
```

Na afloop open je `FootnoteSeparatorsStyled.docx`. Je zou de rode en blauwe scheidingsteken‑lijnen moeten zien zoals beschreven.

### 5. Breid de oplossing uit

* **Different colors:** Gebruik elke `System.Drawing.Color`‑waarde, bijv. `Color.FromArgb(255, 128, 0)` voor oranje.  
* **Custom line style:** In plaats van de kleur te wijzigen, kun je `ParagraphFormat`‑eigenschappen aanpassen zoals `LineSpacing`, `Shading`, of zelfs het scheidingsteken‑karakter vervangen.  
* **Multiple documents:** Plaats de logica in een methode die invoer‑ en uitvoer‑paden accepteert, en roep deze vervolgens in een lus aan voor batchverwerking.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Symptoom | Oorzaak | Oplossing |
|----------|---------|-----------|
| `GetChild` returns `null` | Het brondocument heeft geen voetnoot/eindnoot scheidingsteken (bijv. geen voetnoten). | Voeg minstens één voetnoot of eindnoot toe, of controleer op `null` voordat je `Font` benadert. |
| Color change not visible | De scheidingsteken wordt weergegeven als een lijn in plaats van een teken in sommige Word‑versies. | Stel `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` en `ParagraphFormat.LineSpacing = 1` in om een zichtbaar teken af te dwingen. |
| Runtime exception `FileNotFoundException` | Onjuist bestandspad. | Gebruik absolute paden of `Path.Combine` met `Environment.CurrentDirectory`. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren‑en‑plakken in een console‑app. Het bevat foutafhandeling en commentaren die elke bewerking toelichten.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Het uitvoeren van dit programma levert een Word‑bestand op waarin de voetnootscheiding rood is en de eindnootscheiding blauw, waarmee de **hoe je de scheidingsteken van voetnoten kunt wijzigen**‑vereiste wordt vervuld en tevens **de letterkleur in een Word‑document wijzigen** wordt gedemonstreerd.

## Conclusie

Je weet nu **hoe je de scheidingsteken van voetnoten kunt wijzigen** in een Word‑document met Aspose.Words for .NET en hoe je **de letterkleur in een Word‑document kunt wijzigen** programmatically. De aanpak is:

1. Laad het document.  
2. Haal de verborgen scheidingsteken‑paragrafen op.  
3. Stel hun `Font.Color`‑eigenschappen in.  
4. Sla het gewijzigde bestand op.

Vanaf hier kun je meer geavanceerde opmaak verkennen — de lijndikte aanpassen, verschillende lettertypen toepassen, of het proces automatiseren voor vele bestanden. Het beheersen van deze technieken geeft je fijne controle over het uiterlijk van Word‑documenten direct vanuit C#‑code.

---

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}