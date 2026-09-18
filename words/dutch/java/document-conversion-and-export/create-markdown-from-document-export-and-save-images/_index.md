---
category: general
date: 2026-02-18
description: Maak markdown van een document met eenvoudige stappen om het document
  naar markdown te exporteren en afbeeldingen op te slaan in een submap. Leer hoe
  je een document als markdown opslaat in C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: nl
og_description: Maak markdown van een document in C# en leer hoe je een document naar
  markdown exporteert terwijl je afbeeldingen opslaat in een submap. Volg de stapsgewijze
  handleiding.
og_title: Maak markdown van document – Exporteer en sla afbeeldingen op
tags:
- C#
- Aspose.Words
- Markdown export
title: Maak markdown van document – Exporteer en sla afbeeldingen op
url: /nl/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak markdown van document – Exporteren en afbeeldingen opslaan

Heb je ooit **markdown van document maken** nodig gehad, maar wist je niet hoe je de ingesloten afbeeldingen netjes kunt houden? Je bent niet de enige. In veel projecten genereren we rapporten, handleidingen of blogconcepten programmatically, en het laatste wat we willen is een rommel van afbeeldingsbestanden verspreid over de outputmap.  

In deze tutorial lopen we een complete, kant‑klaar oplossing door die **document naar markdown exporteert**, elke afbeelding opslaat in een toegewijde *md‑resources* sub‑map, en uiteindelijk **document als markdown opslaat** met de Aspose.Words for .NET API. Aan het einde heb je een enkele methode die je in elke C# codebase kunt gebruiken, plus een aantal tips voor het omgaan met randgevallen.

> **Snelle blik:**  
> • Stel `MarkdownSaveOptions` in  
> • Geef een `IResourceSavingCallback` op die afbeeldingen naar een submap leidt  
> • Roep `Document.Save` aan met de geconfigureerde opties  

Als je benieuwd bent waarom we een callback kiezen in plaats van post‑processing, lees dan verder – de reden wordt stap voor stap uitgelegd.

---

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)  
- Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`)  
- Een bron `Document`‑object (kan een .docx, .pdf, .rtf, enz. zijn)  

Er zijn geen extra bibliotheken nodig; de callback‑API is ingebouwd in Aspose.Words.

---

## Stap 1: Maak markdown van document – configureer opslaan‑opties

Het eerste wat we doen is `MarkdownSaveOptions` instantieren. Dit object vertelt Aspose.Words hoe de conversie zich moet gedragen, zoals welke Markdown‑variant te gebruiken, of afbeeldingen als Base64 in te sluiten, en waar de gegenereerde bestanden geplaatst moeten worden.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Waarom dit belangrijk is:**  
> Zonder expliciet `MarkdownSaveOptions` te maken, valt de bibliotheek terug op standaardinstellingen die afbeeldingen direct in het Markdown‑bestand insluiten als Base64‑strings. Dat maakt het bestand enorm groot en ondermijnt het doel van een nette *images* map.

---

## Stap 2: Exporteer document naar markdown en definieer resource‑afhandeling

Nu vertellen we de saver **waar** elke afbeelding moet worden geplaatst. De `IResourceSavingCallback`‑interface geeft ons een hook die wordt geactiveerd voor elke resource (afbeelding, SVG, enz.) die tijdens de export wordt ontdekt. Binnen de callback doen we:

1. Zorg ervoor dat de doelmap bestaat (`md-resources/`).  
2. Stel `OutputFileName` in op de map plus de oorspronkelijke resource‑naam.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Veelgestelde vraag:** *Wat als ik afbeeldingen wil insluiten in plaats van opslaan?*  
> Sla gewoon de callback over of stel `args.OutputFileName = null;` in – de saver zal de afbeelding automatisch als een Base64‑string insluiten.  

> **Randgeval:** Sommige oudere documenten bevatten dubbele afbeeldingsnamen. De bovenstaande callback zal het vorige bestand overschrijven. Om dat te voorkomen, kun je een GUID toevoegen:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Stap 3: Sla document op als markdown en controleer opgeslagen afbeeldingen

Met de opties volledig geconfigureerd, is de laatste aanroep een één‑regelcode die het Markdown‑bestand en de bijbehorende afbeeldingen naar schijf schrijft.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Als alles goed gaat zie je:

- `MyReport.md` – de Markdown‑representatie van je bron‑document.  
- `md-resources/` – een map naast het .md‑bestand die elke geëxtraheerde afbeelding bevat (bijv. `image001.png`, `image002.jpg`).  

**Voorbeeld Markdown‑fragment** (automatisch gegenereerd door Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Pro tip:** Open het gegenereerde `.md`‑bestand in VS Code of een andere Markdown‑previewer; de afbeeldingen zouden direct moeten worden weergegeven omdat de relatieve paden overeenkomen met de mapstructuur.

---

## Volledig, uitvoerbaar voorbeeld

Hieronder staat een zelfstandige console‑applicatie die je kunt plakken in een nieuw .NET‑project en uitvoeren. Het maakt een eenvoudig Word‑document, voegt een afbeelding toe, en vervolgens **markdown van document maken** terwijl de afbeelding in een submap wordt opgeslagen.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Wat je zou moeten zien** na het uitvoeren:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Open `ExportedDoc.md` – de afbeeldingsreferentie zal wijzen naar `md-resources/sample-image.png`, en de afbeelding zal correct worden weergegeven in elke Markdown‑viewer.

---

## Veelgestelde variaties

| Scenario | Hoe de code aan te passen |
|----------|---------------------------|
| **Afbeeldingen exporteren overslaan** (insluiten als Base64) | Omit `ResourceSavingCallback` entirely, or set `args.OutputFileName = null;` inside the callback. |
| **Afbeeldingsformaat wijzigen** (bijv. allemaal PNG) | Inside the callback, modify `args.ResourceFileName` and optionally convert the stream before writing. |
| **Aangepaste mapnaam** | Replace `"md-resources/"` with any relative or absolute path you prefer. |
| **Meerdere documenten in één batch** | Loop over a collection of `Document` objects, reusing the same `MarkdownSaveOptions` instance (just ensure the folder is cleared or uniquely named per run). |

---

## Conclusie

We hebben je zojuist **hoe je markdown van document maakt**, **document naar markdown exporteert**, en **afbeeldingen opslaat in een submap** laten zien met een schone, callback‑gedreven aanpak. De belangrijkste punten zijn:

- Gebruik `MarkdownSaveOptions` om fijnmazige controle over de export te krijgen.  
- Implementeer `IResourceSavingCallback` om afbeeldingen naar een toegewijde map te leiden, zodat je Markdown netjes blijft.  
- Hetzelfde patroon werkt voor andere resource‑typen (SVG, audio) – inspecteer gewoon `args.ResourceType`.  

Vervolgens kun je **document opslaan als markdown** verkennen met aangepaste kopstijlen, of deze routine integreren in een ASP.NET Web API die een ZIP retourneert met het `.md`‑bestand en de resources. Hoe dan ook, de bouwstenen zitten nu in je gereedschapskist.

Heb je vragen, of een randgeval ontdekt dat we niet hebben behandeld? Laat een reactie achter hieronder, en happy coding!

---

![create markdown from document example](placeholder.png "create markdown from document example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}