---
category: general
date: 2026-07-29
description: Teken een rechthoek in Word met Aspose.Words. Leer hoe je een rechthoekvorm,
  een lijnvorm toevoegt en meerdere vormen in één document beheert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: nl
lastmod: 2026-07-29
og_description: Teken een rechthoek in Word met Aspose.Words. Volg deze stapsgewijze
  handleiding om een rechthoekvorm toe te voegen, een lijnvorm toe te voegen en moeiteloos
  met meerdere vormen in Word te werken.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: rechthoek tekenen in Word – Word een meester in het toevoegen van vormen
  in Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: rechthoek tekenen in Word – Voeg vormen toe in Word met Aspose
url: /nl/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Complete Guide to Adding Shapes in Word

Heb je je ooit afgevraagd hoe je **draw rectangle word** documenten kunt tekenen zonder elke keer de UI te openen? Je bent niet de enige. Veel ontwikkelaars moeten Word‑bestanden on‑the‑fly genereren, en de makkelijkste manier is om een bibliotheek het zware werk te laten doen. In deze tutorial laten we je precies zien **hoe je vormen toevoegt**—specifiek een rechthoek en een lijn—met Aspose.Words for .NET, en we blijven focussen op de uitdrukking *draw rectangle word* zodat je nooit de weg kwijtraakt.

Beschouw het als een mini‑kunststudio die in je code leeft. Aan het einde kun je **add rectangle shape**, **add line shape**, en ze zelfs combineren tot **multiple shapes word**‑groepen. Geen UI, geen handmatig gedoe, alleen nette, herhaalbare C#.

## What You’ll Learn

- Een nieuw Word‑document opzetten met Aspose.Words.  
- Een **GroupShape** maken die meerdere objecten kan bevatten.  
- **Add rectangle shape** en **add line shape** binnen die groep toevoegen.  
- De gegroepeerde vormen in de document‑body invoegen.  
- Het bestand opslaan en het resultaat direct bekijken.  

Als je vertrouwd bent met basis‑C# en een kopie van Aspose.Words hebt, ben je klaar. Geen extra NuGet‑pakketten naast de core‑bibliotheek zijn nodig.

> **Pro tip:** Aspose.Words werkt met .NET 6, .NET 7, en .NET Framework 4.6+. Kies de runtime die bij je project past.

