---
category: general
date: 2026-10-04
description: Leer hoe je vormen groepeert in Word met C#. Deze gids laat zien hoe
  je een rechthoekvorm invoegt, meerdere vormen groepeert en een leeg Word‑bestand
  via code maakt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: nl
lastmod: 2026-10-04
og_description: Groep vormen in Word met C#. Volg deze stap‑voor‑stap handleiding
  om een rechthoekvorm in te voegen, meerdere vormen te groeperen en een leeg Word‑bestand
  te maken met DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Vormen groeperen in Word met C# – volledige DocumentBuilder‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Hoe vormen te groeperen in Word met C# en DocumentBuilder
url: /nl/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Word met C# en DocumentBuilder

Als je **vormen wilt groeperen in Word** vanuit een C#-applicatie, laat deze tutorial je precies zien hoe je dat doet. Je ziet hoe je een *rechthoekvorm* kunt *invoegen*, verschillende tekeningen combineert tot één groep, en uiteindelijk **een leeg Word‑bestand maakt** dat de gegroepeerde objecten bevat.

Werken met vormen is een veelvoorkomende eis bij het programmatically genereren van rapporten, facturen of aangepaste sjablonen. Aan het einde van deze gids heb je een herbruikbaar code‑fragment dat je in elk .NET‑project kunt plaatsen dat naar Aspose.Words verwijst.

## Wat je zult leren

- Maak een leeg Word‑document vanaf nul.  
- Voeg een rechthoekvorm en een ellips toe met `DocumentBuilder`.  
- **Meerdere vormen groeperen** in een `GroupShape`.  
- Gebruik **append child to group** om de hiërarchie op te bouwen.  
- Sla het bestand op schijf op en controleer het resultaat.

Ervaring met Aspose.Words is niet vereist, maar je moet wel een basisbegrip hebben van C# en .NET‑ontwikkeling.

## Vereisten

| Vereiste | Reden |
|-------------|--------|
| .NET 6.0 of later | Biedt de runtime voor de C#‑code. |
| Aspose.Words for .NET (latest version) | Levert `Document`, `DocumentBuilder` en vormklassen. |
| Een IDE zoals Visual Studio 2022 (of VS Code) | Maakt het eenvoudig om het voorbeeld te compileren en uit te voeren. |
| Schrijfrechten voor een map op je computer | Nodig voor de `doc.save`‑aanroep. |

Installeer Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Vormen groeperen in Word – stapsgewijze handleiding

Hieronder staat het volledige, uitvoerbare programma. Elk gedeelte wordt in detail uitgelegd zodat je begrijpt **waarom** de code op deze manier is geschreven, en niet alleen **wat** hij doet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Waarom elke stap belangrijk is

1. **Maak een leeg Word‑bestand** – Beginnen met een schoon document garandeert dat geen verborgen opmaak de positionering van vormen beïnvloedt.  
2. **Initialiseer DocumentBuilder** – `DocumentBuilder` abstraheert low‑level knooppuntmanipulatie, zodat je je kunt concentreren op de lay-out.  
3. **Voeg individuele vormen in** – Je hebt eerst afzonderlijke objecten nodig (`insert rectangle shape` en een ellips) voordat je ze kunt groeperen. Het aanpassen van `Left` en `Top` zorgt ervoor dat ze naast elkaar verschijnen.  
4. **Meerdere vormen groeperen** – Door een `GroupShape` te maken en **append child to group** te gebruiken, zet je twee onafhankelijke tekeningen om in één logische eenheid. Het verplaatsen of wijzigen van de grootte van de groep beïnvloedt beide kinderen tegelijk.  
5. **Sla het document op** – Het uiteindelijke bestand, `GroupedShapes.docx`, kan in Microsoft Word worden geopend om te verifiëren dat de rechthoek en ellips inderdaad gegroepeerd zijn (selecteer één, en beide bewegen samen).

### Verwachte uitvoer

Open `GroupedShapes.docx` in Microsoft Word:

- Je ziet een rechthoek en een ellips naast elkaar geplaatst.  
- Het selecteren van een van beide vormen markeert beide, wat bevestigt dat ze tot dezelfde groep behoren.  
- De groep kan worden versleept, van grootte worden veranderd of opgemaakt als één enkel object.

![Diagram van gegroepeerde rechthoek en ellips in een Word‑document](https://example.com/grouped-shapes.png){: .center-image alt="Diagram van gegroepeerde rechthoek en ellips in een Word‑document"}

*De screenshot illustreert de uiteindelijke gegroepeerde vormen.*

---

## Rechthoekvorm invoegen – grootte en stijl aanpassen

Als je een rechthoek nodig hebt met een specifieke vulkleur of rand, wijzig dan het `Shape`‑object na het invoegen:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Deze eigenschappen maken deel uit van de `Shape`‑klasse en werken voor elk type vorm, niet alleen rechthoeken. Het aanpassen van de stijl voordat je **append child to group** gebruikt, zorgt ervoor dat de groep de visuele eigenschappen erft die je hebt ingesteld.

---

## Meerdere vormen groeperen – meer dan twee objecten verwerken

Het voorbeeld groepeert een rechthoek en een ellips, maar je kunt elk aantal vormen toevoegen:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Pro tip:** Nadat je een complexe groep hebt opgebouwd, kun je de lay-out vergrendelen om accidentele wijzigingen te voorkomen:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – volgorde is belangrijk

De volgorde waarin je `AppendChild` aanroept bepaalt de Z‑order (welke vorm bovenop verschijnt). In het voorbeeld wordt de rechthoek eerst toegevoegd, daarna de ellips, zodat de ellips de rechthoek overlapt als ze elkaar kruisen. Herschikken is zo simpel als `RemoveChild` aanroepen en opnieuw toevoegen:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Leeg Word‑bestand maken – herbruikbare hulpmethode

Als je applicatie vaak een nieuw document nodig heeft, verpak dan de creatielogica:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Je kunt vervolgens de `new Document()`‑regel in het hoofdprogramma vervangen door `CreateBlankWordFile()`. Dit demonstreert het concept **create blank word file** op een herbruikbare manier.

---

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|-------|----------------|-----|
| Vormen verschijnen buiten de pagina | Standaardwaarden voor `Left`/`Top` zijn 0, waardoor de vorm op de marge wordt geplaatst. | Stel `Left` en `Top` expliciet in na het invoegen. |
| Groep verliest opmaak | Het wijzigen van een kindvorm nadat deze aan een groep is toegevoegd, kan de lay-out van de groep breken. | Pas alle visuele eigenschappen **voor** het aanroepen van `AppendChild` toe. |
| Opgeslagen bestand is leeg | `DocumentBuilder` werd nooit gebruikt om een knooppunt toe te voegen, of `doc.Save` werd aangeroepen op een andere `Document`‑instantie. | Controleer of je hetzelfde `Document` opslaat dat je hebt opgebouwd. |
| Compatibiliteitswaarschuwingen in Word | Gebruik van nieuwere vormfuncties die niet worden ondersteund |  |

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Groepvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vormen invoegen in Word‑documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Rechthoekvorm maken in Word met C# – stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}