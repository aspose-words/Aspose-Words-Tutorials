---
category: general
date: 2025-12-29
description: Leer hoe u DPI instelt bij het converteren van Word naar PNG met Aspose.Words.
  Deze stapsgewijze tutorial behandelt ook het exporteren van PNG met hoge resolutie
  en instellingen voor beeldresolutie.
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: nl
og_description: Hoe DPI in te stellen bij het converteren van Word naar PNG met Aspose.Words.
  Volg deze gids voor export van PNG met hoge resolutie en controle over de beeldresolutie.
og_title: Hoe DPI in te stellen bij het converteren van Word naar PNG – Complete C#‑gids
tags:
- Aspose.Words
- C#
- Image Export
title: Hoe DPI in te stellen bij het converteren van Word naar PNG – Complete C#‑gids
url: /nl/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe DPI in te stellen bij het converteren van Word naar PNG – Complete C# Gids

Heb je je ooit afgevraagd **hoe je DPI kunt instellen** terwijl je een Word‑document naar PNG converteert? Misschien heb je scherpe schermafbeeldingen nodig voor een presentatie, of genereer je afdrukbare assets die er scherp uit moeten zien op 300 dpi. Hoe dan ook, je bent op de juiste plek. In deze tutorial lopen we stap voor stap door het converteren van een multi‑page `.docx` naar PNG‑afbeeldingen met hoge resolutie met behulp van Aspose.Words, en laten we je precies zien hoe je de beeldresolutie instelt zodat de output niet onscherp is.

We zullen ook tips toevoegen over **convert word to png**, **save word as png**, en een **high resolution png export** bereiken zonder moeite. Geen externe documenten, alleen een zelfstandige, uitvoerbare voorbeeldcode die je kunt copy‑paste in Visual Studio.

---

## Wat je nodig hebt

- **Aspose.Words for .NET** (latest version, e.g., 24.9).  
- .NET 6+ (or .NET Framework 4.7.2+) – elke recente runtime werkt.  
- Een Word‑bestand (`MultiPage.docx`) dat je wilt omzetten naar PNG’s.  
- Een ontwikkelomgeving – Visual Studio, Rider, of VS Code volstaat.

Dat is alles. Geen extra NuGet‑pakketten naast Aspose.Words.

---

## Stap 1: Laad het Word‑document

Eerst en vooral hebben we een in‑memory representatie van het Word‑bestand nodig. De `Document`‑klasse doet dat voor ons.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **Waarom dit belangrijk is:** Het laden van het document geeft ons toegang tot de `PageCount`, die we later nodig hebben wanneer we Aspose vertellen om **alle pagina's** als PNG te exporteren.

---

## Stap 2: Configureer ImageSaveOptions met DPI‑instellingen

Nu vertellen we Aspose dat we PNG‑output *en* een DPI‑waarde willen. De eigenschappen `ImageHorizontalResolution` en `ImageVerticalResolution` zijn waar de magie gebeurt.

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **Pro tip:** 300 dpi is de de‑facto standaard voor print‑ready graphics. Als je alleen schermkwaliteit nodig hebt, zal 96 dpi de bestandsgrootte drastisch verkleinen.

---

## Stap 3: Sla alle pagina's op als één enkele getegelde PNG (of aparte bestanden)

Aspose laat je kiezen tussen het bundelen van elke pagina in één enorme getegelde PNG **of** het schrijven van elke pagina naar een eigen bestand. Het voorbeeld hieronder toont de *enkele getegelde* aanpak, maar de `PageSavingCallback` die we hebben toegevoegd zorgt er al voor dat er aparte bestanden worden aangemaakt als je de `ExportImagesAsSeparateFiles`‑vlag omschakelt.

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

Als je één bestand per pagina wilt, stel dan simpelweg in:

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

en de callback zorgt voor het benoemen van elk `Page_#.png`.

---

## Stap 4: Verifieer de output

Na het uitvoeren van de code, open je `Pages.png` (of de gegenereerde `Page_#.png`‑bestanden) in een willekeurige afbeeldingsviewer. Je zou scherpe, hoge‑resolutie‑afbeeldingen moeten zien die overeenkomen met de lay‑out van de originele Word‑pagina's.

