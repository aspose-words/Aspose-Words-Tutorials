---
category: general
date: 2026-07-19
description: Groep vormen in Word met Aspose.Words. Leer hoe je een rechthoekvorm
  toevoegt, een ellipsvorm definieert en een vorm in Word‑documenten invoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: nl
lastmod: 2026-07-19
og_description: Groep vormen in Word met Aspose.Words. Beheers het toevoegen van een
  rechthoekvorm, het definiëren van een ellipsvorm en het invoegen van een vorm in
  Word‑documenten.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Vormen groeperen in Word – Stapsgewijze C#‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Groepsvormen in Word met Aspose.Words – Complete C#‑gids
url: /nl/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Groepeer vormen in Word – Complete C#‑gids

Heb je je ooit afgevraagd hoe je **vormen in Word kunt groeperen** zonder met de UI te knoeien? Je bent niet de enige. Of je nu contracten, flyers of diagrammen programmatically genereert, het kunnen **toevoegen van een rechthoekige vorm**, **definiëren van een ellipsvorm**, en vervolgens **vormen in Word groeperen** kan je uren handmatig werk besparen.

In deze tutorial lopen we een praktijkvoorbeeld door met **Aspose.Words for .NET**. Aan het einde weet je precies hoe je **een vorm in Word invoegt**, ze combineert en een gepolijst document produceert dat je naar klanten of teamleden kunt sturen.

---

## Wat je nodig hebt

Voordat we beginnen, zorg dat je het volgende hebt:

