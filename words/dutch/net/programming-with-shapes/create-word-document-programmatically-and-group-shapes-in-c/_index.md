---
category: general
date: 2026-08-10
description: Maak een Word‑document programmatisch met Aspose.Words, leer hoe je meerdere
  vormen in Word groepeert, een rechthoek aan Word toevoegt en een groepsvorm maakt
  in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: nl
lastmod: 2026-08-10
og_description: Maak een Word‑document programmatisch met Aspose.Words. Deze gids
  laat zien hoe je meerdere vormen in Word groepeert, een rechthoek toevoegt aan Word
  en een platte‑tekst inhoudsbesturingselement insluit, allemaal in C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Maak een Word‑document programmatisch – groepeer vormen in C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Maak een Word‑document programmatisch en groepeer vormen in C#
url: /nl/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Een Word‑document programmatically maken en vormen groeperen in C#

Als je **een Word‑document programmatically wilt maken**, laat deze tutorial je zien hoe je een DOCX‑bestand bouwt met Aspose.Words en **meerdere vormen in Word groepeert**. We behandelen ook **een rechthoek toevoegen aan Word** en **hoe je een groepsvorm maakt** die zowel een rechthoek als een ellips bevat, plus een platte‑tekst StructuredDocumentTag voor gebruikersinvoer.

Je eindigt met een kant‑klaar Word‑bestand dat een gegroepeerde rechthoek‑ellips‑vorm bevat en een content‑control waar een gebruiker een naam kan typen. Handmatige bewerking in Word is niet meer nodig nadat de code is uitgevoerd.

## Wat je nodig hebt

- .NET 6.0 of later (het voorbeeld richt zich op .NET 6, maar elke recente .NET‑versie werkt)
- Een Aspose.Words for .NET‑licentie (de gratis trial werkt voor testen)
- Visual Studio 2022 of een andere C#‑IDE naar keuze
- Basiskennis van C#‑syntaxis

## Een Word‑document programmatically maken – algemeen werkproces

Het proces bestaat uit drie logische fasen:

1. **Initialiseer** een `Document` en een `DocumentBuilder` – de basis voor elk Word‑bestand dat je genereert.
2. **Bouw een groepsvorm** die een rechthoek en een ellips bevat – demonstreert **meerdere vormen in Word groeperen** en **hoe je een groepsvorm maakt**.
3. **Voeg een StructuredDocumentTag (SDT) toe** – een platte‑tekst content‑control waarmee eindgebruikers gegevens kunnen invullen, illustrerend **een rechthoek toevoegen aan Word** als onderdeel van de algehele documentlay-out.

Hieronder staat de volledige, uitvoerbare code, gevolgd door een stap‑voor‑stap‑uitleg.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Stap 1 – Initialiseert het document en de builder
Het `Document`‑object vertegenwoordigt het volledige DOCX‑bestand, terwijl `DocumentBuilder` een handige API biedt om inhoud toe te voegen. Het initialiseren hiervan is de eerste vereiste telkens wanneer je **een Word‑document programmatically maakt**.

> **Pro tip:** Als je van plan bent hetzelfde document meerdere keren te gebruiken, houd dan één `DocumentBuilder`‑instantie aan om onnodige objectcreatie te vermijden.

### Stap 2 – Maak een container voor de groepsvorm
Een `Shape` met `ShapeType.Group` fungeert als een canvas dat andere vormen kan bevatten. Het instellen van `Width` en `Height` definieert de omhullende doos voor de groep. Dit is de kern van **hoe je een groepsvorm maakt** in Aspose.Words.

> **Edge case:** Als de breedte van de groep kleiner is dan de gecombineerde breedte van de kinderen, worden de kinderen afgesneden. Zorg ervoor dat de groep groot genoeg is om elke kindvorm te bevatten.

### Stap 3 – Een rechthoek toevoegen aan Word
Een rechthoek wordt gecreëerd met `ShapeType.Rectangle`. De eigenschappen `Left` en `Top` positioneren deze ten opzichte van de oorsprong van de groep. Deze stap demonstreert **een rechthoek toevoegen aan Word** en laat zien hoe je de exacte plaatsing kunt regelen.

> **Veelgemaakte fout:** Het vergeten van `Left`/`Top` zorgt ervoor dat de rechthoek verschijnt op de standaard oorsprong van de groep (0,0), wat kan overlappen met andere kinderen.

### Stap 4 – Een ellips (cirkel) aan de groep toevoegen
Een ellips wordt op dezelfde manier toegevoegd als de rechthoek, maar met `ShapeType.Ellipse`. `Left = 210` verplaatst deze naar rechts van de rechthoek, waardoor een visueel onderscheidend paar vormen ontstaat binnen dezelfde groep.

> **Waarom een groep gebruiken?** Groeperen stelt je in staat om beide vormen later met één bewerking te verplaatsen, roteren of schalen, waarbij hun relatieve lay-out behouden blijft.

### Stap 5 – Voeg de voltooide groepsvorm in het document in
`builder.InsertNode(groupShape)` plaatst de hele groep op de huidige cursorpositie. Omdat de groep al zijn kinderen bevat, zijn er geen extra insert‑calls nodig voor de rechthoek of ellips.

### Stap 6 – Maak een platte‑tekst StructuredDocumentTag (SDT)
Een StructuredDocumentTag is een content‑control die eindgebruikers kunnen invullen wanneer het document in Word wordt geopend. Het instellen van `Title = "CustomerName"` geeft de control een betekenisvolle identifier, wat handig is voor latere gegevensextractie.

> **Waarom een platte‑tekst SDT?** Het beperkt invoer tot platte tekst, waardoor onbedoelde opmaak die downstream verwerking kan verstoren, wordt voorkomen.

### Stap 7 – Sla het document op
`doc.Save("GroupAndSDT.docx")` schrijft het bestand naar schijf. Het resulterende DOCX‑bestand bevat de gegroepeerde vormen en de SDT. Het openen van het bestand in Microsoft Word toont een rechthoek naast een cirkel, beide selecteerbaar als één object, gevolgd door een placeholder “Enter name here …”.

#### Verwachte output
- Een bestand genaamd **GroupAndSDT.docx** in de uitvoermap.
- In Word: een gegroepeerde vorm (rechthoek + ellips) die je als één eenheid kunt verplaatsen.
- Direct onder de groep een grijs‑gekleurde content‑control die de gebruiker vraagt een naam in te voeren.

## Aanvullende variaties en best practices

### Gebruik van verschillende vormtypen
Je kunt `ShapeType.Rectangle` of `ShapeType.Ellipse` vervangen door elk ander `ShapeType` (bijv. `ShapeType.Polygon`, `ShapeType.Line`). De groeperingslogica blijft identiek.

### Instellen van vulkleur en randen
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Het toevoegen van vul- en lijnstijlen verbetert de visuele onderscheidbaarheid, vooral wanneer het document wordt gedeeld met niet‑technische belanghebbenden.

### De hele groep roteren
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Het roteren van de groep is efficiënter dan elk kind afzonderlijk roteren.

### Exporteren naar PDF
Als je een PDF‑versie nodig hebt, roep je simpelweg aan:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Alle gegroepeerde vormen en de SDT (weergegeven als een tekstveld) verschijnen in de PDF.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Symptom | Cause | Fix |
|---------|-------|-----|

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}