---
category: general
date: 2026-11-18
description: Leer hoe je een rechthoekvorm maakt in een Word‑document met C#. De gids
  behandelt ook het instellen van de vormgrootte, het instellen van de vormpositie
  en het groeperen van vormen in Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: nl
lastmod: 2026-11-18
og_description: Maak een rechthoekvorm in een Word‑bestand met C# en leer de afmetingen
  van de vorm in te stellen, de positie van de vorm te bepalen en vormen te groeperen
  in Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Maak een rechthoekvorm en groepeer vormen in Word met C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een rechthoekvorm te maken en vormen te groeperen in Word met C#
url: /nl/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een rechthoekvorm en groepeer vormen in Word met C#

Als je een **rechthoekvorm** in een Word‑document moet maken, toont deze tutorial een complete, kant‑klaar oplossing. Je ziet hoe je de vormgrootte instelt, de vormpositie instelt en vormen groepeert in Word zodat ze zich als één object gedragen.

Werken met vormen is een veelvoorkomende eis bij het programmatisch genereren van rapporten, facturen of diagrammen. Aan het einde van deze gids kun je een `.docx`‑bestand genereren dat een rechthoek, een ellips en een gegroepeerde container bevat — allemaal gemaakt met Aspose.Words for .NET.

## Vereisten

