---
category: general
date: 2025-12-08
description: Voeg snel schaduw toe aan een vorm met Aspose.Words. Leer hoe je een
  Word‑document maakt met Aspose, hoe je vormschaduw toevoegt en schaduwtransparantie
  toepast in C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: nl
og_description: Schaduw toevoegen aan vorm in een Word‑bestand met Aspose.Words. Deze
  stapsgewijze handleiding laat zien hoe je een document maakt, een vorm toevoegt
  en schaduwtransparantie toepast.
og_title: Schaduw toevoegen aan vorm – Aspose.Words C#-handleiding
tags:
- Aspose.Words
- C#
- Word Automation
title: Schaduw toevoegen aan vorm in een Word‑document – Complete Aspose.Words‑gids
url: /dutch/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Schaduw toevoegen aan vorm – Complete Aspose.Words-gids

Heb je ooit **schaduw aan een vorm** moeten toevoegen in een Word‑bestand, maar wist je niet welke API‑aanroepen je moest gebruiken? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur wanneer ze voor het eerst een rechthoek of een ander tekenobject een echte slagschaduw willen geven, vooral wanneer ze werken met Aspose.Words voor .NET.

In deze tutorial lopen we alles door wat je moet weten: van **een Word‑document maken met Aspose** tot het configureren van de schaduw, het aanpassen van de vervaging, afstand, hoek en zelfs **schaduwtransparantie toepassen**. Aan het einde heb je een kant‑klaar C#‑programma dat een `.docx`‑bestand produceert met een mooi gearceerde rechthoek—geen handmatig geknoei in Word nodig.

---

## Wat je zult leren

- Hoe je een Aspose.Words‑project opzet in Visual Studio.  
- De exacte stappen om **een Word‑document te maken met Aspose** en een vorm in te voegen.  
- **Hoe je vormschaduw toevoegt** met volledige controle over vervaging, afstand, hoek en transparantie.  
- Tips voor het oplossen van veelvoorkomende valkuilen (bijv. ontbrekende licentie, onjuiste eenheden).  
- Een complete, copy‑and‑paste code‑voorbeeld dat je vandaag nog kunt uitvoeren.

> **Voorwaarden:** .NET 6+ (of .NET Framework 4.7.2+), een geldige Aspose.Words‑licentie (of de gratis proefversie), en een basiskennis van C#.

---

## Stap 1 – Stel je project in en voeg Aspose.Words toe

Allereerst. Open Visual Studio, maak een nieuwe **Console App (.NET Core)** aan en voeg het Aspose.Words‑NuGet‑pakket toe:

```bash
dotnet add package Aspose.Words
```

> **Pro‑tip:** Als je een licentiebestand (`Aspose.Words.lic`) hebt, kopieer dit dan naar de project‑root en laad het bij het opstarten. Dit voorkomt het watermerk dat verschijnt in de gratis evaluatiemodus.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Stap 2 – Maak een nieuw leeg document

Nu **maken we een Word‑document met Aspose**. Dit object dient als het canvas voor onze vorm.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

De `Document`‑klasse is het toegangspunt voor alles wat volgt—alinea’s, secties en uiteraard tekenobjecten.

---

## Stap 3 – Voeg een rechthoekige vorm toe

Met het document klaar, kunnen we een vorm toevoegen. Hier kiezen we een eenvoudige rechthoek, maar dezelfde logica werkt voor cirkels, lijnen of aangepaste polygonen.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Waarom een vorm?** In Aspose.Words kan een `Shape`‑object tekst, afbeeldingen of gewoon een decoratief element bevatten. Het toevoegen van een schaduw aan een vorm is veel eenvoudiger dan het manipuleren van een afbeeldingskader.

---

## Stap 4 – Configureer de schaduw (Schaduw toevoegen aan vorm)

Dit is het hart van de tutorial—**hoe je vormschaduw toevoegt** en het uiterlijk fijn afstemt. De eigenschap `ShadowFormat` geeft je volledige controle.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Wat elke eigenschap doet

