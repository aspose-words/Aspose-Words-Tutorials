---
category: general
date: 2026-08-23
description: Leer hoe je vormen groepeert in C# met Aspose.Words. De gids behandelt
  ook hoe je een rechthoekvorm invoegt en vormen toevoegt aan Word voor complexe documenten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: nl
lastmod: 2026-08-23
og_description: Hoe vormen te groeperen in C# met Aspose.Words. Volg deze volledige
  tutorial om een rechthoekvorm in te voegen, vormen toe te voegen aan Word, en meerdere
  vormen efficiënt te groeperen.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Hoe vormen te groeperen in C# – stap‑voor‑stap gids
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Hoe vormen groeperen in C# met Aspose.Words
url: /nl/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in C# met Aspose.Words

Als je **how to group shapes** in een Word‑document programmatically moet doen, laat deze tutorial je de exacte stappen zien met Aspose.Words voor .NET. Of je nu een rapportgenerator, een sjabloonengine of een diagramtool bouwt, je leert hoe je een groep start, een rechthoekvorm invoegt en add shapes word‑level content toevoegt zonder je code te verlaten.

Je ziet ook hoe je **group multiple shapes** samen kunt groeperen, wat essentieel is wanneer je een verzameling objecten wilt verplaatsen, roteren of opmaken als één entiteit. Het voorbeeld hieronder werkt met de nieuwste Aspose.Words 24.x release en vereist alleen .NET 6 of hoger.

## Vereisten

- .NET 6 SDK (of een .NET‑versie die door Aspose.Words wordt ondersteund)
- Visual Studio 2022 of VS Code
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
- Basiskennis van C# en het Aspose.Words‑objectmodel

> **Pro tip:** Gebruik de gratis evaluatielicentie van Aspose om watermerkbeperkingen tijdens het testen te vermijden.

## Hoe vormen groeperen met Aspose.Words

Hieronder staat een compleet, uitvoerbaar programma dat **how to start group** demonstreert, een rechthoek toevoegt en de groep afrondt. De code volgt dezelfde logische stroom als het fragment dat je hebt opgegeven, maar voegt context, foutafhandeling en commentaar toe voor duidelijkheid.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Waarom elke stap belangrijk is

| Stap | Doel | Hoe het zich verhoudt tot de zoekwoorden |
|------|------|------------------------------------------|
| **Maak een nieuw leeg document** | Biedt een schoon canvas voor vormbewerkingen. | Zet de basis voor **add shapes word** later. |
| **Initialiseer DocumentBuilder** | De builder is de primaire API voor het invoegen van objecten. | Nodig voordat je **how to start group** kunt uitvoeren. |
| **StartGroupShape** | Begint een logische container; alle volgende vormen worden leden van deze groep. | Beantwoordt direct **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Plaatst individuele vormen binnen de groep. De rechthoekaanroep voldoet aan **insert rectangle shape**; de tekstvorm voldoet aan **add shapes word**. | Toont **group multiple shapes**. |
| **EndGroupShape** | Rondt de groep af zodat je deze als één geheel kunt verplaatsen of opmaken. | Voltooit de **how to group shapes** workflow. |

## Een rechthoekvorm invoegen – dieper duiken

De `InsertShape`‑methode accepteert een `ShapeType`‑enum, breedte en hoogte. Om **insert rectangle shape** met aangepaste opmaak toe te voegen, kun je het voorbeeld uitbreiden:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Waarom opmaken?** Opmaak zorgt ervoor dat de rechthoek opvalt wanneer de groep later wordt verplaatst. Het toont ook aan dat vormeigenschappen kunnen worden ingesteld *voordat* de groep wordt gesloten.

## Word‑niveau vormen toevoegen (add shapes word)

Als je tekst direct in een vorm wilt insluiten — vaak “WordArt” of “tekstvak” genoemd — gebruik dan `ShapeType.TextPlainText`. Na het invoegen kun je tekst in de vorm schrijven met `DocumentBuilder.Writeln` of door de `TextBox`‑eigenschap van de vorm te benaderen:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Dit voldoet aan het **add shapes word**‑zoekwoord en laat zien hoe tekst met de groep kan meereizen.

## Meerdere vormen groeperen – praktische scenario's

Wanneer je **group multiple shapes**, kun je ze behandelen als één object voor positionering, rotatie of schaling. Bijvoorbeeld, nadat de groep is gesloten, kun je de hele groep verplaatsen:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Of roteer de groep:

```csharp
group.Rotation = 45; // degrees
```

Deze bewerkingen zijn alleen mogelijk omdat de vormen dezelfde bovenliggende groep delen.

## Randgevallen afhandelen

1. **Nested groups** – Aspose.Words staat groepen binnen groepen toe. Om een geneste groep te maken, roep je `StartGroupShape` opnieuw aan vóór het aanroepen van `EndGroupShape` voor de binnenste groep.
2. **Empty groups** – Als je een groep start maar nooit een vorm invoegt, zal `EndGroupShape` toch een lege container aanmaken. Dit is onschadelijk maar kan de bestandsgrootte iets vergroten.
3. **Compatibility** – Het gegenereerde DOCX werkt met Word 2010 en later. Oudere versies kunnen de groeperingsmetadata negeren, dus test altijd met de beoogde Word‑versie.

## Volledig bronbestand ter referentie

Sla het volgende op als `Program.cs` in een .NET‑console‑project. De code compileert en draait zonder aanpassingen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Verwachte output

Het openen van `GroupedShapes.docx` in Microsoft Word toont:

- Een licht‑koraalrode rechthoek, een ellips en een tekstvak — allemaal visueel samengevoegd.
- Het selecteren van een deel van de groep selecteert ook de hele groep (er verschijnt één omvattende rechthoek).
- Het verplaatsen of roteren van de groep verplaatst alle drie de vormen samen.

## Veelgestelde vragen

**Q: Kan ik vormen groeperen die al in het document bestaan?**  
A: Ja. Haal de bestaande `Shape`‑objecten op, roep `builder.StartGroupShape()` aan, voeg ze opnieuw in met `builder.InsertShape(existingShape)`, en roep vervolgens `EndGroupShape()` aan.

**Q: Heeft groeperen invloed op de onderliggende XML?**  
A: Aspose.Words voegt een `<w:grpSp>`‑element toe dat elk `<w:sp>`‑knooppunt van een vorm bevat. Dit is volledig conform de Office Open XML‑specificatie.

**Q: Wat als ik later moet degroeperen?**  
A: Er is geen directe “ungroup”‑API, maar je kunt itereren over de kindvormen van de groep (`group.GroupShape.Children`) en ze naar het documentlichaam kopiëren.

## Volgende stappen

Nu je weet hoe je **how to group shapes** kunt, overweeg dan deze gerelateerde onderwerpen:

- **Complexe opmaak toepassen op gegroepeerde vormen** – leer hoe je verloopvullingen, schaduweffecten en lijneigenschappen instelt.
- **Gegroepeerde vormen exporteren als afbeeldingen** – gebruik `Shape.GetShapeRenderer().Save(...)` om een groep te rasteren.
- **Dynamische diagrammen maken** – combineer data‑gedreven positionering met groeperen om automatisch stroomdiagrammen te genereren.

Elk hiervan bouwt voort op de hier behandelde basis en helpt je rijkere, meer interactieve Word‑documenten te maken.

---

*Veel programmeerplezier! Als je deze gids nuttig vond, deel hem dan met teamgenoten of geef ster aan de repository die het voorbeeldproject bevat.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Vormen invoegen in Word‑documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Groepvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechthoekvorm maken in Word met Aspose.Words – Stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}