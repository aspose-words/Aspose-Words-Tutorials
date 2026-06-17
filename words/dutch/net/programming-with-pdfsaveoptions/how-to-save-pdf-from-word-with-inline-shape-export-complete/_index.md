---
category: general
date: 2026-06-02
description: Hoe PDF opslaan vanuit een DOCX met Aspose.Words, vormen exporteren als
  inline span‑tags en Word naar PDF converteren in slechts een paar stappen.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: nl
og_description: Hoe PDF opslaan vanuit een Word‑document met Aspose.Words, waarbij
  zwevende vormen worden geëxporteerd als inline span‑tags voor een schoon Word‑naar‑PDF‑conversieresultaat.
og_title: Hoe PDF opslaan vanuit Word – Tutorial voor Inline Shape Export
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Hoe PDF opslaan vanuit Word met Inline Shape‑export – Complete gids
url: /nl/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe PDF opslaan vanuit Word met Inline Shape Export – Complete gids

Heb je je ooit afgevraagd **hoe je PDF kunt opslaan** vanuit een Word‑bestand terwijl elke zwevende vorm netjes in de tekststroom blijft? Je bent niet de enige. In veel bedrijfsapplicaties moeten we *Word naar PDF converteren* zonder dat er verkeerd geplaatste afbeeldingen of losse tekenobjecten ontstaan. Het goede nieuws? Aspose.Words maakt het moeiteloos, en je kunt de bibliotheek zelfs laten **vormen exporteren als inline `<span>`‑tags** zodat de PDF er precies uitziet als de originele DOCX.

In deze tutorial lopen we het volledige proces door — een DOCX laden, de `PdfSaveOptions` aanpassen, en uiteindelijk een nette PDF opslaan. Aan het einde weet je **hoe je PDF kunt opslaan**, **docx als pdf opslaan**, en zelfs **hoe je vormen kunt exporteren** met *inline span‑tags*.

## Wat je nodig hebt

