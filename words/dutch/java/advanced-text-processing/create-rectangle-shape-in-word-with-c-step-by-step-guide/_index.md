---
category: general
date: 2026-03-04
description: Learn how to create rectangle shape, add shadow to shape and apply shadow
  effect in a Word document, then save Word document automatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: nl
og_description: Maak een rechthoekvorm, voeg een schaduw toe aan de vorm en pas het
  schaduweffect toe in een Word‑document met C#. Volg deze gids om moeiteloos een
  Word‑document op te slaan.
og_title: Maak een rechthoekvorm in Word – Complete C#‑tutorial
tags:
- C#
- Aspose.Words
- Document Automation
title: Rechthoekvorm maken in Word met C# – Stapsgewijze handleiding
url: /nl/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een rechthoekige vorm in Word met C# – Complete programmeertutorial

Heb je ooit **create rectangle shape** nodig gehad in een Word‑bestand maar wist je niet waar te beginnen? Je bent niet de enige—veel ontwikkelaars lopen tegen die muur aan wanneer ze voor het eerst duiken in programmatische documentgeneratie. Het goede nieuws is dat je met een paar regels C# een rechthoek kunt invoegen, **add shadow to shape**, en **apply shadow effect** zonder Word zelf ooit te openen. In deze gids lopen we het volledige proces door, van een verse **create blank document** tot het opslaan van het uiteindelijke **save word document** op schijf.

We behandelen alles wat je nodig hebt: het vereiste NuGet‑pakket, de exacte API’s, waarom elke eigenschap belangrijk is, en een reeks tips om de meest voorkomende valkuilen te vermijden. Aan het einde heb je een volledig uitvoerbaar voorbeeld dat je in elk .NET‑project kunt gebruiken.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Visual Studio 2022 of elke IDE die je verkiest
- **Aspose.Words for .NET** geïnstalleerd via NuGet (`Install-Package Aspose.Words`)
- Basiskennis van C#‑syntaxis

Er zijn geen extra Word‑interop‑bibliotheken nodig—Aspose.Words verwerkt alles in het geheugen.

## Stap 1 – Create a blank document

Het eerste wat we doen is **create blank document**. Beschouw het als het lege canvas waarop we later **create rectangle shape** zullen plaatsen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Waarom dit belangrijk is:** Door te beginnen met een schoon `Document`‑object wordt gegarandeerd dat geen verborgen stijlen of secties later de positionering van de vorm beïnvloeden.

## Stap 2 – Insert a rectangle shape into the document

Nu maken we daadwerkelijk **create rectangle shape**. We stellen de grootte en positie in en vertellen Word om geen tekst eromheen te laten wikkelen.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tip:** Als je wilt dat de rechthoek zich binnen een tabelcel bevindt, wijzig `WrapType` naar `WrapType.Inline`. Voor de meeste rapporten houdt `None` de vorm zwevend boven de tekst.

## Stap 3 – Add shadow to shape and configure its appearance

Hier gebeurt de magie: we **add shadow to shape** en **apply shadow effect**. Het schaduw laat de rechthoek op de pagina opvallen, vooral bij afdrukken.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Waarom deze waarden?**  
> - **BlurRadius** bepaalt hoe wazig de randen lijken; een waarde rond `5` geeft een subtiele, professionele uitstraling.  
> - **Transparency** zorgt ervoor dat de onderliggende tekst leesbaar blijft.  
> - **OffsetX/Y** verplaatsen de schaduw van de vorm, waardoor diepte ontstaat.  
> - Het gebruik van een **blue** tint is slechts een voorbeeld—elke `System.Drawing.Color` werkt.

## Stap 4 – Add the configured shape to the document body

Met de rechthoek volledig gestyled, **add rectangle shape** nu aan de eerste sectie van het document. Deze stap plaatst de vorm daadwerkelijk in het bestand.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Randgeval:** Als je document al secties bevat, wil je misschien een specifieke targeten (`doc.Sections[2]` bijvoorbeeld). De bovenstaande code werkt voor een document met één sectie, wat gebruikelijk is voor snelle rapporten.

## Stap 5 – Save the Word document

