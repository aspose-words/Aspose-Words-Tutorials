---
category: general
date: 2026-07-29
description: Maak een leeg Word‑document en leer hoe je een vorm kunt verbergen, een
  verborgen object kunt maken en een ellipsvorm kunt creëren met Aspose.Words in C#.
  Stap‑voor‑stap code inbegrepen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: nl
lastmod: 2026-07-29
og_description: Maak een leeg Word‑document en verberg de vorm onmiddellijk. Leer
  hoe je een verborgen object maakt en een ellipsvorm tekent met Aspose.Words in C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Maak een leeg Word‑document met een verborgen ellipsvorm – C#‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Maak een leeg Word‑document met een verborgen ellipsvorm – Volledige C#‑gids
url: /nl/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document met een verborgen ellipsvorm – Volledige C#‑gids

Heb je ooit een **leeg Word‑document** moeten maken en vervolgens een vorm erin moeten verbergen? Misschien genereer je een sjabloon waarbij bepaalde markeringen onzichtbaar moeten blijven tot een latere stap. In deze tutorial lopen we precies door **hoe je een vorm verbergt**, hoe je een **verborgen object maakt**, en zelfs hoe je een **ellipsvorm maakt** met Aspose.Words voor .NET. Aan het einde heb je een kant‑klaar C#‑fragment dat een DOCX‑bestand produceert met een onzichtbare ellips.

## Wat je zult leren

- Initialiseer een nieuw leeg Word‑document met Aspose.Words.  
- Maak een ellipsvorm, stel de afmetingen in en positioneer deze op de pagina.  
- Markeer de vorm als verborgen zodat deze nooit verschijnt op het scherm of bij afdrukken.  
- Sla het resultaat op schijf op en controleer dat het verborgen object echt onzichtbaar is.  

Er zijn geen externe bibliotheken nodig naast Aspose.Words, en de code werkt met versie 24.10 of nieuwer (de `Hidden`‑eigenschap werd geïntroduceerd in die release). Laten we beginnen.