- **Aspose.Words for .NET** (latest version, 24.x at the time of writing).  
- **.NET 6.0** of later – de code werkt ook op .NET Framework 4.7.2, maar .NET 6 is de ideale keuze.  
- Een eenvoudig Word‑document dat minstens één zwevende vorm bevat (afbeelding, tekstvak of tekening).  
- Elke IDE die je wilt (Visual Studio, Rider, VS Code + C#‑extensie).  

Dat is alles — geen extra NuGet‑pakketten, geen ingewikkelde COM‑interop. Klaar? Laten we beginnen.

## Stap 1: Het project instellen en Aspose.Words toevoegen

Maak eerst een console‑applicatie (of integreer de code in je bestaande service).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Als je Visual Studio gebruikt, kun je het pakket toevoegen via de NuGet Package Manager UI — zoek gewoon naar *Aspose.Words*.

## Stap 2: Laad het bron‑document

Nu de bibliotheek is gerefereerd, kunnen we de DOCX laden. Dit is de eerste concrete actie van het **hoe je PDF kunt opslaan**‑deel — het bronbestand in het geheugen laden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Waarom dit belangrijk is:** Het laden van het bestand controleert of het pad correct is en of Aspose de Word‑structuur kan parseren. Als het bestand zwevende vormen bevat, maken deze deel uit van de `Document`‑object‑nodeboom.

## Stap 3: PDF‑opslaan‑opties configureren – Vormen exporteren als inline‑tags

Dit is het hart van **hoe je vormen kunt exporteren**. Standaard rendert Aspose.Words zwevende vormen als afzonderlijke objecten in de PDF, wat de lay‑out kan verschuiven. Door `ExportFloatingShapesAsInlineTag` op `true` te zetten, wordt elke vorm ingepakt in een inline `<span>`‑element, waardoor de stroom behouden blijft.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Waarom deze vlag inschakelen?** Stel je een contract voor met een handtekeningvak dat boven de tekst zweeft. Wanneer je het naar PDF converteert zonder deze instelling, kan het vak op een andere pagina verschijnen. Inline `<span>`‑tags houden de vorm verankerd aan de omringende alinea, waardoor een getrouwe visuele replica ontstaat.

## Stap 4: Het document opslaan als PDF

Tot slot roepen we `doc.Save` aan met de opties die we zojuist hebben opgebouwd. Dit is het moment waarop je daadwerkelijk **docx als pdf opslaat**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Voer het programma uit (`dotnet run`) en controleer de `output.pdf`. Je zou je zwevende vormen inline weergegeven moeten zien, precies zoals ze in Word verschenen.

## Stap 5: Controleer het resultaat – Snelle checklist

1. **Alle tekst is aanwezig** – geen ontbrekende alinea’s.  
2. **Zwevende vormen verschijnen waar ze moeten** – ze maken nu deel uit van de tekststroom.  
3. **PDF‑grootte is redelijk** – exporteren als inline‑tags vermindert meestal de bestandsgrootte vergeleken met afzonderlijke afbeeldingsstromen.  

Als er iets niet klopt, controleer dan dubbel of het bron‑DOCX echt *zwevende* vormen gebruikt (rechtermuisklik → Layout → “In lijn met tekst” vs “Vierkant/Achter tekst”). Een vorm naar “In lijn” wijzigen vóór conversie werkt ook, maar de inline‑tag‑optie geeft je controle zonder het originele bestand te bewerken.

## Randgevallen & Veelgestelde vragen

### Wat als mijn document **SmartArt** of **Grafieken** bevat?

SmartArt en grafieken worden behandeld als tekenobjecten. De `ExportFloatingShapesAsInlineTag`‑vlag zal ze nog steeds in `<span>`‑tags plaatsen, maar complexe grafieken kunnen wat kwaliteit verliezen. Overweeg in die gevallen de grafiek eerst als afbeelding te exporteren (`Chart.ToImage()`) en vervolgens inline in te voegen.

### Kan ik **hyperlinks** en **bladwijzers** behouden?

Absoluut. Deze elementen worden niet beïnvloed door de `ExportFloatingShapesAsInlineTag`‑instelling. Aspose.Words behoudt automatisch alle hyperlink‑ en bladwijzerinformatie.

### Hoe wijzig ik **PDF‑compressie** of **lettertypen insluiten**?

`PdfSaveOptions` biedt veel extra eigenschappen:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

Voel je vrij om die instellingen aan te passen op basis van je downstream‑vereisten (bijv. PDF/A‑conformiteit).

## Volledig werkend voorbeeld (klaar om te kopiëren‑plakken)

Hieronder staat het volledige programma dat je kunt kopiëren naar `Program.cs`. Vervang `YOUR_DIRECTORY` door een echt mappad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Verwachte output in de console:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Open `output.pdf` — je ziet de originele lay‑out, met elke zwevende vorm netjes geplaatst binnen de tekststroom.

## Conclusie

We hebben **hoe je PDF kunt opslaan** vanuit een Word‑document behandeld, terwijl we ervoor zorgen dat zwevende vormen inline `<span>`‑tags worden. Door de DOCX te laden, `PdfSaveOptions` te configureren en `doc.Save` aan te roepen, kun je betrouwbaar **docx als pdf opslaan** en **word naar pdf converteren** zonder onverwachte lay‑out.  

Volgende stappen? Probeer deze aanpak te combineren met **PDF/A**‑conformiteit voor archivering, of verwerk een map met DOCX‑bestanden in batch met een eenvoudige `foreach`‑lus. Je kunt ook **aangepaste rendering** verkennen (bijv. watermerken toevoegen) door gebruik te maken van Aspose.Words’ `DocumentVisitor`‑API.

Heb je meer vragen over vormafhandeling, het insluiten van lettertypen, of prestatie‑optimalisatie? Laat een reactie achter hieronder, en happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Convert DOCX to PDF in Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}