![draw rectangle word voorbeeld](https://example.com/placeholder-image.png "draw rectangle word – gegroepeerde vormen in een Word‑bestand")

## draw rectangle word – Setting Up the Document

Voordat we **draw rectangle word** kunnen uitvoeren, hebben we een schoon canvas nodig. De `Document`‑klasse is dat canvas; de `DocumentBuilder` is ons penseel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

De twee regels hierboven geven ons een verse, in‑memory `.docx`. Er wordt nog niets naar schijf geschreven, waardoor we kunnen experimenteren zonder het bestandssysteem te vervuilen.

## How to Add Shapes – Creating a GroupShape Container

Wanneer je **multiple shapes word** wilt laten gedragen als één eenheid—samen verplaatsen, samen roteren—verpak je ze in een `GroupShape`. Beschouw een groep als een map die andere vormen bevat.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Waarom een groep? Omdat je later **add rectangle shape** en **add line shape** wilt toevoegen en ze vervolgens samen wilt verplaatsen. Zonder groep zou je elke vorm afzonderlijk moeten herpositioneren.

## add rectangle shape – Inserting a Rectangle Inside the Group

Nu de container bestaat, laten we **add rectangle shape**. Een rechthoek is een `Shape` waarvan de `ShapeType` `Rectangle` is.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Let op: de waarden van `Left` en `Top` zijn relatief ten opzichte van de oorsprong van de groep, niet van de pagina. Dit maakt het eenvoudig om vormen precies uit te lijnen. De rechthoek verschijnt dicht bij de linkerbovenhoek van de groep.

## add line shape – Adding a Line to the Same Group

Een lijn is gewoon een andere `Shape`, maar de `ShapeType` is `Line`. We positioneren hem onder de rechthoek.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Omdat de hoogte van de lijn nul is, bepaalt de eigenschap `Top` waar de lijn verticaal staat. De `Width` bepaalt hoe lang de lijn horizontaal reikt.

## multiple shapes word – Inserting the Group into the Document Body

We hebben nu een groep die **add rectangle shape** en **add line shape** bevat. De laatste stap is om het geheel in het document te plaatsen.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` plaatst de groep precies waar de `DocumentBuilder` zich op dat moment bevindt. Als je het op een specifieke alinea wilt hebben, verplaats je de builder eerst met `builder.MoveToParagraph(index)`.

## Saving the Result – Seeing the draw rectangle word Output

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Open het gegenereerde bestand in Microsoft Word en je ziet één groep met een rechthoek en een lijn. Je kunt de groep aanklikken, verplaatsen, of zelfs de grootte aanpassen—alle vormen bewegen mee. Dat is de kracht van **multiple shapes word**.

### Expected Output

- Een `.docx`‑bestand genaamd `GroupShape.docx`.  
- Eén pagina met een gegroepeerde rechthoek (120 × 80 pt) dicht bij de linkerbovenhoek.  
- Een horizontale lijn (150 pt lang) net onder de rechthoek.  
- Beide vormen zijn selecteerbaar als één object.

Dubbelklik je op de groep, dan laat Word je elke vorm afzonderlijk bewerken—perfect voor fijne afstemming.

## Common Questions & Edge Cases

**Wat als ik meer dan twee vormen nodig heb?**  
Blijf `group.AppendChild(yourShape)` aanroepen voor elk extra object. De groep kan een onbeperkt aantal vormen bevatten, ideaal voor complexe diagrammen.

**Kan ik de vulkleur van de rechthoek wijzigen?**  
Zeker. Na het maken van de rechthoek, stel `rectangle.FillColor = System.Drawing.Color.LightBlue;` in. Dit werkt voor elke vorm die vullen ondersteunt.

**Moet ik `Height = 0` instellen voor een lijn?**  
Ja, voor een rechte horizontale lijn moet de hoogte nul zijn. Voor een verticale lijn stel je `Width = 0` en geef je `Height` een positieve waarde.

**Werkt dit met .doc‑bestanden (Word 97‑2003)?**  
Aspose.Words kan opslaan naar het oudere `.doc`‑formaat, maar sommige moderne vorm‑features kunnen beperkt zijn. Gebruik `.docx` voor volledige functionaliteit.

**Hoe roteer ik de hele groep?**  
Stel `group.Rotation = 45;` (graden) in vóór het invoegen. De rotatie wordt toegepast op elke onderliggende vorm.

## Recap – How to Add Shapes in Word Programmatically

- **draw rectangle word** begint met het aanmaken van een `Document` en `DocumentBuilder`.  
- Bouw een **GroupShape** om **multiple shapes word** te bevatten.  
- **add rectangle shape** en **add line shape** worden aan de groep toegevoegd.  
- Voeg de groep toe aan de body met `builder.InsertNode`.  
- Sla het bestand op en open het om het visuele resultaat te verifiëren.

Dat is de volledige workflow, samengevat in één duidelijke code‑voorbeeld.

## Next Steps & Related Topics

Nu je weet **how to add shapes**, kun je verder verkennen:

- **add rectangle shape** met afgeronde hoeken (`ShapeType.Rectangle` + `CornerRadius`).  
- Lijnen stylen met verschillende streep‑patronen (`line.LineFormat.DashStyle`).  
- Afbeeldingen naast vormen insluiten voor rijkere rapporten.  
- **multiple shapes word** gebruiken om flowcharts of eenvoudige UML‑diagrammen te bouwen.  

Elk van deze onderwerpen bouwt logisch voort op de basis die we hier hebben gelegd, en ze volgen allemaal hetzelfde patroon: vormen maken, configureren, en indien nodig groeperen.

---

Happy coding! Als je tegen eigenaardigheden aanloopt of een cool use‑case wilt delen, laat dan een reactie achter. Jouw feedback helpt ons allemaal de kunst van **draw rectangle word** en meer onder de knie te krijgen.


## What Should You Learn Next?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑features onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}