Tot slot **save word document** we naar schijf. Het bestand bevat de rechthoek met zijn schaduw, klaar om geopend te worden in Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tip:** Gebruik `doc.Save(outputPath, SaveFormat.Docx)` als je expliciet het formaat moet aangeven. De `Save`‑methode detecteert automatisch de extensie, maar expliciet zijn kan verwarring voorkomen wanneer het pad programmatisch wordt gegenereerd.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een console‑applicatie. Het bevat alle `using`‑statements en de `Main`‑methode, zodat je het direct kunt uitvoeren.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Verwacht resultaat

Wanneer je *shadowed_rectangle.docx* opent in Microsoft Word, zie je een blauw‑omrande rechthoek die zweeft nabij de bovenkant van de eerste pagina, met een zachte blauwe schaduw die 8 pt naar rechts en beneden is verschoven. Er staat geen extra tekst omheen omdat we `WrapType.None` hebben ingesteld.

## Veelgestelde vragen & variaties

| Question | Answer |
|----------|--------|
| **Kan ik de vorm wijzigen naar een ellips?** | Ja—vervang `ShapeType.Rectangle` door `ShapeType.Ellipse`. Alle schaduw‑eigenschappen blijven gelijk. |
| **Wat als ik meerdere vormen nodig heb?** | Herhaal simpelweg Stappen 2‑4 voor elke nieuwe `Shape`‑instantie, en pas `OffsetX/Y` of `Left/Top` aan om overlapping te voorkomen. |
| **Is er een manier om de schaduwkleur te laten overeenkomen met de vulling van de vorm?** | Absoluut. Stel eerst `rectangle.FillColor` in, en wijs daarna `rectangle.ShadowFormat.Color = rectangle.FillColor;` toe. |
| **Hoe voeg ik de vorm toe aan een tabelcel?** | Gebruik `cell.FirstParagraph.AppendChild(rectangle);` nadat je het gewenste `Cell`‑object hebt gevonden. |
| **Werkt dit op .NET Core?** | Ja—Aspose.Words is cross‑platform. Zorg er alleen voor dat je de juiste NuGet‑pakketversie voor .NET Core/5/6 referereert. |

## Veelvoorkomende valkuilen & pro‑tips

- **Pitfall:** Het vergeten om `ShadowFormat.Visible = true` in te stellen. De schaduw‑eigenschappen worden stilzwijgend genegeerd.  
  **Fix:** Schakel altijd de zichtbaarheid in voordat je andere schaduw‑parameters aanpast.

- **Pitfall:** Het gebruik van een zeer grote `BlurRadius` (bijv. 20) kan de schaduw er wazig en onprofessioneel uit laten zien.  
  **Fix:** Houd je aan waarden tussen `3` en `8` voor de meeste zakelijke documenten.

- **Pro tip:** Als je wilt dat de vorm later selecteerbaar is (bijv. voor bewerking door eindgebruikers), vermijd het instellen van `WrapType.Inline`. Zwevende vormen (`WrapType.None`) zijn programmeermatig makkelijker te verplaatsen.

- **Pro tip:** Bij het genereren van veel documenten in een lus, hergebruik een enkele `Document`‑instantie en roep `doc.Clone(true)` aan voor elke iteratie om de prestaties te verbeteren.

## Gerelateerde onderwerpen die je hierna kunt verkennen

- **Add text inside a rectangle shape** – leer hoe je `Shape.TextPath` kunt gebruiken voor labels.  
- **Create complex diagrams** – combineer meerdere vormen, connectoren en groeperen.  
- **Export to PDF** – converteer hetzelfde document naar PDF met een enkele `doc.Save("output.pdf")`.  
- **Apply different fill styles** – verlopen, texturen, of zelfs afbeeldingen binnen vormen.

## Conclusie

We hebben zojuist **create rectangle shape**, **add shadow to shape**, en **apply shadow effect** in een Word‑bestand met C#. Door de vijf beknopte stappen te volgen, heb je nu een herbruikbaar patroon voor elke document‑automatiseringsscenario, en weet je hoe je **save word document** betrouwbaar kunt uitvoeren. Voel je vrij om afmetingen, kleuren aan te passen, of zelfs de rechthoek te vervangen door een andere geometrie—Aspose.Words maakt alles eenvoudig.

Als je deze tutorial nuttig vond, geef hem een ster op GitHub, of deel je eigen variaties in de reacties. Veel plezier met coderen, en moge je documenten er altijd net zo gepolijst uitzien als deze schaduwrijke rechthoek!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}