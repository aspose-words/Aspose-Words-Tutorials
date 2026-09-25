---
category: general
date: 2026-02-26
description: Maak een rechthoekvorm in Word met Aspose.Words en leer hoe je een vorm
  aan Word toevoegt, een schaduw op de vorm toepast en de transparantie van de vorm
  instelt in enkele minuten.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: nl
og_description: Maak een rechthoekvorm in Word met Aspose.Words. Leer hoe je een vorm
  aan Word toevoegt, een schaduw op de vorm toepast en de transparantie van de vorm
  snel instelt.
og_title: Rechthoekvorm maken in Word – Volledige Aspose.Words-gids
tags:
- Aspose.Words
- C#
- Word Automation
title: Rechthoekvorm maken in Word – Volledige Aspose.Words-gids
url: /nl/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in Word – Volledige Aspose.Words-gids

Heb je ooit een **create rectangle shape** nodig gehad in een Word‑document, maar wist je niet waar je moest beginnen? Je bent niet de enige—veel ontwikkelaars lopen tegen die muur aan bij het automatiseren van rapporten of facturen. In deze tutorial lopen we een compleet, kant‑klaar voorbeeld door dat laat zien hoe je **add shape to Word** kunt uitvoeren, een subtiele schaduw toepast en de transparantie van de vorm regelt, allemaal met Aspose.Words voor .NET.

Aan het einde van de gids heb je een `.docx`‑bestand met een nette rechthoek en een gepolijste schaduw—perfect voor branding, call‑outs, of gewoon om je document er iets professioneler uit te laten zien. Geen externe tools nodig, alleen een paar regels C#.

## Wat je nodig hebt

