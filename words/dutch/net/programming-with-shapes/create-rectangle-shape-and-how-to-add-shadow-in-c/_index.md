---
category: general
date: 2026-04-04
description: Maak een rechthoekvorm in C# met Aspose.Words en leer hoe je een schaduw
  toevoegt, vervaging op de schaduw toepast en de schaduw transparant maakt – stapsgewijze
  handleiding.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: nl
og_description: Maak een rechthoekvorm in C# met Aspose.Words. Leer hoe je een schaduw
  toevoegt, vervaging op de schaduw toepast en de schaduw transparant maakt in een
  beknopte tutorial.
og_title: Rechthoekvorm maken en hoe je schaduw toevoegt in C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Rechthoekvorm maken en hoe schaduw toe te voegen in C#
url: /nl/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken en hoe schaduw toe te voegen in C#

Heb je ooit **een rechthoekvorm** in een Word‑document moeten maken, maar wist je niet hoe je er een subtiele slagschaduw aan kon geven? Je bent niet de enige. In veel rapportage‑ of branding‑scenario’s kan een eenvoudige rechthoek met een zachte, half‑transparante schaduw de lay‑out een gepolijste uitstraling geven zonder veel moeite.

In deze tutorial lopen we stap voor stap door **hoe een document te maken** met Aspose.Words, vervolgens laten we zien **hoe je een schaduw toevoegt**, **blur toepassen op de schaduw**, en zelfs **de schaduw transparant maakt**. Aan het einde heb je een kant‑klaar C#‑fragment dat een *.docx*-bestand produceert met een mooi gearceerde rechthoek—alles in een paar minuten.

## Wat je nodig hebt

- .NET 6 of later (de API werkt ook met .NET Framework 4.6+)
- Aspose.Words for .NET (de gratis proefversie werkt voor dit voorbeeld)
- Een code‑editor – Visual Studio, VS Code, Rider, wat je ook verkiest
- Basis C#‑kennis – niets ingewikkelds, alleen het vermogen om een console‑applicatie uit te voeren

Als je die hebt, kunnen we direct naar de oplossing springen.

## Stap 1 – Hoe een document te maken en het canvas te initialiseren

Allereerst: je hebt een leeg `Document`‑object nodig. Beschouw het als een leeg vel papier dat Aspose.Words later zal omzetten in een Word‑bestand.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Waarom maken we een `Document`‑instantie in plaats van een sjabloon te laden? Vanaf nul beginnen garandeert dat er geen verborgen stijlen of secties onze rechthoek beïnvloeden. Het houdt ook de bestandsgrootte klein – een goede gewoonte wanneer je veel documenten in een lus genereert.

## Stap 2 – Rechthoekvorm maken (de kern van ons primaire trefwoord)

Nu maken we daadwerkelijk **een rechthoekvorm**. De `Shape`‑klasse is flexibel; je geeft het het type (Rectangle), de grootte en hoe het moet omsluiten met omringende tekst.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Let op het gebruik van object‑initializer‑syntaxis – het is beknopt en verkleint de kans dat je later een eigenschap vergeet in te stellen. De rechthoek zal binnen de eerste alinea worden geplaatst, die we in de volgende stap toevoegen.

## Stap 3 – Hoe schaduw toe te voegen en het uiterlijk aan te passen

Een schaduw toevoegen is niet slechts één regel; je hebt verschillende eigenschappen om aan te passen. Hier komen de secundaire trefwoorden **blur toepassen op de schaduw** en **de schaduw transparant maken** in beeld.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Een korte opmerking over de getallen: een `BlurRadius` van 5 geeft een zachte vedering; verhoog dit naar 10 voor een zachtere uitstraling, of verlaag het naar 2 voor een scherpe rand. De `Transparency`‑waarde varieert van 0 (ondoorzichtig) tot 1 (onzichtbaar). Pas aan op basis van de contrastvereisten van je merk.

### Pro‑tip

Als je ooit een gekleurde schaduw nodig hebt (bijvoorbeeld een bedrijfsblauw), vervang dan gewoon `Color.DarkGray` door `Color.FromArgb(80, 0, 120, 215)`. Het eerste argument is het alfa‑kanaal – houd het laag voor subtiliteit.

## Stap 4 – De vorm in het document invoegen

Met de rechthoek en zijn schaduw klaar, plaatsen we deze nu in de eerste alinea van het document. Deze stap zorgt ervoor dat de vorm bovenaan het bestand verschijnt.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Waarom de eerste alinea? Het is een veilige standaard die werkt zelfs wanneer het document volledig leeg is. Als je een specifieke locatie hebt (bijv. na een koptekst), zou je dat knooppunt zoeken en de vorm daar invoegen.

## Stap 5 – Het bestand opslaan en het resultaat verifiëren

Tot slot slaan we het document op schijf op. Je kunt elk pad kiezen dat je wilt; zorg er alleen voor dat de map bestaat.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Wanneer je *ShadowRectangle.docx* opent in Microsoft Word, zou je een rechthoek van 200 × 100 punten moeten zien met een donkergrijze, licht vervaagde, 30 % transparante schaduw die drie punten naar rechts en omlaag is verschoven. Het effect is subtiel maar voegt diepte toe aan anders vlakke lay‑outs.

![rechthoekvorm met schaduw in Aspose.Words](https://example.com/placeholder-image.png "rechthoekvorm met schaduw in Aspose.Words")

*Afbeeldings‑alt‑tekst:* **rechthoekvorm met schaduw in Aspose.Words** – de afbeelding toont het uiteindelijke document met de gearceerde rechthoek.

## Veelvoorkomende variaties en randgevallen

### Kleur van de schaduw dynamisch wijzigen

Als je applicatie thema's ondersteunt, kun je de kleur van de schaduw uit een configuratie‑bestand halen:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### De vorm niet‑inline maken

Soms wil je dat de rechthoek zweeft boven de tekst. Schakel `WrapType` over naar `WrapType.Square` en stel `RelativeHorizontalPosition` in op `RelativeHorizontalPosition.Margin` voor meer controle.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Meerdere pagina's verwerken

Als je een rechthoek op elke pagina nodig hebt, loop dan door `doc.Sections` en voeg een gekloonde vorm toe aan de eerste alinea van elke sectie. Vergeet niet `rect.Clone(true)` aan te roepen om ook de schaduwinstellingen te dupliceren.

## Samenvatting – Wat we hebben bereikt

- **Rechthoekvorm gemaakt** using Aspose.Words
- **Hoe schaduw toe te voegen** met kleur, offset, blur en transparantie
- Gedemonstreerd **blur toepassen op de schaduw** en **de schaduw transparant maken**
- Een Word‑bestand opgeslagen dat je direct kunt openen

Dit alles werd bereikt met slechts een handvol regels, wat bewijst dat geavanceerde visuele aanpassingen niet altijd zware grafische bibliotheken vereisen.

## Wat is het volgende?

- Experimenteer met andere `ShapeType`s (Ellipse, Cloud, enz.) en zie hoe schaduwen zich gedragen.
- Combineer de rechthoek met tekstvakken om gelabelde call‑outs te maken.
- Duik in **hoe een document te maken** sjablonen die al placeholders voor vormen bevatten, en vul ze vervolgens programmatically in.

Voel je vrij om de blur‑radius, kleur of transparantie aan te passen totdat de schaduw er precies goed uitziet voor je ontwerp‑taal. De API is vergevingsgezind, en de wijzigingen zijn direct zichtbaar wanneer je de console‑app opnieuw uitvoert.

Veel plezier met coderen, en moge je documenten altijd die extra diepte hebben!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}