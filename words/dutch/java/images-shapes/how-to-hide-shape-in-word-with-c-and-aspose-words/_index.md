---
category: general
date: 2026-09-11
description: Leer hoe je een vorm in Word kunt verbergen met C#. Deze gids laat ook
  zien hoe je een rechthoekvorm invoegt en een vorm in een Word‑document plaatst met
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: nl
lastmod: 2026-09-11
og_description: Hoe een vorm in Word te verbergen met C# en Aspose.Words. Volg de
  stapsgewijze tutorial om een rechthoekvorm in te voegen en vormen in een Word‑document
  te beheren.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Hoe verberg je een vorm in Word – volledige C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een vorm te verbergen in Word met C# en Aspose.Words
url: /nl/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een vorm verbergen in Word met C# en Aspose.Words

Als u een vorm in Word moet verbergen terwijl u de vorm in de documentstructuur behoudt, laat deze tutorial u precies zien hoe. Met Aspose.Words voor .NET kunt u een rechthoekige vorm invoegen, deze verbergen en toch de positie behouden voor latere verwerking.

Word-automatisering vereist vaak fijnmazige controle over vormen—of u nu sjablonen genereert, rapporten voorbereidt of een documentbewerkingsservice bouwt. Aan het einde van deze gids kunt u:

* Een rechthoekige vorm invoegen in een Word-document (`insert rectangle shape`).
* Elke vorm verbergen zonder deze te verwijderen (`how to hide shape in word`).
* Het resultaat opslaan en verifiëren dat de verborgen vorm niet verschijnt in de weergegeven weergave (`insert shape into word document`).

Het voorbeeld werkt met Aspose.Words 24.10 of later en richt zich op .NET 6.0+, maar de concepten zijn ook toepasbaar op eerdere versies.

## Vereisten

* **Aspose.Words for .NET** ≥ 24.10. U kunt een gratis tijdelijke licentie verkrijgen op de Aspose-website.
* **.NET SDK** 6.0 of nieuwer geïnstalleerd op uw machine.
* Een ontwikkelomgeving zoals Visual Studio 2022, VS Code of Rider.
* Basiskennis van C# en het Word Open XML-concept (optioneel maar nuttig).

## Hoe een vorm verbergen in Word met Aspose.Words

Hieronder staat een compleet, uitvoerbaar programma dat de volledige workflow demonstreert—van het maken van een document tot het invoegen van een rechthoekige vorm en uiteindelijk het verbergen ervan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Uitleg van elke stap

1. **Maak een nieuw document** – `Document` vertegenwoordigt het Word‑bestand in het geheugen. `DocumentBuilder` biedt een vloeiende API voor het invoegen van inhoud.
2. **Voeg een rechthoekige vorm in** – `InsertShape` maakt een tekenobject van het type `Rectangle`. De afmetingen worden uitgedrukt in punten (1 pt ≈ 1/72 in). Dit voldoet aan de `insert rectangle shape`‑vereiste.
3. **Verberg de vorm** – Door `Shape.Hidden = true` in te stellen, wordt de vorm gemarkeerd als verborgen in de Word‑markup (`<w:hidden/>`). De vorm blijft deel uitmaken van de documentboom, zodat u deze later kunt weer zichtbaar maken of programmatisch kunt refereren. Dit is de kern van `how to hide shape in word`.
4. **Sla het bestand op** – Het document wordt weggeschreven naar `output.docx`. Wanneer het wordt geopend in Microsoft Word, zal de rechthoek niet zichtbaar zijn, maar hij bestaat nog steeds in de XML en kan worden geïnspecteerd met een ZIP‑viewer of de Open XML SDK.

### Verwacht resultaat

Open `output.docx` in Microsoft Word:

* Het document lijkt leeg—geen zichtbare vorm.
* Als u de onderliggende XML inspecteert (`word/document.xml`) vindt u een `<w:pict>`‑element met een `<w:hidden/>`‑attribuut, wat bevestigt dat de vorm aanwezig maar verborgen is.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

De verborgen vorm kan weer zichtbaar worden gemaakt door `Hidden = false` in te stellen en het document opnieuw op te slaan.

## Rechthoekige vorm invoegen in een Word-document