- **Resolutie‑check:** Rechtermuisknop → Eigenschappen → Details → Horizontale DPI / Verticale DPI → moet **300** lezen.  
- **Grootte‑check:** Bij 300 dpi wordt een typische A4‑pagina (8,27 in × 11,69 in) ongeveer 2481 × 3508 pixels – perfect voor afdrukken.

---

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| **Blurry output** | DPI bleef op standaard (96) | Stel expliciet `ImageHorizontalResolution` **en** `ImageVerticalResolution` in. |
| **Missing pages** | `PageSet` dekt alleen een subset | Gebruik `new PageSet(0, multiPageDoc.PageCount - 1)` om alle pagina's op te nemen. |
| **File name collisions** | Callback niet ingesteld | Voorzie een `PageSavingCallback` die unieke namen genereert. |
| **Large file size** | 600 dpi of hoger zonder noodzaak | Kies de laagste DPI die nog aan je kwaliteitsvereiste voldoet. |
| **Out‑of‑memory errors** for huge docs | Exporteren van een enorme getegelde PNG | Schakel over naar `ExportImagesAsSeparateFiles = true` om elke pagina afzonderlijk te schrijven. |

---

## Geavanceerd: Exporteren naar verschillende PNG‑varianten

Soms heb je een **transparante achtergrond** of een **andere kleurdiepte** nodig. Aspose.Words ondersteunt die aanpassingen via `PngOptions` binnen `ImageSaveOptions`.

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

Je kunt dit ook combineren met de bovenstaande DPI‑instellingen om een **high resolution png export** te krijgen die klaar is voor zowel web als print.

---

## Volledig werkend voorbeeld

Hieronder vind je het complete, copy‑paste‑klare programma. Vervang simpelweg `YOUR_DIRECTORY` door het daadwerkelijke pad op jouw machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

Voer het programma uit, en je hebt een **high resolution PNG export** van elke pagina, elk met de exacte DPI die je hebt ingesteld.

---

## Veelgestelde vragen

**Q: Werkt dit ook met oudere `.doc`‑bestanden?**  
A: Absoluut. Aspose.Words abstraheert het formaat, zodat dezelfde code `.doc`, `.docx`, `.rtf` en zelfs `.odt` aankan.

**Q: Kan ik exporteren naar JPEG in plaats van PNG?**  
A: Ja – wijzig simpelweg `SaveFormat.Png` naar `SaveFormat.Jpeg` en pas `JpegOptions` aan indien nodig.

**Q: Wat als ik 600 dpi nodig heb voor een groot poster?**  
A: Stel `ImageHorizontalResolution =  en `ImageVerticalResolution = 600` in. Houd het geheugenverbruik in de gaten; hoge DPI‑waarden vergroten de pixelafmetingen snel.

**Q: Is er een manier om veel Word‑bestanden in batch te verwerken?**  
A: Plaats de bovenstaande logica in een `foreach (var file in Directory.GetFiles(folder, "*.docx"))`‑lus. Vergeet niet elke `Document`‑instantie te disposen of een enkele `ImageSaveOptions`‑object te hergebruiken voor efficiëntie.

---

## Conclusie

We hebben behandeld **hoe je DPI kunt instellen** wanneer je **Word naar PNG converteert** met Aspose.Words, de nuances van **high resolution PNG export** besproken, en je een kant‑klaar code‑voorbeeld gegeven dat **save word as png** met precieze beeldresolutie‑controle. Door `ImageHorizontalResolution`, `ImageVerticalResolution` en eventueel `PngOptions` aan te passen, kun je met vertrouwen print‑ready graphics of lichte web‑assets genereren.

Volgende stappen? Experimenteer met verschillende DPI‑waarden, schakel over naar exporteren als aparte bestanden, of combineer deze workflow met een PDF‑naar‑PNG‑pipeline voor nog bredere documentafhandeling. Dezelfde principes gelden wanneer je **set image resolution png** voor andere formaten, zodat je nu uitgerust bent om een breed scala aan afbeelding‑exportscenario's aan te kunnen.

Happy coding, en moge je PNG’s altijd vlijmscherp zijn! 

![Hoe DPI in te stellen bij het converteren van Word naar PNG – voorbeeldoutput](/images/how-to-set-dpi-word-to-png.png "hoe DPI instellen")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}