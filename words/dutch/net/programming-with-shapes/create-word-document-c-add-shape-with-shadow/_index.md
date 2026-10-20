---
category: general
date: 2026-03-27
description: Maak een Word‑document in C# en leer hoe je een vorm toevoegt, een schaduw
  op de vorm toepast en de schaduwafstand instelt. Stapsgewijze handleiding voor Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: nl
og_description: Maak een Word-document in C# met een rechthoekvorm en aangepaste schaduw.
  Volg deze volledige tutorial om de schaduwafstand en stijl in te stellen.
og_title: Word-document maken C# – Vorm met schaduw toevoegen
tags:
- Aspose.Words
- C#
- Document Automation
title: Word-document maken C# – Vorm met schaduw toevoegen
url: /nl/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-document maken met C# – Vorm toevoegen met schaduw

Heb je ooit een **create word document c#** nodig gehad die een mooi gestileerde rechthoek bevat? Misschien bouw je een rapporttemplate en wil je een subtiele slagschaduw om de lay-out meer te laten opvallen. In deze tutorial lopen we precies dat stap voor stap door – hoe je een vorm toevoegt, een schaduw op de vorm toepast en zelfs de schaduwdistance aanpast met Aspose.Words.

We beginnen met een leeg document, voegen een rechthoek toe, geven het een voorgedefinieerde schaduw en slaan het bestand op. Aan het einde heb je een kant‑klaar .docx dat je in Word kunt openen en direct het effect ziet. Geen externe tools, alleen pure C#‑code.

## Vereisten

- .NET 6 (of een recente .NET Framework) geïnstalleerd.
- Visual Studio 2022 of VS Code met C#‑extensie.
- Aspose.Words for .NET NuGet‑pakket (`Aspose.Words` versie 23.12 of later).  
  Je kunt het toevoegen via de Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

Dat is alles – geen extra DLL’s of COM‑interop nodig.

## Stap 1: Een nieuw document en builder initialiseren – *create word document c#* basisprincipes

Eerst hebben we een `Document`‑object nodig dat het Word‑bestand vertegenwoordigt en een `DocumentBuilder` om het te bewerken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Waarom deze stap belangrijk is:** De `Document`‑klasse is de container voor alle Word‑onderdelen (pagina’s, stijlen, afbeeldingen). De builder is de high‑level API die low‑level knooppuntmanipulatie abstraheert, waardoor het eenvoudig is om **create word document c#** uit te voeren zonder direct met XML te werken.

## Stap 2: Een rechthoekvorm invoegen – *how to create rectangle*  

Nu plaatsen we een rechthoek op de pagina. De grootte wordt uitgedrukt in punten (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tip:** Als je een andere vorm nodig hebt, vervang dan simpelweg `ShapeType.Rectangle` door `ShapeType.Ellipse`, `ShapeType.Triangle`, enz. Dezelfde code werkt voor **how to add shape** van elk type.

## Stap 3: Een voorgedefinieerde schaduw toepassen en verfijnen – *apply shadow to shape*  

Aspose.Words wordt geleverd met verschillende voorgedefinieerde schaduwformaten. We gebruiken `Preset1` en passen vervolgens afstand, vervaging, transparantie en kleur aan.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Waarom de schaduw aanpassen?** De `Distance`‑eigenschap bepaalt hoe ver de schaduw van de rechthoek af staat – zie het als de “lift” die je in een 3‑D‑rendering zou zien. Het wijzigen van `BlurRadius` verzacht de randen, terwijl `Transparency` je een subtiele, professionele uitstraling geeft. Dit dekt de **set shadow distance**‑vereiste en laat zien hoe je **apply shadow to shape** op een flexibele manier kunt toepassen.

## Stap 4: Het document opslaan – *create word document c#* voltooiing

Tot slot schrijf je het document naar schijf. Pas het pad aan naar een map waar je schrijfrechten voor hebt.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Open het resulterende bestand in Microsoft Word, en je ziet een lichtblauwe rechthoek met een zachte grijze schaduw die 5 pt is verschoven. Dat is het visuele bewijs dat je succesvol **create word document c#** hebt gemaakt met een gestylede vorm.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# voorbeeld dat een rechthoek met schaduw toont"}

## Optionele variaties & randgevallen

| Scenario | Wat te wijzigen | Waarom het belangrijk is |
|----------|----------------|--------------------------|
| **Andere schaduwstijl** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Geeft je een dramatischer uiterlijk zonder extra code. |
| **Geen preset – aangepaste schaduw** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Volledige controle over richting en diepte. |
| **Meerdere vormen** | Call `builder.InsertShape` again before saving. | Handig voor complexe sjablonen met iconen, logo’s, enz. |
| **Compatibiliteit met oudere Aspose‑versies** | Use `ShadowEffect` class (available in v20.x). | Zorgt ervoor dat je code werkt in legacy‑projecten. |
| **Opslaan als PDF** | `document.Save("ShadowShape.pdf");` | Dezelfde schaduwweergave verschijnt in de PDF‑output. |

> **Veelgestelde vraag:** *Wat als de schaduw niet verschijnt in Word?*  
> Zorg ervoor dat je een recente versie van Aspose.Words gebruikt (≥ 22.9). Oudere releases hadden beperkte schaduwondersteuning. Controleer ook dat het document wordt geopend in een recente versie van Word (2016+).

## Volledig werkend voorbeeld

Hieronder staat het volledige, kant‑klaar te kopiëren programma. Het bevat alle `using`‑directieven, commentaren en foutafhandeling voor een soepele ervaring.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Voer het programma uit, ga naar `C:\Temp\ShadowShape.docx`, en je ziet de rechthoek met de exacte schaduw die we hebben geconfigureerd.

## Samenvatting & volgende stappen

- Je weet nu hoe je **create word document c#** maakt, een rechthoek invoegt, en **apply shadow to shape** toepast met een aangepaste **set shadow distance**.  
- Het voorbeeld gebruikt Aspose.Words, dat de OpenXML‑complexiteit abstraheert en consistente weergave garandeert over verschillende Word‑versies.  
- Wil je verder gaan? Probeer meerdere vormen te combineren, tekst binnen de rechthoek toe te voegen, of hetzelfde document als PDF te exporteren om te zien hoe de schaduw wordt overgezet.

### Gerelateerde onderwerpen die je kunt verkennen

- **How to add shape** aan een header/footer voor branding.  
- Gebruik van **Aspose.Words** om grafieken en tabellen programmatisch in te voegen.  
- **shadow effects** aanpassen op afbeeldingen in plaats van vectorvormen.  
- Bulk‑documentgeneratie automatiseren voor facturen of certificaten.

Voel je vrij om te experimenteren, de code te breken en vervolgens opnieuw op te bouwen – dat is de snelste manier om de concepten te internaliseren. Als je tegen een probleem aanloopt, laat dan een reactie achter of raadpleeg de officiële Aspose.Words‑documentatie voor diepere API‑inzichten.

Veel plezier met coderen, en geniet ervan om je Word‑bestanden er net iets netter uit te laten zien!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}