Hoewel het primaire doel is om een vorm te verbergen, beginnen veel scenario's eerst met het invoegen van een vorm. De `InsertShape`‑methode ondersteunt vele `ShapeType`‑waarden, waaronder `Rectangle`, `Ellipse`, `Line` en aangepaste afbeeldingen.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Waarom een rechthoek gebruiken?**  
Een rechthoek biedt een nette, as‑gealigneerde container die tekst, afbeeldingen of andere geneste vormen kan bevatten. Het wordt vaak gebruikt als tijdelijke aanduiding voor dynamische inhoud zoals tabellen of grafieken. Door de rechthoek eerst in te voegen, behoudt u de lay-outconsistentie, zelfs nadat u deze later verbergt.

## Vorm invoegen in Word-document – best practices

Wanneer u `insert shape into word document` uitvoert, overweeg dan het volgende:

* **Stel expliciete afmetingen in** – Vermijd afhankelijkheid van automatische grootte; specificeer breedte en hoogte in punten om een consistente lay-out over platforms te garanderen.
* **Definieer positionering** – Standaard wordt de vorm verankerd aan de huidige alinea. Gebruik `builder.MoveTo` of `builder.StartBookmark` om deze nauwkeurig te plaatsen.
* **Pas styling vroeg toe** – Opvulkleur, lijntype en tekstomloop beïnvloeden het uiteindelijke uiterlijk. Zelfs verborgen vormen profiteren van juiste styling omdat de markup ongewijzigd blijft.
* **Versie‑compatibiliteit** – De `Hidden`‑eigenschap is alleen beschikbaar vanaf Aspose.Words 24.10. Als u een oudere versie target, kunt u handmatig het `<w:hidden/>`‑attribuut toevoegen via de `Node`‑API.

### Handmatig het verborgen attribuut toevoegen (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Volledig end‑to‑end voorbeeld

Door alles samen te voegen, is hier een enkel programma dat:

1. Een rechthoekige vorm invoegt.
2. De vorm verbergt.
3. Een zichtbare ellips invoegt voor contrast.
4. Het document opslaat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Het uitvoeren van het programma genereert `demo_output.docx`. Wanneer geopend, ziet u alleen de koraal‑ellips; de groene rechthoek is aanwezig in de XML maar verborgen in de weergave.

## Veelgestelde vragen en randgevallen

**V: Heeft het verbergen van een vorm invloed op paginering?**  
A: Nee. Verborgen vormen worden genegeerd door de lay‑out engine, zodat ze geen ruimte innemen. Dit is nuttig voor tijdelijke inhoud die geen paginering mag beïnvloeden.

**V: Kan ik een vorm verbergen die deel uitmaakt van een kop‑ of voettekst?**  
A: Ja. Dezelfde `Hidden`‑eigenschap werkt op vormen die zich overal in de documentboom bevinden, inclusief kop‑ en voetteksten, en zelfs binnen tabellen.

**V: Wat als ik meerdere vormen tegelijk moet verbergen?**  
A: Iterate over de `Document.GetChildNodes(NodeType.Shape, true)`‑collectie en stel `Hidden = true` in voor elke doelvorm.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**V: Wordt het verborgen attribuut behouden bij conversie naar PDF?**  
A: Bij conversie naar PDF worden verborgen vormen standaard weggelaten, wat overeenkomt met het weergavegedrag van Word. Als u ze in de PDF nodig heeft, moet u ze vóór de conversie weer zichtbaar maken.

## Tips en valkuilen

- **Pro tip:** Stel `shape.WrapType = WrapType.None` in vóór het verbergen als u later van plan bent de vorm weer zichtbaar te maken zonder de omliggende tekst te verstoren.
- **Let op oudere Aspose.Words‑versies:** De `Hidden`‑eigenschap geeft een `NotSupportedException` vóór 24.10. Gebruik in dat geval de handmatige XML‑aanpak.
- **Testen:** Open altijd de gegenereerde `.docx` in Word en gebruik “Show XML markup” (tabblad Ontwikkelaar) om te verifiëren dat het `<w:hidden/>`‑attribuut aanwezig is.

## Conclusie

U weet nu hoe u een vorm in Word kunt verbergen met C# en Aspose.Words, evenals hoe u een rechthoekige vorm kunt invoegen en een vorm in een Word-document kunt invoegen met volledige controle over de zichtbaarheid. Door gebruik te maken van de `Hidden`‑eigenschap kunt u vormen in het documentmodel behouden voor latere verwerking, terwijl u een schone weergave aan eindgebruikers presenteert.

Vervolgens kunt u gerelateerde onderwerpen verkennen, zoals **updating shape properties at runtime**, **converting hidden shapes to images**, of **using the Open XML SDK to manipulate hidden elements directly**. Deze uitbreidingen zullen uw kennis verdiepen

## Wat moet u hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om u te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}