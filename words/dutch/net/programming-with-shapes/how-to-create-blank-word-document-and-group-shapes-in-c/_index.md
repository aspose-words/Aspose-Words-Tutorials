---
category: general
date: 2026-10-07
description: Maak een leeg Word‑document in C# en leer een rechthoekvorm toe te voegen,
  een afbeeldingvorm in te voegen en meerdere vormen te groeperen voor dynamische
  rapporten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: nl
lastmod: 2026-10-07
og_description: Maak een leeg Word‑document in C# met Aspose.Words. Leer hoe je een
  rechthoekvorm toevoegt, een afbeeldingsvorm invoegt en meerdere vormen groepeert
  voor professionele documenten.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Maak een leeg Word‑document en groepeer vormen in C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe maak je een leeg Word‑document en groepeer je vormen in C#
url: /nl/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg Word‑document te maken en vormen te groeperen in C#

Als je **een leeg Word‑document** programmatically wilt **maken**, laat deze gids je precies zien hoe. Je ziet hoe je een **rechthoekvorm toevoegt**, een **afbeeldingsvorm invoegt**, en **meerdere vormen groepeert** zodat ze zich als één object gedragen wanneer je later een **afbeelding toevoegt aan Word**.

Werken met Word‑bestanden vanuit code kan intimiderend aanvoelen, maar Aspose.Words maakt het proces eenvoudig. Aan het einde van deze tutorial heb je een herbruikbare C#‑snippet die een schoon, leeg Word‑bestand genereert met een gegroepeerde rechthoek en een logo. Je kunt het resultaat in facturen, rapporten of elke geautomatiseerde document‑workflow opnemen.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 of hoger (de code werkt ook met .NET Framework 4.7+).  
* Een geldige Aspose.Words for .NET‑licentie of een gratis evaluatiesleutel.  
* Een afbeeldingsbestand (bijv. `logo.png`) geplaatst in een map die je vanuit code kunt refereren.  
* Visual Studio 2022 of een andere C#‑compatibele IDE.

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Hoe een leeg Word‑document te maken met Aspose.Words

De eerste stap is altijd om **een leeg Word‑document** te **maken**. Dit object zal alle volgende vormen hosten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` vertegenwoordigt het volledige `.docx`‑bestand. Op dit moment is het bestand leeg, wat voldoet aan de *maak een leeg Word‑document*‑vereiste.

## Een container maken om meerdere vormen te groeperen

Vormen groeperen stelt je in staat ze samen te verplaatsen, roteren of van grootte te veranderen. Aspose.Words biedt de `GroupShape`‑klasse hiervoor.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

De `Bounds`‑rechthoek bepaalt waar de groep op de pagina verschijnt. Door de groep in de eerste alinea te plaatsen, garandeer je dat het **leeg Word‑document** onmiddellijk een visuele container bevat.

## Hoe een rechthoekvorm toe te voegen binnen de groep

Een veelvoorkomende eis is om een **rechthoekvorm toe te voegen** als achtergrond of rand. De volgende code maakt een rechthoek en voegt deze toe aan de eerder gedefinieerde groep.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Omdat de rechthoek zich binnen de `GroupShape` bevindt, beweegt hij mee met alle andere vormen die later worden toegevoegd. Dit is de kern van de **meerdere vormen groeperen**‑functionaliteit.

## Hoe een afbeeldingsvorm toe te voegen binnen de groep

Vervolgens **voeg je een afbeeldingsvorm toe** (het logo) en plaats je deze naast de rechthoek. Dit demonstreert de **afbeelding toevoegen aan Word**‑workflow.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

De `SetImage`‑methode leest het bestand en embedt het direct in het Word‑document, waardoor de afbeelding behouden blijft zelfs als het bronbestand wordt verplaatst. Hiermee is de stap **afbeeldingsvorm invoegen** voltooid en is de **afbeelding toevoegen aan Word**‑vereiste vervuld.

## Het document opslaan

Tot slot sla je het bestand op schijf op. Het opgeslagen bestand bevat het lege document, de gegroepeerde rechthoek en het ingesloten logo.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Wanneer je `GroupShape.docx` opent in Microsoft Word, zie je één groep met een lichtgrijze rechthoek en het logo naast elkaar. Door een deel van de groep te selecteren kun je de hele collectie verplaatsen of van grootte veranderen, wat bewijst dat de vormen inderdaad **meerdere vormen groeperen**.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Vervang `YOUR_DIRECTORY` door een absoluut of relatief pad dat op jouw machine bestaat.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Verwachte output

* Een bestand genaamd `GroupShape.docx` in `YOUR_DIRECTORY`.  
* Het openen van het bestand in Word toont één visuele groep met een grijze rechthoek links en `logo.png` rechts.  
* Het selecteren van een deel van de visuele groep stelt je in staat de hele collectie te verplaatsen of van grootte te veranderen, waarmee wordt bevestigd dat de vormen correct **meerdere vormen groeperen**.

## Veelgestelde vragen en edge‑case handling

| Vraag | Antwoord |
|---|---|
| **Kan ik meer dan twee vormen aan dezelfde groep toevoegen?** | Ja. Roep `group.AppendChild(yourShape)` aan voor elke extra `Shape`. De groep kan een willekeurig aantal tekenobjecten bevatten. |
| **Wat gebeurt er als het afbeeldingsbestand ontbreekt?** | `SetImage` zal een `FileNotFoundException` gooien. Plaats de aanroep in een try‑catch‑blok en bied een fallback (bijv. een placeholder‑vorm). |
| **Moet ik `WrapType` voor de vormen instellen?** | Standaard zijn vormen inline. Als je zwevend gedrag nodig hebt, stel `picture.WrapType = WrapType.Inline;` of een andere wrap‑modus in voordat je de vorm aan de groep toevoegt. |
| **Hoe beïnvloedt de documentgrootte de grenzen van de groep?** | De `Bounds`‑rechthoek wordt gedefinieerd in punten (1 pt ≈ 1/72 in). Pas de grootte aan als je de groep op een andere paginalay‑out plaatst (bijv. A4 versus Letter). |
| **Kan ik dezelfde groep in een ander document hergebruiken?** | Ja. Clone de groep met `GroupShape cloned = (GroupShape)group.Clone(true);` en voeg deze in een ander `Document` in. |

## Pro‑tips

* **Herbruik de `DocumentBuilder`** voor het toevoegen van tekst vóór of na de groep. Hij houdt automatisch rekening met de huidige cursorpositie.  
* **Stel `Shape.StrokeColor` in** als je een zichtbare rand rondom de rechthoek nodig hebt.  
* **Gebruik high‑resolution PNG‑bestanden** voor het logo om pixelatie te voorkomen wanneer  

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}