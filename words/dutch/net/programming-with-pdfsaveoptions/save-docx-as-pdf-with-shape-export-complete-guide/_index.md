---
category: general
date: 2026-02-13
description: Sla docx op als pdf terwijl zwevende vormen behouden blijven. Leer hoe
  je Word naar pdf converteert, vormen exporteert en randgevallen in C# afhandelt.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: nl
og_description: Sla docx op als pdf terwijl zwevende vormen behouden blijven. Deze
  gids laat zien hoe je Word naar pdf converteert, vormen exporteert en veelvoorkomende
  valkuilen aanpakt.
og_title: Docx opslaan als PDF met Shape Export – Complete gids
tags:
- Aspose.Words
- C#
- PDF conversion
title: Docx opslaan als pdf met Shape Export – Complete gids
url: /nl/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save docx as pdf – Full‑stack Tutorial (C#)

Heb je ooit moeten **save docx as pdf** en die zwevende diagrammen er precies hetzelfde uit laten zien? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur aan wanneer de vormen van Word verdwijnen of vervormd raken na conversie. Het goede nieuws? Met een paar regels C# kun je de bibliotheek vertellen elke vorm als een blok‑niveau element te behandelen, en het resultaat is een getrouwe PDF‑replicatie.

In deze gids lopen we het volledige proces door: een `.docx`‑bestand laden, de **convert word to pdf**‑opties configureren zodat vormen correct worden geëxporteerd, en uiteindelijk de PDF naar schijf schrijven. Aan het einde weet je **how to export shapes**, begrijpt de afwegingen van verschillende exportmodi, en heb je een kant‑klaar code‑voorbeeld dat je in elk .NET‑project kunt gebruiken.

> **What you’ll get:** een compleet, uitvoerbaar voorbeeld, uitleg over *waarom* elke instelling belangrijk is, tips voor randgevallen, en ideeën om de oplossing uit te breiden (bijv. afbeeldingen verwerken, aangepaste lettertypen, of wachtwoord‑beveiligde PDF's).

---

## Voorvereisten

- .NET 6+ (of .NET Framework 4.7+). De API die we gebruiken werkt op beide.
- Aspose.Words for .NET (gratis proefversie of gelicentieerde versie). Installeer via NuGet: `Install-Package Aspose.Words`.
- Een Word‑document (`input.docx`) dat zwevende vormen bevat (tekstvakken, auto‑shapes, SmartArt, enz.).
- Visual Studio 2022 of een IDE naar keuze.

Er zijn geen andere externe bibliotheken nodig.

---

## Stapsgewijze Implementatie

Onder elke stap zie je een korte code‑snippet, een eenvoudige Engelse uitleg, en een opmerking over **how to export shapes** correct.

### ## Stap 1 – Laad het brondocument (save docx as pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Waarom dit belangrijk is:* De `Document`‑klasse vertegenwoordigt het volledige Word‑bestand in het geheugen. Als je deze stap overslaat, is er niets om te converteren, en hebben de daaropvolgende PDF‑opties niets om op toe te passen.

### ## Stap 2 – Configure PDF save options (how to export shapes)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Uitleg**

- `PdfSaveOptions` is een “bag of settings” die Aspose.Words vertelt hoe Word‑constructies naar PDF te vertalen.
- De **ExportFloatingShapesAsInlineTag**‑eigenschap heeft drie mogelijke waarden:
  1. **Inline** – vormen worden inline‑elementen (vaak samengedrukt in de omringende tekst).
  2. **Block** – elke vorm wordt op een eigen blok geplaatst, wat de veiligste manier is om het oorspronkelijke uiterlijk te behouden.
  3. **Auto** – de bibliotheek beslist automatisch (kies niet altijd de beste optie).

Het kiezen van **Block** is de aanbevolen aanpak wanneer je *need to export shapes* precies zoals ze in het originele document verschijnen. Het voorkomt het “shape disappears”‑probleem dat veel mensen ondervinden bij het simpelweg aanroepen van `doc.Save("out.pdf")`.

### ## Stap 3 – Save the document as PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*Wat je zult zien:* Nadat deze regel is uitgevoerd, staat `FloatingShapes.pdf` in `C:\MyFolder`. Open het, en je zou elk tekstvak, elke callout en elke SmartArt moeten zien, precies gepositioneerd zoals in de bron‑`.docx`.

---

## Volledig Werkend Voorbeeld

Hieronder staat het **complete program** dat je kunt compileren en uitvoeren als een console‑applicatie. Het bevat alle benodigde `using`‑statements en commentaren voor duidelijkheid.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Verwachte output**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Open de resulterende PDF en controleer of alle vormen hun oorspronkelijke posities behouden. Als een vorm er nog steeds verkeerd uitziet, controleer dan dubbel of het echt een *floating* vorm is (in tegenstelling tot een inline‑afbeelding) in Word.

---

## Veelgestelde Vragen & Randgevallen

| Question | Answer |
|----------|--------|
| **Kan ik vormen exporteren als inline in plaats van block?** | Ja – stel `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline` in. Dit kan nuttig zijn voor eenvoudige lay-outs, maar verwacht een strakkere tekststroom en mogelijke overlapping. |
| **Wat als mijn document afbeeldingen bevat binnen vormen?** | Dezelfde optie werkt; Aspose.Words rasteriseert de vorm samen met de afbeelding. Voor de hoogste getrouwheid, schakel ook `PdfSaveOptions.JpegQuality` in als je betere beeldcompressie nodig hebt. |
| **Werkt dit met wachtwoord‑beveiligde DOCX‑bestanden?** | Laad het document met een `LoadOptions`‑object dat het wachtwoord levert, en ga vervolgens normaal verder. |
| **Kan ik meerdere DOCX‑bestanden in één batch converteren?** | Plaats de drie‑stappen‑logica in een `foreach`‑lus over een bestandslijst. Vergeet niet `PdfSaveOptions` te hergebruiken voor prestaties. |
| **Is de PDF compatibel met oudere lezers (Acrobat 7)?** | Standaard maakt Aspose.Words PDF 1.7‑bestanden. Stel `pdfOptions.Compliance = PdfCompliance.PdfA1b` in voor archief‑grade PDF's die werken op legacy‑lezers. |

---

## Pro Tips & Veelvoorkomende Valkuilen

- **Pro tip:** Als je lichte verticale verschuivingen na conversie opmerkt, probeer dan `pdfOptions.UsePdfDocumentStructure = true` in te stellen. Dit dwingt de PDF‑engine om de Word‑layouthierarchie te respecteren.
- **Let op:** Documenten die zwevende vormen combineren met verankerde tabellen. In sommige gevallen kan de block‑export een tabel naar een nieuwe pagina duwen; je kunt dit mitigeren door `pdfOptions.PageSetup` aan te passen vóór het opslaan.
- **Prestatie‑opmerking:** Het hergebruiken van één `PdfSaveOptions`‑instantie voor veel bestanden vermindert GC‑druk en versnelt batch‑conversies.

---

## Visuele Referentie

Hieronder staat een schematische screenshot (placeholder) die het voor/na van een document met een zwevend tekstvak toont.

![save docx as pdf example with floating shapes](image-placeholder.png "save docx as pdf example with floating shapes")

*De afbeelding illustreert hoe de vorm precies op dezelfde plek blijft als in het originele Word‑bestand na conversie.*

---

## Samenvatting

We hebben **how to save docx as pdf** behandeld terwijl elke zwevende vorm intact blijft, de **convert word to pdf**‑instellingen die van belang zijn verkend, en de meest voorkomende “**how to export shapes**”‑vragen beantwoord. Het complete code‑voorbeeld is klaar om in elk C#‑project te gebruiken, en de optionele aanpassingen geven je flexibiliteit voor real‑world scenario’s zoals batch‑verwerking of PDF/A‑compliance.

### Volgende Stappen

- Probeer **convert word document pdf** met verschillende compliance‑niveaus (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) om te voldoen aan regelgeving.
- Experimenteer met **how to convert docx pdf** voor wachtwoord‑beveiligde bestanden—voeg `LoadOptions` toe met een wachtwoord en `PdfSaveOptions` met `EncryptionDetails`.
- Verken andere uitvoerformaten (bijv. XPS, HTML) met hetzelfde `Document`‑object; de enige wijziging is het `Save`‑method argument voor het formaat.

Heb je meer vragen? Laat een reactie achter, en happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}