---
category: general
date: 2026-09-21
description: Leer hoe je vormen groepeert in Word met Aspose.Words voor C#. Deze stapsgewijze
  handleiding behandelt het maken, positioneren en opslaan van gegroepeerde vormen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: nl
lastmod: 2026-09-21
og_description: Groep vormen in Word met Aspose.Words voor C#. Volg deze beknopte
  tutorial om gegroepeerde vormen programmeermatig te maken, te positioneren en op
  te slaan.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Groep vormen in Word met Aspose.Words – volledige C#‑handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe vormen groeperen in Word met Aspose.Words voor C#
url: /nl/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Word met Aspose.Words voor C#

Als je **vormen in Word** programmatisch moet groeperen, maakt Aspose.Words het eenvoudig. Deze tutorial laat zien hoe je twee rechthoekige vormen maakt, ze naast elkaar plaatst, combineert tot een `GroupShape`, en het resultaat opslaat als een DOCX‑bestand.

Je ziet een compleet, uitvoerbaar voorbeeld, uitleg waarom elke stap belangrijk is, en tips voor het omgaan met veelvoorkomende randgevallen zoals overlappende vormen of dynamische afmetingen. Aan het einde van deze gids kun je vormgroepering integreren in elk Word‑automatiseringsproject.

## Vereisten

* .NET 6.0 (of later) geïnstalleerd – Aspose.Words ondersteunt .NET Standard 2.0+, .NET Core en .NET Framework.
* Een geldige Aspose.Words for .NET‑licentie (of een tijdelijke evaluatiesleutel) – de bibliotheek werkt zonder licentie maar voegt een watermerk toe.
* Visual Studio 2022 (of een andere C#‑IDE) om het voorbeeld te compileren en uit te voeren.

Er zijn geen extra NuGet‑pakketten vereist, behalve `Aspose.Words`.

## Hoe vormen groeperen in Word met Aspose.Words

De kern van de oplossing is een **`GroupShape`**‑object dat fungeert als container voor individuele vormen. Hieronder splitsen we het proces in duidelijke stappen.

### Stap 1: Maak een leeg document en een `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom deze stap?*  
`Document` vertegenwoordigt het volledige DOCX‑bestand, terwijl `DocumentBuilder` vloeiende methoden levert (bijv. `InsertShape`) die automatisch nieuwe elementen op de huidige cursorpositie plaatsen.

### Stap 2: Voeg de eerste rechthoekvorm in

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

De `InsertShape`‑aanroep voegt de vorm toe aan het document en retourneert een `Shape`‑object dat je verder kunt configureren (kleur, rand, enz.). De grootte wordt uitgedrukt in punten (1 pt ≈ 1/72 in).

### Stap 3: Voeg de tweede rechthoek toe en verschuif deze

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Het instellen van `Left` positioneert de vorm relatief ten opzichte van de paginamarge. De offset moet groter zijn dan de breedte van de eerste vorm (100 pt) om overlapping te voorkomen; we gebruiken 120 pt om een kleine ruimte te laten.

### Stap 4: Maak een `GroupShape` die groot genoeg is voor beide rechthoeken

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` neemt het bijbehorende `Document` en de afmetingen van de container. De breedte van de container moet groter zijn dan de rechterrand van de verste vorm; anders zou de tweede vorm worden afgesneden.

### Stap 5: Voeg de individuele vormen toe aan de groep

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Door toe te voegen worden de vormen verplaatst naar de interne collectie van de groep. Na deze aanroep zijn de vormen geen onafhankelijke objecten meer in de documentboom – ze behoren tot de groep.

### Stap 6: Voeg de gegroepeerde vorm weer in het document in

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` plaatst de volledige `GroupShape` op de positie waar de cursor zich momenteel bevindt. Als je de groep in een specifieke alinea nodig hebt, verplaats je de builder eerst naar die alinea.

### Stap 7: Sla het document op

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Het resulterende bestand bevat twee rechthoeken die zich gedragen als één object – je kunt ze samen verplaatsen, van grootte wijzigen of verwijderen in Microsoft Word.

## Volledige broncode

Alle stappen samenvoegen levert een zelfstandige applicatie op:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Verwachte output:** Het openen van *GroupedShapes.docx* in Microsoft Word toont twee rechthoeken naast elkaar, behandeld als één selecteerbaar object. Het slepen van de groep verplaatst beide rechthoeken samen.

## Veelvoorkomende variaties en randgevallen

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Meer dan twee vormen** | Maak extra `Shape`‑objecten, positioneer ze overeenkomstig, en voeg elk toe aan dezelfde `GroupShape`. |
| **Dynamische grootte** | Bereken de breedte/hoogte van de groep op basis van de maximale `Right`‑ en `Bottom`‑waarden van de onderliggende vormen. |
| **Verschillende vormtypen** | `ShapeType.Ellipse`, `ShapeType.Triangle`, enz., kunnen op dezelfde manier worden ingevoegd; de groepscontainer maakt niet uit welk type. |
| **Gedraaide vormen** | Stel `shape.Rotation = 45;` in vóór het toevoegen; de rotatie wordt behouden binnen de groep. |
| **Opslaan als PDF** | Roep `doc.Save("GroupedShapes.pdf");` aan – de groep blijft behouden in de PDF‑rendering. |

**Pro tip:** Na het groeperen kun je nog steeds individuele vormen wijzigen door `group.GetChildNodes(NodeType.Shape, true)` aan te roepen. Dit is handig wanneer je de vulkleur van één rechthoek wilt wijzigen zonder de groep te verbreken.

## Hoe de groepering programmatisch te verifiëren

Als je moet bevestigen dat de vormen correct zijn gegroepeerd (bijv. in unit‑tests), bekijk dan de document‑knooppunt‑hiërarchie:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

De output moet zijn:

```
Number of groups: 1
Children in first group: 2
```

Dit bevestigt dat **groeperen van vormen in Word** is gemaakt zoals verwacht.

## Conclusie

Je weet nu hoe je **vormen in Word** kunt groeperen met Aspose.Words voor C#. Het proces omvat het maken van individuele vormen, ze positioneren, ze in een `GroupShape` verpakken en de groep weer in het document invoegen. Met het volledige voorbeeld hierboven kun je de techniek uitbreiden naar een willekeurig aantal vormen, verschillende typen, of zelfs combineren met tekstvakken en afbeeldingen.

Verken vervolgens gerelateerde onderwerpen zoals **Aspose.Words shape grouping**, **C# Word shape manipulation**, en **DocumentBuilder insert shape** voor meer geavanceerde document‑automatiseringsscenario's. Experimenteer met dynamische afmetingen, conditionele groepering en exporteren naar PDF om de kracht van Aspose.Words volledig te benutten.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Vormen invoegen in Word‑documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Rechthoekvorm maken in Word met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Een schaduw toevoegen aan een Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}