![Diagram van een verborgen ellips in een leeg Word‑document](https://example.com/hidden-ellipse.png "Verborgen ellipsvorm ingevoegd in een leeg Word‑document")

## Maak een leeg Word‑document en voeg een verborgen ellipsvorm in

De eerste stap is het aanmaken van een gloednieuw document. Beschouw `Document` als een leeg canvas; `DocumentBuilder` is je penseel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Waarom beginnen met een leeg document?**  
> Een schone lei garandeert dat geen vooraf bestaande inhoud interfereert met de verborgen vorm die je gaat toevoegen. Het maakt het voorbeeld ook gemakkelijker om te kopiëren‑plakken in elk project.

## Hoe een vorm verbergen: de Hidden‑eigenschap instellen

Aspose.Words 24.10 introduceerde de `Hidden`‑vlag op `Shape`. Wanneer deze op `true` staat, behandelt Word de vorm als een opmerking—volledig onzichtbaar in de UI en bij afdrukken.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Pro tip:** Als je later de vorm programmatisch wilt onthullen, schakel dan eenvoudig `ellipseShape.Hidden = false;` in en sla het document opnieuw op.

## Verborgen object maken: de vorm in het document invoegen

Nu de ellips is voorbereid en verborgen, voegen we deze in op de huidige cursorpositie van de builder. De positie van de builder staat standaard op het begin van de eerste alinea, wat perfect is voor een leeg document.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **Wat als je de vorm op een specifieke pagina nodig hebt?**  
> Verplaats de builder eerst naar de gewenste pagina (`builder.MoveToDocumentEnd();` of `builder.MoveToPage(pageNumber);`) voordat je `InsertNode` aanroept.

## Sla het document met de verborgen vorm op

Tot slot schrijf je het bestand naar schijf. De output is een standaard DOCX die elke tekstverwerker kan openen—behalve dat de ellips onzichtbaar blijft.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Verwachte output:** Open `HiddenShape.docx` in Microsoft Word. Je zult geen grafische elementen zien, maar de bestandsgrootte zal iets groter zijn dan een echt leeg document omdat de verborgen ellips in de XML is opgeslagen.

## Verifieer de verborgen ellips programmatisch (optioneel)

Als je wilt dubbel‑controleren dat de vorm inderdaad verborgen is, kun je het opgeslagen bestand laden en de `Hidden`‑eigenschap van de vorm inspecteren:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Het uitvoeren van dit fragment print `True`, wat bevestigt dat het verborgen object de opslaan‑laden cyclus heeft overleefd.

## Randgevallen en veelgestelde vragen

### Wat als de doel‑Word‑versie geen verborgen vormen ondersteunt?

De `Hidden`‑vlag maakt deel uit van de Office Open XML‑specificatie en wordt gerespecteerd door Word 2007+ en LibreOffice. Oudere formaten (bijv. `.doc`) negeren de vlag, dus sla altijd op als `.docx` wanneer je betrouwbare verberging nodig hebt.

### Kan ik andere soorten objecten verbergen (afbeeldingen, tabellen)?

Ja. Elke node afgeleid van `Shape`—inclusief afbeeldingen, tekstvakken en zelfs SmartArt—heeft de `Hidden`‑eigenschap. Stel deze gewoon in op `true` vóór het invoegen.

### Heeft het verbergen van een vorm invloed op de documentprestaties?

Verwaarloosbaar. De vorm wordt opgeslagen als XML‑markup, en Word slaat het renderen van verborgen objecten over tijdens de lay-out. Als je veel verborgen objecten invoegt, groeit de bestandsgrootte, maar het renderen blijft snel.

### Hoe verschilt dit van het gebruik van een bladwijzer of opmerking als marker?

Bladwijzers zijn per ontwerp onzichtbaar, maar ze zijn bedoeld voor navigatie, niet als visuele placeholders. Opmerkingen verschijnen in de marge. Een verborgen vorm geeft je een visueel object (grootte, positie) dat je later kunt onthullen of manipuleren, wat handig is voor sjabloonscenario's.

## Volledig werkend voorbeeld

Hieronder staat het volledige, kant‑klaar te kopiëren‑en‑plakken programma. Het bevat alle using‑directives, het maken van de verborgen ellips, en een verificatiestap.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Het uitvoeren van het programma maakt `HiddenEllipse.docx` aan in de uitvoermap. Open het—je ziet een perfect normale lege pagina, maar de verborgen ellips leeft stilletjes binnenin.

## Samenvatting

We hebben behandeld hoe je een **leeg Word‑document maakt**, een **vorm verbergt**, een **verborgen object maakt**, en een **ellipsvorm maakt**, allemaal met een handvol C#‑regels. Het belangrijkste inzicht is de `Hidden`‑eigenschap op `Shape`, die elk visueel element verandert in een onzichtbare marker zonder de Word‑compatibiliteit te breken.

## Wat is het volgende?

- **Stijl de verborgen vorm** (vulkleur, lijnstijl) zodat wanneer je deze later onthult, hij er precies uitziet zoals bedoeld.  
- **Combineer verborgen vormen met bladwijzers** om dynamische sjablonen te bouwen die aan‑ of uitgeschakeld kunnen worden.  
- **Verken andere vormtypen**—rechthoeken, pijlen, of zelfs aangepaste SVG‑paden—door `ShapeType.Ellipse` te vervangen.  

Voel je vrij om te experimenteren: wijzig de grootte, verplaats de positie, of voeg meerdere verborgen ellipsen toe. Hetzelfde patroon werkt voor elke Aspose.Words‑vorm die je uit het zicht wilt houden.

Als je een probleem tegenkomt of ideeën hebt om dit patroon uit te breiden, laat dan een reactie achter. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een leeg Word‑document met een schaduwrand‑rechthoekvorm – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Maak een groepsvorm in een Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Maak een rechthoekvorm in Word met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}