- .NET 6.0 SDK of later (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
- Een code‑editor of IDE (Visual Studio, VS Code, Rider, enz.)

Er zijn geen extra bibliotheken vereist.

## Hoe maak je een rechthoekvorm en groepeer je vormen in Word

De kernstappen zijn:

1. **Maak een leeg document** en een `DocumentBuilder`.
2. **Voeg een `GroupShape` toe** die de individuele vormen zal bevatten.
3. **Maak een rechthoekvorm**, stel de afmetingen in en voeg deze toe aan de groep.
4. **Maak een ellipsvorm**, stel de grootte en positie in, en voeg deze toe aan de groep.
5. **Sla** het document op.

Elke stap wordt hieronder uitgelegd, en de volledige broncode volgt de uitleg.

### Stap 1: Initialiseer het document en de builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` een vloeiende API biedt om inhoud in te voegen. Ze initialiseren is verplicht voordat je vormen kunt toevoegen.

### Stap 2: Voeg een groepsvorm toe

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

Een `GroupShape` werkt als een container; alle onderliggende vormen bewegen samen. Dit is de aanbevolen manier om **vormen te groeperen in Word** wanneer je collectieve transformaties nodig hebt (bijv. verplaatsen, roteren of verwijderen).

### Stap 3: Maak de rechthoek en stel de grootte in

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Hier **maken we een rechthoekvorm** en **stellen we de vormgrootte in** door `Width` en `Height` toe te wijzen. In Aspose.Words worden afmetingen uitgedrukt in punten (1 pt ≈ 1/72 in). Het expliciet instellen van de afmetingen zorgt ervoor dat de rechthoek precies verschijnt zoals bedoeld.

### Stap 4: Maak de ellips, stel de afmetingen in en positioneer deze

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

De **afmetingen van de vorm** voor de ellips zijn identiek voor breedte en hoogte, waardoor een perfecte cirkel ontstaat. De `Left`‑eigenschap toont **het instellen van de vormpositie**: de ellips begint 120 pt rechts van de oorsprong van de groep, zodat deze de rechthoek niet overlapt.

### Stap 5: Sla het document op

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Opslaan schrijft het Word‑bestand naar de schijf. Je kunt `GroupShape.docx` openen in Microsoft Word om te verifiëren dat de rechthoek en ellips correct zijn gegroepeerd en gepositioneerd.

## Vormafmetingen en -grootte instellen – dieper inzicht

- **Punten vs. inches**: 72 pt = 1 in. Als je inches verkiest, vermenigvuldig dan met 72 (bijv. `2.5 * 72` voor 2.5 in).
- **Automatische schaal**: Als je `Width` of `Height` weglaat, gebruikt de vorm de standaardgrootte. Stel expliciet **de vormgrootte in** om verrassingen in de lay‑out te voorkomen.
- **Aspectratio**: Voor vormen zoals `Ellipse` behoudt het gelijk houden van `Width` en `Height` een cirkelvormig uiterlijk.

## Een vorm positioneren in Word

De `Left`‑ en `Top`‑eigenschappen regelen de offset van de vorm binnen zijn container (de groep of de pagina). Positieve waarden verplaatsen de vorm naar rechts/naar beneden; negatieve waarden verschuiven deze naar links/naar boven. Bij groeperen zijn posities relatief ten opzichte van de oorsprong van de groep, wat lay‑outberekeningen vereenvoudigt.

## Vormen groeperen in Word met Aspose.Words

Groeperen is essentieel wanneer je meerdere vormen als één eenheid wilt laten functioneren. Het `GroupShape`‑object:

- Ondersteunt `AppendChild` om elke `Shape` toe te voegen (rechthoek, ellips, afbeelding, enz.).
- Staat je toe om de hele groep met één aanroep te verplaatsen, roteren of verwijderen.
- Behoudt de posities van onderliggende vormen relatief ten opzichte van de groep, waardoor complexe diagrammen makkelijker te beheren zijn.

**Pro tip:** Nadat je alle onderliggende vormen hebt toegevoegd, kun je de `Width`, `Height`, `Left` en `Top` van de groep aanpassen om de volledige collectie in één stap te verplaatsen.

## Volledig uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Het bevat alle `using`‑directieven, een `Main`‑methode en commentaren die elke regel uitleggen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Verwachte output:** Na het uitvoeren van het programma verschijnt `GroupShape.docx` in de uitvoermap. Het openen in Word toont een rechthoek (100 pt × 50 pt) links en een ellips (80 pt × 80 pt) 120 pt naar rechts gepositioneerd, beide binnen één gegroepeerd object.

![Word‑document met gegroepeerde rechthoek en ellips](grouped_shapes.png){: .center alt="Schermafbeelding van een Word‑document dat een gegroepeerde rechthoek‑ en ellipsvorm toont, gemaakt met C#" }

*De bovenstaande afbeelding illustreert het eindresultaat; de rechthoek en ellips zijn als één groep selecteerbaar.*

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik meer dan twee vormen toevoegen?** | Ja. Roep `group.AppendChild(yourShape)` aan voor elke extra vorm. |
| **Wat als ik de groep moet roteren?** | Gebruik `group.RotationAngle = 45;` (graden) nadat je alle kinderen hebt toegevoegd. |
| **Hoe wijzig ik de achtergrondkleur van de groep?** | Stel `group.FillColor = System.Drawing.Color.LightGray;` in. |
| **Werkt dit met .doc‑bestanden?** | Aspose.Words ondersteunt `.doc` en `.docx`. dezelfde code werkt; wijzig alleen de bestandsextensie in `Save`. |
| **Is er een geheugenimpact bij het groeperen van veel vormen?** | Groeperen voegt zelf minimale overhead toe. Het belangrijkste punt is het totale aantal vormen; houd dit redelijk voor grote documenten. |

## Conclusie

In deze tutorial heb je geleerd hoe je een **rechthoekvorm** maakt in een Word‑bestand met C#, hoe je **de vormgrootte instelt**, **de vormafmetingen instelt**, **de vormpositie instelt**, en uiteindelijk hoe je **vormen groepeert in Word** met Aspose.Words. Het volledige voorbeeld toont een schone, onderhoudbare aanpak die je kunt uitbreiden naar complexere diagrammen, grafieken of aangepaste afbeeldingen.

Vervolgens kun je verkennen:

- Tekst toevoegen binnen vormen (`Shape.TextPath.Text = "Hello"`).
- Afbeeldingen invoegen in een `GroupShape`.
- De gegroepeerde vormen exporteren naar PDF met `doc.Save("output.pdf")`.

Voel je vrij om te experimenteren met verschillende groottes, posities en extra vormtypen om aan de behoeften van je project te voldoen. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe maak je een rechthoekvorm en groepeer je vormen in Word met Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Groepvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}