| Eigenschap | Effect | Typische waarden |
|------------|--------|------------------|
| **Visible** | Schakelt de schaduw in/uit. | `true` / `false` |
| **Blur** | Verzacht de randen van de schaduw. | `0` (hard) tot `10` (zeer zacht) |
| **Distance** | Verplaatst de schaduw van de vorm af. | `1`–`5` punten is gebruikelijk |
| **Angle** | Bepaalt de richting van de offset. | `0`–`360` graden |
| **Transparency** | Maakt de schaduw gedeeltelijk doorschijnend. | `0` (ondoorzichtig) tot `1` (onzichtbaar) |

> **Randgeval:** Als je `Transparency` op `1` zet, verdwijnt de schaduw volledig—handig om deze programmatisch te toggelen.

---

## Stap 5 – Voeg de vorm toe aan het document

We koppelen de vorm nu aan de eerste alinea van de body van het document. Aspose maakt automatisch een alinea aan als er nog geen bestaat.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Als je document al inhoud bevat, kun je de vorm op elk knooppunt invoegen met `InsertAfter` of `InsertBefore`.

---

## Stap 6 – Sla het document op

Tot slot schrijven we het bestand naar schijf. Je kunt elk ondersteund formaat kiezen (`.docx`, `.pdf`, `.odt`, enz.), maar voor deze tutorial blijven we bij het native Word‑formaat.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Open het resulterende `ShadowedShape.docx` in Microsoft Word, en je ziet een rechthoek met een zachte, 45‑graden schaduw die 30 % transparant is—precies zoals we hebben geconfigureerd.

---

## Volledig werkend voorbeeld

Hieronder staat het **complete, copy‑and‑paste‑klare** programma dat alle bovenstaande stappen bevat. Sla het op als `Program.cs` en voer het uit met `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Verwachte output:** Een bestand genaamd `ShadowedShape.docx` met één rechthoek en een subtiele, half‑transparante slagschaduw onder een hoek van 45°.

---

## Variaties & Geavanceerde tips

### Schaduwkleur wijzigen

Standaard erft de schaduw de vulkleur van de vorm, maar je kunt een aangepaste kleur instellen:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Meerdere vormen met verschillende schaduwen

Als je meerdere vormen nodig hebt, herhaal dan simpelweg de creatie‑ en configuratiestappen. Vergeet niet elke vorm een unieke naam te geven als je later naar ze wilt verwijzen.

### Exporteren naar PDF met behouden schaduwen

Aspose.Words behoudt schaduweffecten bij het opslaan naar PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Veelvoorkomende valkuilen

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| Schaduw niet zichtbaar | `ShadowFormat.Visible` staat op `false` | Zet op `true`. |
| Schaduw ziet er te hard uit | `Blur` staat op `0` | Verhoog `Blur` naar 3–6. |
| Schaduw verdwijnt in PDF | Een oude Aspose.Words‑versie (< 22.9) wordt gebruikt | Upgrade naar de nieuwste bibliotheek. |

---

## Conclusie

We hebben behandeld **hoe je schaduw aan een vorm toevoegt** met Aspose.Words, van het initialiseren van een document tot het fijn afstemmen van vervaging, afstand, hoek en **schaduwtransparantie toepassen**. Het volledige voorbeeld toont een nette, productie‑klare aanpak die je kunt aanpassen aan elke vorm of documentlay-out.

Heb je vragen over **een Word‑document maken met Aspose** voor complexere scenario’s—zoals tabellen met schaduwen of dynamisch gegenereerde vormen? Laat een reactie achter of bekijk de gerelateerde tutorials over Aspose.Words‑afbeeldingsverwerking en alinea‑opmaak.

Veel programmeerplezier, en geniet van die extra visuele polish in je Word‑documenten! 

--- 

![schaduw aan vorm voorbeeld](shadowed_shape.png "schaduw aan vorm voorbeeld")

{{< layout-end >}}

{{< layout-end >}}