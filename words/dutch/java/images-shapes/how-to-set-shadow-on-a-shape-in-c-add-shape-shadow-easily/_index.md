---
category: general
date: 2026-04-28
description: Hoe je snel een schaduw op een vorm instelt. Leer hoe je een vormschaduw
  toevoegt, de schaduwkleur instelt en de vormschaduw aanpast met Aspose.Words voor
  .NET.
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: nl
og_description: Hoe je een schaduw op een vorm instelt in C# met Aspose.Words. Stapsgewijze
  handleiding over het toevoegen van een vormschaduw, het instellen van de schaduwkleur
  en het aanpassen van de vormschaduw.
og_title: Hoe schaduw op een vorm instellen in C# – Complete gids
tags:
- Aspose.Words
- C#
- Document Automation
title: Hoe je een schaduw op een vorm instelt in C# – Voeg eenvoudig een vormschaduw
  toe
url: /nl/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe je een schaduw aan een vorm toevoegt in C# – Voeg eenvoudig vormschaduw toe

Heb je je ooit afgevraagd **hoe je een schaduw** aan een vorm kunt toevoegen zonder eindeloos door API‑documentatie te speuren? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur aan wanneer ze een subtiele slagschaduw nodig hebben om een diagram te laten opvallen, maar ze vinden geen helder voorbeeld dat zowel het “wat” als het “waarom” laat zien.  

In deze tutorial lopen we stap voor stap door het toevoegen van een vormschaduw, het wijzigen van de schaduwkleur en het fijn afstellen van de vervaging, offset en transparantie – alles met Aspose.Words voor .NET. Aan het einde heb je een kant‑klaar code‑fragment dat je in elk C#‑project kunt plakken, plus een aantal tips om vormschaduw in complexere scenario’s aan te passen.

> **Opmerking:** De code werkt met Aspose.Words 22.9 of later en vereist .NET 6+ (of .NET Framework 4.7.2+).  

![Vorm met aangepaste schaduw](shape-shadow.png "Vorm met aangepaste schaduw")

## Wat je zult leren

- **Vormschaduw toevoegen** programmatically aan de eerste vorm in een Word‑document.  
- **Schaduwkleur instellen** op elke `System.Drawing.Color`.  
- **Vormschaduw aanpassen** door de vervagingsradius, offsets en transparantie te wijzigen.  
- Hoe je meerdere vormen kunt behandelen en schaduwinstellingen kunt resetten indien nodig.  

Geen externe tools, geen Visual Basic‑macro’s – alleen pure C#.

---

## Voorwaarden

| Voorwaarde | Waarom het belangrijk is |
|------------|--------------------------|
| **Aspose.Words for .NET** (NuGet‑package `Aspose.Words`) | Biedt de `Document`, `Shape` en `ShadowFormat` klassen die in het voorbeeld worden gebruikt. |
| **.NET 6 SDK** (of .NET Framework 4.7.2) | Garandeert compatibiliteit met de nieuwste API‑surface. |
| **Een .docx‑bestand** met ten minste één vorm (bijv. een rechthoek of afbeelding) | De tutorial wijzigt de *eerste* vorm; je kunt er één maken in Word als je er geen hebt. |

Installeer de bibliotheek met:

```bash
dotnet add package Aspose.Words
```

---

## Stapsgewijs: Hoe je een schaduw aan een vorm toevoegt

### 1. Laad het Word‑document

We beginnen met het openen van het `.docx`‑bestand. De `Document`‑constructor leest het bestand in het geheugen, zodat we volledige toegang hebben tot de knooppunten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Waarom?** Het document laden is de basis – zonder dit kun je de vormboom niet doorlopen.

### 2. Haal de eerste vorm op (of een andere gewenste vorm)

Aspose.Words slaat vormen op als knooppunten van type `NodeType.SHAPE`. De `GetChild`‑methode laat ons het *n‑de* vormobject ophalen; hier nemen we index 0, dus de eerste vorm.

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **Pro‑tip:** Als je **vormschaduw wilt toevoegen** aan een specifieke vorm, vervang dan de index door de juiste waarde of iterateer door `doc.GetChildNodes(NodeType.Shape, true)`.

### 3. Toegang tot het schaduw‑opmaakobject

Elke `Shape` heeft een `ShadowFormat`‑eigenschap die alle schaduw‑gerelateerde instellingen blootlegt.

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

