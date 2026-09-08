---
category: general
date: 2026-09-08
description: Maak een rechthoekvorm in een Word‑document met C#. Leer de vormgrootte
  instellen, meerdere vormen groeperen en een leeg Word‑document via code maken.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: nl
lastmod: 2026-09-08
og_description: Maak een rechthoekvorm in een Word‑document met C#. Deze gids laat
  zien hoe je de grootte van de vorm instelt, meerdere vormen groepeert en een leeg
  Word‑document via code maakt.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Maak een rechthoekvorm en groepeer vormen in Word met C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Maak een rechthoekvorm en groepeer vormen in Word met C#
url: /nl/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak rechthoekvorm en groepeer vormen in Word met C#

Als je een **rechthoekvorm** in een Word‑bestand moet **maken**, biedt deze tutorial een complete, kant‑klaar oplossing. Je ziet hoe je de vormgrootte instelt, meerdere vormen groepeert en een leeg Word‑document vanaf nul maakt — alles met de Aspose.Words for .NET‑bibliotheek.

Programma's die Word‑documenten bewerken voelen vaak als jongleren met veel kleine details. Aan het einde van deze gids heb je één methode die een `.docx`‑bestand oplevert met een rechthoek en een ellips die samen zijn gegroepeerd, klaar voor verdere bewerking of afdrukken.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 of hoger (de code werkt ook met .NET Framework 4.6+)
* Een gelicentieerde kopie van **Aspose.Words for .NET** (je kunt een gratis evaluatiesleutel gebruiken)
* Een IDE zoals Visual Studio 2022 of Visual Studio Code
* Basiskennis van C#‑syntaxis

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Stap 1: Maak een leeg Word‑document

De eerste stap is het aanmaken van een leeg document dat de vormen zal bevatten. Hiermee voldoe je aan de *maak leeg Word‑document*‑vereiste.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Het maken van een leeg document geeft je een schoon canvas. Het `Document`‑object vertegenwoordigt het volledige `.docx`‑bestand, en `FirstSection.Body.FirstParagraph` is het standaard invoerpunt voor nieuwe knooppunten.

## Stap 2: Maak een rechthoekvorm

Nu kun je de rechthoek toevoegen. Hier gebeurt de **maak rechthoekvorm**‑bewerking.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Het direct instellen van de afmetingen beantwoordt het trefwoord **set shape size**. Alle afmetingen worden uitgedrukt in points, wat precieze controle biedt over hoe de vorm er in het uiteindelijke document uitziet.

## Stap 3: Maak een extra vorm (ellips)

Een typisch gebruiksscenario is het combineren van meerdere vormen. Hier voegen we een ellips toe die later dezelfde container zal delen.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Beide vormen zijn op dit moment nog onafhankelijk. De volgende stap laat zien hoe je **multiple shapes** kunt **groeperen**.

## Stap 4: Groepeer vormen in Word

Vormen groeperen stelt je in staat ze te verplaatsen, schalen of opmaken als één geheel. Hiermee voldoe je aan de vereisten **group shapes in word** en **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

De eigenschap `GroupShape.Bounds` bepaalt het coördinatensysteem voor de onderliggende vormen. Door de rechthoek en ellips in dezelfde `GroupShape` te plaatsen, kun je ze later samen verplaatsen of roteren met één enkele aanroep.

## Stap 5: Sla het document op

Tot slot schrijf je het document naar schijf. Het bestand bevat de gegroepeerde vormen die je zojuist hebt aangemaakt.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Na het uitvoeren van het programma, open je `GroupedShapes.docx` in Microsoft Word. Je zou een rechthoek en een ellips moeten zien die gegroepeerd zijn; het selecteren van één vorm selecteert ook de andere, wat bevestigt dat de groepering geslaagd is.

## Volledige broncode

Kopieer het volgende volledige programma naar een nieuw console‑app‑project en voer het uit. Er is geen extra code nodig.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Verwachte output

Het uitvoeren van het programma levert `GroupedShapes.docx` op. Het openen van het bestand in Word toont:

* Een **rechthoek** (100 pt × 50 pt) met een blauwe rand en lichtgrijze vulling.
* Een **ellips** (80 pt × 80 pt) met een donkergroene rand en lichtgele vulling.
* Beide vormen bevinden zich in één groep, dus het verplaatsen van de ene verplaatst de andere.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik meer dan twee vormen aan de groep toevoegen?** | Ja. Maak extra `Shape`‑objecten aan en roep `group.AppendChild(yourShape)` voor elk aan. |
| **Wat als ik de groep moet roteren?** | Stel `group.RotationAngle = 45;` in (graden). Alle onderliggende vormen roteren samen. |
| **Is het mogelijk om vormen te groeperen nadat het document is opgeslagen?** | Je moet de documentstructuur wijzigen vóór het opslaan; anders moet je het bestand laden, de vormen lokaliseren en de groep opnieuw aanmaken. |
| **Moet ik objecten handmatig vrijgeven?** | Aspose.Words beheert zijn eigen resources, maar je moet `FileStream`‑objecten sluiten als je streams handmatig opent. |
| **Werkt de code met het .doc (binair) formaat?** | Ja, wijzig `doc.Save("output.doc")`. Het groeperingsgedrag is identiek. |

## Conclusie

Je weet nu hoe je **rechthoekvorm** kunt **maken**, **vormgrootte** kunt **instellen** en **meerdere vormen** kunt **groeperen** in een Word‑bestand met C#. Deze aanpak stelt je in staat om programmatisch complexe diagrammen, watermerken of sjabloongebaseerde rapporten te bouwen zonder handmatige bewerking.

### Volgende stappen

* Verken **group shapes in word** verder door tekstvakken of afbeeldingen aan dezelfde groep toe te voegen.
* Gebruik het `SetShapeSize`‑patroon om dynamisch afmetingen te berekenen op basis van de paginalay-out.
* Combineer deze techniek met mail‑merge‑velden om gepersonaliseerde documenten op grote schaal te genereren.

Voel je vrij om te experimenteren met verschillende vormtypen, kleuren en groeps‑transformaties. Veel programmeerplezier!

## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Maak een groepsvorm in een Word‑document met Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Maak een leeg Word‑document met een schaduwrijke rechthoekvorm – Stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Maak een Word‑document met een schaduwrijke rechthoek – Stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}