- **Aspose.Words for .NET** (nieuwste versie, bv. 24.9). Je kunt het ophalen via NuGet met `Install-Package Aspose.Words`.
- Een .NET‑ontwikkelomgeving (Visual Studio 2022 of VS Code met de C#‑extensie werkt prima).
- Basiskennis van C#‑syntaxis – niets bijzonders, alleen de gebruikelijke `using`‑statements en objectcreatie.

Dat is alles. Geen extra libraries, geen COM‑interop, alleen pure managed code.

---

## Hoe vormen in Word te groeperen met Aspose.Words

Hieronder vind je een stap‑voor‑stap‑overzicht dat overeenkomt met de code die je al hebt. Elke stap legt **waarom** we iets doen uit, niet alleen **wat** de regel doet, zodat je het patroon kunt aanpassen aan elke gewenste vorm.

### Stap 1: Document en Builder instellen

We beginnen met het aanmaken van een lege `Document` en een `DocumentBuilder`. De builder is ons “pen” waarmee we inhoud kunnen invoegen waar we maar willen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Waarom?** Het `Document`‑object vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` een handige API biedt om knooppunten (zoals vormen) in te voegen zonder je bezig te houden met de onderliggende knooppuntboom.

### Stap 2: Rechthoekige vorm toevoegen (add rectangle shape)

Nu **voegen we een rechthoekige vorm toe** aan het document. We stellen de grootte, positie en vulkleur in zodat deze opvalt.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** Je kunt `FillColor` wijzigen naar elke `System.Drawing.Color` die je wilt. Handig wanneer je kleur‑gecodeerde secties in een rapport nodig hebt.

### Stap 3: Ellipsvorm definiëren (define ellipse shape)

Vervolgens **definiëren we een ellipsvorm**. Let op het andere `ShapeType` en de offset (`Left = 120`) zodat de ellips naast de rechthoek staat.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Waarom dit belangrijk is:** Door vormen expliciet te positioneren, bepaal je hoe ze eruitzien voordat je ze groepeert. Als je vertrouwt op automatische lay‑out, kan de groepering scheef lijken.

### Stap 4: (Optioneel) Individuele vormen invoegen voor preview

Als je elke vorm wilt zien voordat je ze groepeert, kun je **vorm in Word invoegen** afzonderlijk. Deze stap is optioneel maar handig voor debugging.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Commentarieer deze twee regels uit zodra je zeker weet dat de vormen er goed uitzien; anders krijg je dubbele visuals na het groeperen.

### Stap 5: Hoe vormen groeperen – Een GroupShape maken

Hier is de kern van de tutorial: **hoe vormen te groeperen**. We maken een `GroupShape`, voegen onze rechthoek en ellips toe, en bepalen hoe de groep zich gedraagt ten opzichte van omliggende tekst.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Uitleg:** `GroupShape` is in wezen een mini‑canvas dat andere vormen bevat. Door `WrapType` op `Inline` te zetten, beweegt de hele groep als één eenheid wanneer je tekst toevoegt of verwijdert.

### Stap 6: De gegroepeerde vorm invoegen in het document (insert shape into word)

Nu **voegen we een vorm in Word in** – maar dit keer is het de gegroepeerde container, niet de individuele onderdelen.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Wat gebeurt er onder de motorkap?** De `InsertNode`‑aanroep voegt de `GroupShape` toe aan de node‑collectie van het document. Omdat de groep al de rechthoek en ellips bevat, verschijnen ze samen als één object.

### Stap 7: Document opslaan

Tot slot schrijven we het bestand naar schijf. Je kunt het pad aanpassen aan je projectstructuur.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Resultaat:** Open `GroupShape.docx` in Microsoft Word en je ziet een lichtblauwe rechthoek en een koraalroze ellips die aan elkaar vastzitten. Het slepen van één verplaatst de ander – precies wat “group shapes in word” belooft.

---

## Visuele bevestiging

Hieronder staat een mock‑up van hoe de gegroepeerde vormen eruitzien in het Word‑bestand.  

![Screenshot of grouped shapes in a Word document created with Aspose.Words](grouped_shapes_placeholder.png "group shapes in word")

*De alt‑tekst van de afbeelding bevat het primaire zoekwoord voor toegankelijkheid en SEO.*

---

## Veelgestelde vragen & randgevallen

### Wat als ik meer dan twee vormen nodig heb?

Blijf gewoon `groupShape.AppendChild(jouwNieuweVorm);` aanroepen voordat je de groep invoegt. De API stelt geen limiet aan het aantal kind‑vormen.

### Kan ik de hele groep roteren of van grootte veranderen?

Absoluut. `GroupShape` erft van `Shape`, dus je kunt eigenschappen zoals `RotationAngle`, `Width` of `Height` op de groep zelf instellen, en alle kind‑vormen volgen mee.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Hoe wijzig ik de achtergrondkleur van de groep?

Gebruik `groupShape.FillColor`. Dit vult het onzichtbare begrenzingsvak; handig voor markeringen.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Werkt dit ook met oudere Word‑formaten (.doc)?

`Aspose.Words` kan ook naar `.doc` opslaan – vervang simpelweg de bestandsextensie in `Save`. Echter, sommige geavanceerde vorm‑features (zoals groeperen) worden volledig ondersteund alleen in het OOXML‑`.docx`‑formaat.

---

## Volledig werkend voorbeeld

Kopieer‑plak het onderstaande blok in een nieuwe console‑app om het volledige proces in actie te zien. Er ontbreken geen onderdelen; dit is een **volledig, uitvoerbaar voorbeeld**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Verwachte output:** Wanneer je `GroupShape.docx` opent, zie je één gegroepeerd object bestaande uit een lichtblauwe rechthoek en een lichtkoraalroze ellips, perfect naast elkaar uitgelijnd.

---

## Samenvatting

We hebben zojuist alles behandeld wat je nodig hebt om **vormen in Word te groeperen** met Aspose.Words:

1. Maak een document en builder aan.  
2. **Voeg een rechthoekige vorm toe** en **definieer een ellipsvorm** met expliciete afmetingen.  
3. (Optioneel) **voeg een vorm in Word in** voor een snelle preview.  
4. Gebruik `GroupShape` om **hoe vormen te groeperen** – voeg elk kind toe, stel wrapping in, en voeg de groep in.  
5. Sla het bestand op en controleer het

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑features onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}