---
category: general
date: 2026-08-04
description: Sla een docx‑bestand programmatisch op terwijl je een rechthoekvorm en
  gegroepeerde vormen toevoegt in Word. Leer hoe je de afmetingen van vormen instelt
  en een tekstvak programmatisch maakt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: nl
lastmod: 2026-08-04
og_description: Sla een docx-bestand op met C# door een rechthoekvorm toe te voegen,
  vormen te groeperen in Word, de afmetingen van de vorm in te stellen en een tekstvak
  programmatically te maken.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Docx-bestand opslaan met gegroepeerde vormen in Word – C# stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Docx-bestand met gegroepeerde vormen opslaan in Word met C#
url: /nl/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX-bestand opslaan met gegroepeerde vormen in Word met C#

Als je een **docx-bestand wilt opslaan** dat verschillende vormen bevat die samen zijn gerangschikt, laat deze gids je zien hoe je dit doet met C#. Je leert hoe je een **rechthoekvorm toevoegt**, meerdere vormen groepeert in een Word‑document, **vormafmetingen instelt**, en **een tekstvak programmeermatig maakt**. De oplossing werkt met de nieuwste Aspose.Words voor .NET en draait op .NET 6 of hoger.

De tutorial loopt elke stap door, van projectconfiguratie tot de uiteindelijke `doc.Save`‑aanroep. Aan het einde heb je een herbruikbare code‑snippet die je in elk console‑ of ASP.NET‑project kunt plakken. Er zijn geen externe scripts of handmatige bewerkingen van het DOCX‑bestand nodig.

## Vereisten

* .NET 6 SDK (of nieuwer) geïnstalleerd.
* Een geldige licentie voor **Aspose.Words for .NET** (de gratis proefversie werkt voor testen).
* Visual Studio 2022, VS Code, of een IDE die .NET‑projecten kan bouwen.

De code gebruikt alleen de Aspose.Words‑namespace, dus er zijn geen extra NuGet‑pakketten nodig.

## DOCX-bestand opslaan met gegroepeerde vormen in Word

De kern van de oplossing is het bouwen van een `GroupShape` die een rechthoek en een tekstvak bevat, vervolgens de groep in het document invoegen en `doc.Save` aanroepen. De volgende secties splitsen het proces op in hanteerbare delen.

### 1. Maak een nieuw document en een builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom deze stap belangrijk is* – Een nieuw `Document`‑object vertegenwoordigt een leeg *.docx*‑bestand. `DocumentBuilder` biedt high‑level methoden zoals `InsertNode`, die we zullen gebruiken om de groepsvorm te plaatsen.

### 2. Voeg een rechthoekvorm toe aan een groep

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Waarom deze stap belangrijk is* – De **add rectangle shape**‑bewerking toont hoe je een visueel element definieert met exacte grootte en positie. De rechthoek bevindt zich binnen `group`, dus het verplaatsen van de groep verplaatst later automatisch de rechthoek.

### 3. Groepeer vormen in een Word‑document

De `GroupShape`‑klasse groepeert meerdere tekenobjecten. Groeperen is handig wanneer je verschillende objecten als één eenheid wilt behandelen (bijv. ze samen verplaatsen, roteren of kopiëren).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Waarom we groeperen* – Groeperen vermindert de complexiteit van de lay-out. In plaats van elke vorm afzonderlijk op de pagina te positioneren, pas je de `Left`, `Top`, `Width` en `Height` van de groep één keer aan.

### 4. Stel vormafmetingen in voor een precieze lay-out

Zowel de groep als de onderliggende vormen hebben expliciete afmetingen nodig; anders past Word standaardgroottes toe die mogelijk niet overeenkomen met je ontwerp.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Waarom we afmetingen instellen* – Precieze metingen zorgen ervoor dat de rechthoek en het tekstvak niet onbedoeld overlappen en dat het uiteindelijke **save docx file** overeenkomt met de beoogde lay-out.

### 5. Maak een tekstvak programmeermatig binnen de groep

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Waarom deze stap belangrijk is* – Het **create textbox programmatically**‑segment laat zien hoe je rijke tekst in een vorm kunt insluiten. Het gebruik van een `Paragraph` en `Run` geeft je later volledige controle over de opmaak.

### 6. Voeg de groepsvorm in en **sla docx-bestand op**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Waarom deze laatste stap belangrijk is* – De `InsertNode`‑aanroep plaatst de gegroepeerde vormen precies waar de cursor van de builder zich bevindt. De `doc.Save`‑methode voert de **save docx file**‑operatie uit en schrijft een volledig functioneel Word‑document naar schijf.

> **Resultaat:** Het openen van *GroupShape.docx* in Microsoft Word toont een rechthoek aan de linkerkant en een tekstvak aan de rechterkant, beide samen vergrendeld binnen één groep. Je kunt de groep als één geheel verplaatsen, de grootte aanpassen, of extra opmaak toepassen.

## Volledig, uitvoerbaar voorbeeld

Kopieer de onderstaande code naar een nieuw console‑project (`dotnet new console`) en voer `dotnet run` uit. Het programma maakt `GroupShape.docx` aan in de output‑map van het project.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Verwachte output

* Een bestand met de naam **GroupShape.docx** verschijnt in de output‑directory.
* Het openen van het bestand toont een rechthoekige vorm aan de linkerkant en een tekstvak met “Grouped text” aan de rechterkant, beide samen vergrendeld.
* Het selecteren van een van de vormen verplaatst de hele groep, wat bevestigt dat de **group shapes word**‑functionaliteit werkt zoals bedoeld.

## Veelvoorkomende variaties en randgevallen

| Situation | Recommendation |
|-----------|----------------|
| Meer dan twee vormen nodig | Voeg extra `Shape`‑objecten toe aan `group` voordat je `builder.InsertNode` aanroept. |
| De groep op een specifieke pagina laten verschijnen | Verplaats de cursor van de builder met `builder.MoveToDocumentEnd()` of `builder.MoveToPage(pageNumber)`. |
| Andere eenheden nodig (bijv. centimeters) | Gebruik `ConvertUtil.InchToPoint(1.0)` om inches naar points te converteren, de eenheid die Word verwacht. |
| Het tekstvak tekst laten omwikkelen | Stel `textBox.TextBoxWrap = TextBoxWrapType.Square` in na het aanmaken van het tekstvak. |
| Werken met oudere .NET Framework‑versies | Dezelfde API werkt met .NET Framework 4.7+, maar zorg ervoor dat je de juiste Aspose.Words‑versie referereert. |

**Pro tip:** Stel de `Width` en `Height` van de groep altijd *na* het toevoegen van alle onderliggende vormen in. Dit garandeert dat de groep volledig zijn inhoud omsluit, waardoor afsnijden wordt voorkomen wanneer het document in Word wordt geopend.

## Conclusie

Je weet nu hoe je een **docx-bestand opslaat** terwijl je **een rechthoekvorm toevoegt**, **vormen groepeert in Word**, **vormafmetingen instelt**, en **een tekstvak programmeermatig maakt** met Aspose.Words voor .NET. Het volledige voorbeeld toont een schoon, herhaalbaar patroon dat je kunt aanpassen aan complexere lay-outs, zoals grafieken, afbeeldingen,

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Groepsvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Vorm Schaduw Tutorial – Voeg een schaduw toe aan een Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}