Nu kunnen we de schaduw gaan aanpassen.

### 4. Stel de vervagingsradius in – verzacht de randen

Een grotere vervagingsradius maakt de schaduw meer diffuus. De waarde staat in punten (1 pt ≈ 1/72 inch).

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **Wanneer aanpassen?** Als je vorm klein is, kan een vervaging van 2–3 pt voldoende zijn; voor grote banners kun je 8–10 pt gebruiken.

### 5. Definieer horizontale en verticale offsets

Offsets bepalen hoe ver de schaduw van de vorm wordt verplaatst. Positieve waarden verplaatsen de schaduw naar rechts/onder; negatieve waarden verplaatsen naar links/boven.

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. Pas transparantie (opaciteit) aan

`Transparency` varieert van `0.0` (volledig ondoorzichtig) tot `1.0` (volledig onzichtbaar). Een waarde rond `0.3` geeft een subtiel, halfdoorzichtig effect.

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. Kies een schaduwkleur – **schaduwkleur instellen** op elke `System.Drawing.Color`

Je kunt elke vooraf gedefinieerde kleur kiezen of een eigen kleur maken met RGB‑waarden.

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

Wil je een klassieke zwarte schaduw, gebruik dan simpelweg `Color.Black`.

### 8. Sla het gewijzigde document op

Tot slot schrijf je de wijzigingen weg. Je kunt het originele bestand overschrijven of naar een nieuwe locatie schrijven.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## Volledig werkend voorbeeld (Alle stappen in één blok)

Kopieer‑en‑plak het volgende in de `Main`‑methode van een console‑applicatie. Het compileert direct, mits het NuGet‑package is geïnstalleerd.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**Verwacht resultaat:** Open `output_with_shadow.docx` in Word; de eerste vorm toont nu een zachte blauwe schaduw, verschoven met 3 pt, met een subtiele vervaging en 30 % transparantie.

---

## Veelvoorkomende variaties & randgevallen

### Schaduwen toevoegen aan *alle* vormen

Bevat je document meerdere diagrammen, dan kun je over elke vorm itereren:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### Een schaduw resetten

Soms heeft een vorm al een schaduw die je moet verwijderen. Stel `ShadowFormat.Visible` in op `false`:

```csharp
shape.ShadowFormat.Visible = false;
```

### Een aangepaste kleur met alfa (halfdoorzichtig) gebruiken

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### Compatibiliteitsopmerking

De `ShadowFormat`‑API is stabiel over Aspose.Words‑versies, maar oudere releases (< 19.1) gebruikten `ShadowFormat`‑velden met iets andere benamingen. Richt je altijd op het nieuwste NuGet‑package voor de beste resultaten.

---

## Pro‑tips voor een gepolijste schaduw

- **Balans tussen vervaging en offset:** Een sterke vervaging met een kleine offset kan er “glow‑achtig” uitzien in plaats van een echte slagschaduw. Experimenteer met `BlurRadius` × `DistanceX/Y`.
- **Pas aan op documentthema:** Gebruikt het Word‑bestand een donker thema, dan kan een lichte schaduw (`Color.White`) een subtiel lift‑effect geven.
- **Prestaties:** Het aanpassen van schaduwen op honderden vormen kan enkele milliseconden per vorm kosten. Batch de bewerking bij grote rapporten.
- **Testen:** Open het resulterende `.docx` zowel in Word Desktop als Word Online om te controleren of de schaduw consistent wordt weergegeven.

---

## Conclusie

We hebben net behandeld **hoe je een schaduw aan een vorm toevoegt** met C#. Door de acht stappen hierboven te volgen kun je **vormschaduw toevoegen**, **schaduwkleur instellen** en de **vormschaduw volledig aanpassen** aan elke ontwerp‑taal. Het voorbeeld staat op zichzelf, werkt direct, en biedt een solide basis om de logica uit te breiden naar meerdere vormen, dynamische kleuren of zelfs door de gebruiker gedefinieerde parameters.

Klaar voor de volgende uitdaging? Probeer deze techniek te combineren met **vormrotatie**, of genereer een volledig rapport waarin elk diagram zijn eigen merk‑schaduw krijgt. De mogelijkheden zijn eindeloos, en de code die je nu kent is een perfect springplank.

Als je deze gids nuttig vond, geef dan een ster aan de repository, laat een reactie achter, of deel je eigen schaduw‑tweaktips hieronder. Veel programmeerplezier!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}