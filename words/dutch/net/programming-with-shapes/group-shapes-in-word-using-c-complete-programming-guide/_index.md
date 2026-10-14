---
category: general
date: 2026-10-13
description: Vormen groeperen in Word met C# – leer hoe je vormen groepeert en vormen
  aan een groep toevoegt met Aspose.Words in een paar eenvoudige stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: nl
lastmod: 2026-10-13
og_description: Groep vormen in Word met C# en Aspose.Words. Volg deze gids om te
  leren hoe je vormen groepeert en vormen toevoegt aan een groep in een Word‑document.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Vormen groeperen in Word met C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Vormen groeperen in Word met C# – volledige programmeergids
url: /nl/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Groepeer vormen in Word met C# – volledige programmeergids

Als je **vormen in Word** programmatisch moet **groeperen**, laat deze gids je precies zien hoe. Na de eerste twee zinnen ken je de benodigde code, de reden achter elke stap, en hoe je **vormen aan een groep toevoegt** zonder verrassingen.

We behandelen alles, van het laden van een `.docx`‑bestand tot het opslaan van het bijgewerkte document. De tutorial gaat uit van basiskennis van C# en een referentie naar de Aspose.Words for .NET‑bibliotheek. Geen externe documentatie nodig—kopieer, plak en voer uit.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
- Een Word‑document (`input.docx`) dat al minstens twee vormen bevat (bijv. afbeeldingen, AutoShapes)

> **Pro tip:** Als je test, maak dan een eenvoudig Word‑bestand met twee rechthoeken via de Word‑UI. Sla het op als `input.docx` in een map die je beheert.

## Groepeer vormen in Word – stap‑voor‑stap gids

Hieronder splitsen we het proces in vijf logische stappen. Elke stap bevat de exacte C#‑code, een uitleg *waarom* de regel nodig is, en een korte opmerking over veelvoorkomende valkuilen.

### Stap 1: Laad het Word‑document

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Waarom:** `Document` is het toegangspunt voor elke Word‑manipulatie. Door het volledige bestandspad op te geven, wordt het document in het geheugen geladen, zodat we de node‑boom kunnen doorzoeken en wijzigen.

**Valkuil:** Het gebruik van een relatief pad kan mislukken wanneer de werkmap anders is. Gebruik een absoluut pad of `Path.Combine` met `AppContext.BaseDirectory`.

### Stap 2: Haal de vormen op die je wilt groeperen

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Waarom:** `GetChild` doorloopt de documentboom en retourneert de *n‑de* node van het gevraagde type. Door `isDeep` op `true` te zetten, wordt het hele document doorzocht, niet alleen de huidige sectie.

**Randgeval:** Als het document minder dan twee vormen bevat, zijn `firstShape` of `secondShape` `null` en wordt er een uitzondering gegooid wanneer we proberen te casten. Bescherm hiertegen:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Stap 3: Maak een nieuwe `GroupShape`‑container

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Waarom:** `GroupShape` fungeert als een bovenliggende node die meerdere `Shape`‑objecten kan bevatten. Het erft van `Shape`, zodat het overal kan worden ingevoegd waar een gewone vorm is toegestaan (bijv. in een alinea).

### Stap 4: Voeg de individuele vormen toe aan de groep

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Waarom:** `AppendChild` verplaatst de vormen van hun oorspronkelijke locatie naar de nieuwe groep. Na deze aanroep bestaan de oorspronkelijke vormen niet meer als zelfstandige nodes; ze worden onderdeel van `groupShape`.

**Tip:** Groeperen past automatisch de relatieve posities van de onderliggende vormen aan. Als je een specifieke lay‑out nodig hebt, stel dan de eigenschap `GroupShape.Bounds` *vóór* het toevoegen van kinderen in.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Stap 5: Plaats de groepsvorm in de document‑body

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Waarom:** Een `GroupShape` moet zich binnen een alinea (of een tabelcel) bevinden om te worden gerenderd. Door deze toe te voegen aan de eerste alinea garanderen we een zichtbare plaatsing zonder de bestaande lay‑out te verstoren.

### Stap 6: Sla het gewijzigde document op

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Waarom:** `Save` schrijft de in‑memory wijzigingen terug naar een `.docx`‑bestand. Je kunt ook naar een stream of naar PDF opslaan door de overload te wijzigen.

**Resultaatverificatie:** Open `output.docx` in Microsoft Word. Je zou nu de twee oorspronkelijke vormen moeten zien die zijn samengevoegd tot één gegroepeerd object. Het selecteren van de groep toont de standaard Word‑groeperingsgrepen.

## Hoe je vormen programmatically groepeert – dieper inzicht

- **Node‑eigendom:** Wanneer je `AppendChild` aanroept, verandert de referentie `ParentNode` van de vorm automatisch. Dit voorkomt “wees‑nodes” die het document kunnen beschadigen.
- **Opmaak behouden:** Groeperen verliest **geen** vormopmaak (vulkleur, lijntype, enz.). Alle onderliggende vormen behouden hun oorspronkelijke eigenschappen.
- **Geneste groepen:** `GroupShape` kan andere `GroupShape`‑objecten bevatten, waardoor hiërarchieën met meerdere niveaus mogelijk zijn. Behandel de interne groep gewoon als elke andere vorm.

## Voeg vormen toe aan de groep en beheer ze later

Als je later meer vormen wilt toevoegen nadat de eerste groep is aangemaakt, kun je dezelfde `GroupShape`‑instantie hergebruiken:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Wanneer je later moet degroeperen, loop dan `groupShape.GetChildNodes(NodeType.Shape, true)` af en voeg elk kind opnieuw in op de gewenste plaats.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Waarom dit belangrijk is:** Sommige workflows vereisen tijdelijke groepering (bijv. het uitlijnen van meerdere objecten) gevolgd door degroeperen voor verdere individuele bewerkingen.

## Volledig uitvoerbaar voorbeeld

Hieronder staat een zelfstandige applicatie die je kunt compileren en direct kunt uitvoeren. Vervang `YOUR_DIRECTORY` door een daadwerkelijk pad op jouw machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Verwachte output:** Wanneer je `output.docx` opent, verschijnen de twee oorspronkelijke vormen als één gegroepeerd object. Het selecteren van de groep toont de bekende Word‑groeperingsgrepen, zodat je de hele set tegelijk kunt verplaatsen, van grootte kunt veranderen of roteren.

## Conclusie

Je weet nu hoe je **vormen in Word** kunt groeperen met C# en Aspose.Words, en je hebt de exacte stappen gezien om **vormen aan een groep toe te voegen** en later te manipuleren of te degroeperen. Deze techniek is ideaal voor het automatiseren van rapportlay‑outs, het maken van samengestelde diagrammen, of het voorbereiden van Word‑templates die precieze positionering van meerdere objecten vereisen.

Ga vervolgens verder met gerelateerde onderwerpen zoals **hoe je vormen groepeert** met verschillende anker‑types, het toepassen van **geavanceerde opmaak** op gegroepeerde objecten, of het exporteren van het gegroepeerde resultaat naar PDF. Experimenteer met geneste groepen om complexe grafieken programmatisch te bouwen.

Happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Shadow Effect to Word Shapes – Complete C# Guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}