---
category: general
date: 2026-03-22
description: Maak een rechthoekvorm in C# en voeg een schaduw toe aan de vorm met
  Aspose.Words. Leer hoe je een schaduw toevoegt, hoe je een rechthoek maakt en hoe
  je de schaduweigenschappen instelt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: nl
og_description: Maak een rechthoekvorm in C# en voeg een schaduw toe aan de vorm met
  Aspose.Words. Stapsgewijze handleiding die behandelt hoe je een schaduw toevoegt,
  hoe je een rechthoek maakt en hoe je de schaduw instelt.
og_title: Maak een rechthoekvorm met schaduw in C# – Volledige gids
tags:
- Aspose.Words
- C#
- Document Automation
title: Maak een rechthoekvorm met schaduw in C# met Aspose.Words
url: /nl/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een rechthoekvorm met schaduw in C# met Aspose.Words

Heb je ooit een **create rectangle shape** moeten maken in een Word‑document, maar wist je niet hoe je er een subtiele slagschaduw aan moet geven? Je bent niet de enige—veel ontwikkelaars lopen tegen dit probleem aan wanneer ze voor het eerst met documentautomatisering experimenteren. In deze gids lopen we precies uit hoe je **add shadow to shape** gebruikt met Aspose.Words, en we beantwoorden ook “**how to add shadow**”, “**how to create rectangle**” en “**how to set shadow**” onderweg.

We beginnen met een lege `Document`, tekenen een rechthoek, schakelen de schaduw in, passen de vervaging, afstand, hoek en kleur aan, en slaan tenslotte het bestand op. Aan het einde heb je een kant‑klaar `.docx` dat een grijs getinte rechthoek toont die net boven de pagina zweeft. Geen mysterie, gewoon recht‑toe‑rechtaan code die je kunt kopiëren‑plakken in elk .NET‑project.

## Vereisten

Before we dive in, make sure you have:

* **Aspose.Words for .NET** (de nieuwste versie vanaf maart 2026). Je kunt het ophalen via NuGet met `Install-Package Aspose.Words`.
* Een .NET‑ontwikkelomgeving – Visual Studio, Rider, of zelfs VS Code met de C#‑extensie werkt prima.
* Basiskennis van C# – niets bijzonders, alleen het vermogen om een console‑ of WinForms‑app te maken.

Dat is alles. Geen extra bibliotheken, geen verborgen stappen. Klaar? Laten we beginnen.

## Stap 1: Initialiseer een nieuw leeg document

Om **create rectangle shape** te maken, hebben we eerst een container nodig – een `Document`‑object – dat het Word‑bestand vertegenwoordigt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

De `Document`‑klasse is het toegangspunt voor alles wat Aspose.Words doet. Beschouw het als een leeg canvas; zonder dit kun je geen vormen, tabellen of tekst toevoegen.

## Stap 2: Maak de rechthoek die de schaduw zal bevatten

Nu gaan we **how to create rectangle** door een `Shape` van het type `Rectangle` te instantieren. We stellen ook de grootte in punten in (1 punt ≈ 1/72 inch).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Waarom 200 × 100 punten kiezen? Het is een behoorlijke grootte voor een demo – groot genoeg om de schaduw duidelijk te zien, maar niet zo enorm dat het de pagina overweldigt. Voel je vrij om deze getallen aan te passen aan je lay‑out.

## Stap 3: Schakel het schaduweffect in en configureer het uiterlijk

Dit is het hart van de tutorial: **how to add shadow** en **how to set shadow** eigenschappen. Aspose.Words biedt een `Shadow`‑object op elke vorm, waarmee je het effect kunt in- of uitschakelen en visuele parameters kunt aanpassen.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** verzacht de randen – een hogere waarde maakt de schaduw meer diffuus.
* **Distance** duwt de schaduw verder van de rechthoek af.
* **Angle** bepaalt waar het licht vandaan lijkt te komen; 45° geeft een diagonale, natuurlijke uitstraling.
* **Color** laat je elke `System.Drawing.Color` kiezen. Grijs is een veilige standaard, maar je kunt gewaagd gaan met `Color.Black` of subtiel met `Color.LightGray`.

Pro tip: Als je `Enabled = false` instelt, worden alle andere schaduwinstellingen genegeerd, dus controleer die vlag altijd dubbel.

## Stap 4: Voeg de vorm in de document‑body in