- **Aspose.Words for .NET** (de nieuwste versie vanaf begin 2026). Je kunt het ophalen via NuGet (`Install-Package Aspose.Words`).
- Een .NET‑ontwikkelomgeving (Visual Studio, Rider, of VS Code met de C#‑extensie).
- Basiskennis van C#‑syntaxis—niets bijzonders, alleen de gebruikelijke `using`‑statements en objectcreatie.

Als je die al hebt, geweldig—laten we erin duiken.

## Rechthoekvorm maken – Kernstappen

Hieronder staat de volledige broncode. Kopieer‑en plak deze in een nieuw console‑project, druk op **F5**, en je ziet `ShadowDemo.docx` verschijnen in de opgegeven map.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Waarom dit werkt

- **`Document`** is het toegangspunt; het vertegenwoordigt het volledige Word‑bestand.
- **`Shape`** met `ShapeType.Rectangle` vertelt Aspose dat we een rechthoekig tekenobject willen.
- Het instellen van **`Width`** en **`Height`** geeft de vorm een deterministische grootte; anders wordt een klein tijdelijke aanduiding gebruikt.
- Het **`Shadow`**‑object stelt ons in staat elk visueel aspect fijn af te stemmen: vervaging, afstand, richting, kleur, transparantie en spreiding. Dat is de kern van *apply shadow to shape*.
- Ten slotte injecteert **`AppendChild`** de vorm in de eerste alinea van het document, wat de eenvoudigste manier is om *add shape to Word* uit te voeren zonder tabellen of kop‑/voetteksten te gebruiken.

Wanneer je `ShadowDemo.docx` opent, zie je een grijze rechthoek comfortabel in het document geplaatst, met een schaduw die naar beneden‑rechts helt onder een hoek van 45°. De schaduw is geen massief blok; de vervagingsradius verzacht de randen, en de transparantie zorgt ervoor dat het eruitziet als een natuurlijke slagschaduw in plaats van een harde overlay.

![voorbeeld van rechthoekvorm maken](image.png "rechthoekvorm met schaduw in Word maken met Aspose.Words")

*(De bovenstaande afbeelding toont het uiteindelijke resultaat van de code‑snippet.)*

## Vorm toevoegen aan Word‑document – Plaatsingsopties

Het voorbeeld gebruikt de **eerste alinea** omdat dit de snelste manier is om iets op het scherm te zien. In praktijkscenario's wil je misschien:

- De vorm invoegen in een specifieke **section** of **header/footer**.
- Plaats deze in een **table cell** voor uitlijning met tabelgegevens.
- Omwikkel deze met **text wrapping**‑opties (bijv. `WrapType.Square`) zodat omliggende tekst rond de rechthoek stroomt.

Hier is een snelle variatie die de vorm in een nieuwe alinea met een aangepaste stijl plaatst:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Pro tip:* Voeg de vorm altijd **na** het configureren van de eigenschappen toe; anders moet je mogelijk `UpdateLayout` aanroepen om het visuele uiterlijk te vernieuwen.

## Schaduw toepassen op vorm – Fijnafstemming van het uiterlijk

Schaduwen kunnen de esthetiek van een document drastisch veranderen. De `Shadow`‑klasse biedt verschillende eigenschappen:

| Eigenschap | Wat het regelt | Typische waarden |
|------------|----------------|------------------|
| `BlurRadius` | Softness of the shadow edges | 2.0 – 10.0 |
| `Distance` | How far the shadow is offset from the shape | 1.0 – 8.0 |
| `Direction` | Angle in degrees (0 = left, 90 = up) | 0 – 360 |
| `Color` | Shadow colour (any `System.Drawing.Color`) | Gray, Black, Custom |
| `Transparency`| Opacity (0 = fully opaque, 1 = invisible) | 0.0 – 0.5 |
| `Spread` | Expansion of the shadow before blur is applied | 0.0 – 1.0 |

Als je een **subtiel, professioneel uiterlijk** wilt, houd `BlurRadius` rond 4‑6 en `Transparency` nabij 0.2, net als in de bovenstaande code. Voor een **dramatisch effect** verhoog je `Distance` naar 6, stel je `Direction` in op 135° en verlaag je `Transparency` tot 0.05.

## Vormtransparantie en schaduwspreiding instellen

Transparantie gaat niet alleen over de schaduw; je kunt de rechthoek zelf ook gedeeltelijk doorschijnend maken:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Het combineren van een semi‑transparante vulling met een zachte schaduw geeft vaak een modern UI‑gevoel—ideaal voor dashboards of design‑mock‑ups die in rapporten zijn ingebed.

### Randgevallen om in de gaten te houden

1. **Oudere Word‑versies** (pre‑2007) ondersteunen sommige schaduweigenschappen niet. Als je `.doc`‑bestanden target, overweeg dan de schaduw te vereenvoudigen (bijv. `BlurRadius` op 0 zetten).
2. **High DPI‑schermen** kunnen de schaduw iets anders weergeven. Test in de doelomgeving als visuele nauwkeurigheid cruciaal is.
3. **Overlap‑vormen**—Aspose rendert schaduwen in de volgorde waarin ze worden toegevoegd. Voeg vormen van achter naar voren toe om ongewenste overdekking te voorkomen.

## Opslaan en resultaat verifiëren

De `Document.Save`‑methode detecteert automatisch het uitvoerformaat op basis van de bestandsextensie. Voor een **`.docx`**‑bestand krijg je het Open XML‑formaat, dat de meeste moderne Word‑processors begrijpen. Als je een **PDF**‑versie met dezelfde visuele stijl nodig hebt, wijzig dan simpelweg de extensie:

```csharp
document.Save("ShadowDemo.pdf");
```

Het openen van het gegenereerde `ShadowDemo.docx` (of `ShadowDemo.pdf`) moet een nette **rechthoek met schaduw** tonen, waarmee bevestigd wordt dat je succesvol *create rectangle shape* en *apply shadow to shape* hebt uitgevoerd met Aspose.Words.

## Veelgestelde vragen

**Q: Kan ik een andere vorm gebruiken, zoals een ellips?**  
A: Absoluut. Vervang `ShapeType.Rectangle` door `ShapeType.Ellipse` (of een andere `ShapeType`‑enum). De schaduweigenschappen blijven gelijk.

**Q: Wat als ik wil dat de rechthoek klikbaar is?**  
A: Je kunt een hyperlink aan de vorm toewijzen:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Werkt dit op .NET 6+?**  
A: Ja. Aspose.Words 23.11 en later ondersteunen volledig .NET 6, .NET 7 en .NET 8. Verwijs gewoon naar het juiste NuGet‑pakket.

**Q: Hoe wijzig ik de schaduwkleur zodat deze bij mijn merk past?**  
A: Gebruik elke `System.Drawing.Color` die je wilt:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Samenvatting

We hebben alles behandeld wat je nodig hebt om **create rectangle shape** in een Word‑document te maken, **add shape to Word**, **apply shadow to shape** en **set shape transparency**. De volledige, uitvoerbare code staat bovenaan deze pagina, en de uitleg zou je voldoende vertrouwen moeten geven om afmetingen, kleuren en schaduwparameters voor elk project aan te passen.

Klaar voor de volgende stap? Probeer te experimenteren met:

- Meerdere vormen die samen worden gestapeld voor een badge‑effect.
- Dynamische afmetingen op basis van documentinhoud (bijv. breedte berekenen uit een tabelkolom).
- Het exporteren van het document naar PDF of HTML terwijl de schaduw behouden blijft.

Voel je vrij om een reactie achter te laten als je ergens tegenaan loopt, of deel je eigen variaties op het “rechthoek met schaduw”‑thema.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}