Met de rechthoek klaar en de schaduw geconfigureerd, moeten we deze in het document plaatsen. De eenvoudigste manier is om het toe te voegen aan de eerste alinea van de eerste sectie.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Als je document al tekst bevat, kun je een specifieke `Paragraph` of zelfs een `Table`‑cel zoeken en de vorm daar invoegen. De `AppendChild`‑methode is veelzijdig – hij werkt met elk `Node`‑type.

## Stap 5: Sla het document op en controleer het resultaat

Tot slot schrijven we het bestand naar schijf. Pas het pad aan naar waar je wilt; de map moet bestaan, anders krijg je een uitzondering.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Open het resulterende `ShadowedRectangle.docx` in Microsoft Word (of LibreOffice) en je zou een grijze rechthoek moeten zien met een scherpe, diagonale schaduw die naar rechtsonder beweegt. Als de schaduw te zwak lijkt, verhoog dan `BlurRadius` of `Distance` en voer de code opnieuw uit – experimenteren is onderdeel van het plezier.

![Voorbeeld van rechthoekvorm met schaduw](rectangle-shadow.png){alt="Voorbeeld van rechthoekvorm met schaduw"}

### Verwachte output

* Een één‑pagina Word‑document.
* Een grijze rechthoek van 200 × 100 punten, gepositioneerd links‑boven op de pagina.
* Een subtiele grijze schaduw, verschoven met 8 pixels onder een hoek van 45°, vervaagd met 5 pixels.

## Hoe schaduw toevoegen aan vorm – dieper duiken

Je vraagt je misschien af, *“Kan ik de schaduw animeren of laten veranderen op basis van gebruikersinvoer?”* Hoewel Aspose.Words zelf geen animatie ondersteunt, kun je de schaduweigenschappen programmatically aanpassen vóór het opslaan, waardoor je effectief meerdere versies van hetzelfde document met verschillende looks maakt. Bijvoorbeeld, een lus over een collectie kleuren:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Dat kleine fragment toont **how to set shadow** dynamisch—ideaal voor het genereren van thematische rapporten.

## Hoe rechthoek maken – alternatieve vormen

Als je een afgeronde rechthoek nodig hebt, wijzig dan simpelweg de `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Of, voor een perfecte vierkant, stel `Width` gelijk aan `Height`. Dezelfde schaduweigenschappen gelden, dus je bent al gedekt voor **how to add shadow** voor elke vorm die je kiest.

## Veelvoorkomende valkuilen en probleemoplossing

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| Schaduw verschijnt niet | `Shadow.Enabled` staat op `false` | Zet `rectangleShape.Shadow.Enabled = true;` |
| Schaduw ziet er te scherp uit | `BlurRadius` ingesteld op 0 | Verhoog `BlurRadius` tot minstens 3 |
| Document geeft `FileNotFoundException` bij opslaan | Doelmap bestaat niet | Maak de map eerst aan of gebruik een geldig pad |
| Vorm is onzichtbaar | Width/Height ingesteld op 0 | Zorg dat beide afmetingen > 0 zijn |

Deze problemen in de gaten houden bespaart je de klassieke “waarom wordt mijn vorm niet weergegeven?”‑moment.

## Samenvatting – wat we hebben bereikt

* **Create rectangle shape** in een nieuw Word‑document met Aspose.Words.  
* **Add shadow to shape** door de `Shadow.Enabled`‑vlag te toggelen en blur, distance, angle en color aan te passen.  
* Gedemonstreerd **how to add shadow**, **how to create rectangle**, en **how to set shadow** in een nette, herbruikbare code‑snippet.  
* Een volledig, kant‑klaar voorbeeld geleverd dat je in elk C#‑project kunt plakken.

## Wat is het volgende?

Nu je de basis onder de knie hebt, overweeg het volgende te verkennen:

* **How to add shadow to images** – dezelfde `Shadow`‑API werkt voor `ShapeType.Image`.
* **Combining multiple shapes** – maak stroomdiagrammen of infographics direct in Word.
* **Exporting to PDF** – roep `document.Save("output.pdf")` aan na het toevoegen van schaduwen voor een afdrukbare versie.

Voel je vrij om te experimenteren met verschillende kleuren, hoeken, of zelfs verloopvullingen. De API is flexibel genoeg om professionele documenten te maken zonder ooit Word handmatig te openen.

---

Veel plezier met coderen! Als je tegen problemen aanloopt, laat dan een reactie achter of bekijk de Aspose.Words‑forums – de community helpt snel.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}