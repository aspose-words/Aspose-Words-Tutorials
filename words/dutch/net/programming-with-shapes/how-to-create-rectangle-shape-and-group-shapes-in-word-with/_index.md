---
category: general
date: 2026-09-05
description: Maak een rechthoekvorm in een Word‑document met Aspose.Words, en leer
  vervolgens hoe je een ellips kunt invoegen en vormen kunt groeperen in Word voor
  rijkere lay‑outs.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: nl
lastmod: 2026-09-05
og_description: Maak een rechthoekvorm in een Word‑document met Aspose.Words, en zie
  vervolgens hoe je een ellips invoegt en vormen groepeert in Word voor complexe lay‑outs.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Maak een rechthoekvorm en groepeer vormen in Word – Aspose.Words‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een rechthoekvorm te maken en vormen te groeperen in Word met Aspose.Words
url: /nl/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een rechthoekvorm te maken en vormen te groeperen in Word met Aspose.Words

Als u een **rechthoekvorm** in een Word‑document moet maken, laat deze gids u de exacte stappen zien met Aspose.Words voor .NET. U ziet ook hoe u een ellips in Word kunt invoegen, vormen kunt groeperen in Word, en het resultaat opslaat als een DOCX‑bestand. De oplossing werkt in elk .NET 6+‑project en vereist geen Microsoft Office geïnstalleerd op de server.

De tutorial behandelt alles, van projectconfiguratie tot het omgaan met veelvoorkomende lay‑outproblemen, zodat u de code kunt kopiëren en direct kunt uitvoeren.

## Vereisten

* .NET 6 SDK of later geïnstalleerd  
* Een NuGet‑compatibele IDE (Visual Studio, Rider of VS Code)  
* Een Aspose.Words voor .NET‑licentie (of een tijdelijke evaluatiesleutel)  
* Basiskennis van C# en de structuur van Word‑documenten  

Deze items zorgen ervoor dat de code compileert en de vormen correct worden gerenderd.

## Stap 1: Het project instellen en Aspose.Words toevoegen

Maak een nieuw console‑project aan en voeg het Aspose.Words‑pakket toe:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Het pakket levert de `Document`, `DocumentBuilder`, `Shape` en `GroupShape`‑klassen die door de hele tutorial worden gebruikt.

## Stap 2: Een leeg document en een builder initialiseren

Het `Document`‑object vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` u in staat stelt inhoud programmatisch in te voegen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Het eerst aanmaken van het document zorgt ervoor dat alle daaropvolgende vormbewerkingen een geldige container hebben.

## Stap 3: **Rechthoekvorm maken** en de afmetingen instellen

Een rechthoek is de meest voorkomende container voor tekst of afbeeldingen. U definieert de grootte in punten (1 pt ≈ 1/72 inch).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Waarom deze stap belangrijk is: de `Shape`‑klasse omvat geometrie-, vul- en lijn‑eigenschappen. Het instellen van `Width` en `Height` vóór het invoegen garandeert dat de vorm verschijnt met de verwachte grootte.

## Stap 4: **Hoe een ellips in Word in te voegen** – voeg een ellipsvorm toe

Een ellips kan worden gebruikt voor pictogrammen, markeringen of decoratieve elementen. De code spiegelt de creatie van de rechthoek, alleen verandert de `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

De eigenschappen `FillColor` en `Line.Color` laten zien hoe u het uiterlijk kunt aanpassen zonder externe afbeeldingen.

## Stap 5: **Vormen groeperen in Word** – combineer rechthoek en ellips

Groeperen stelt u in staat meerdere vormen als één geheel te verplaatsen, van grootte te wijzigen of te roteren. Dit is essentieel wanneer u een samengestelde grafiek nodig heeft (bijv. een gelabeld pictogram).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Wanneer u `AppendChild` aanroept, worden de oorspronkelijke vormen uit de hoofd‑documentstroom verwijderd en kinderen van de `GroupShape`. De groep gedraagt zich als één enkele vorm, waardoor latere lay‑outaanpassingen eenvoudiger worden.

## Stap 6: Het document opslaan

Schrijf tenslotte het document naar de schijf. U kunt elk ondersteund formaat kiezen (`.docx`, `.pdf`, `.html`, enz.). Voor deze tutorial behouden we het native Word‑formaat.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Na het uitvoeren van het programma opent u *GroupShape.docx* in Microsoft Word. U ziet een rechthoek en een ellips gegroepeerd, gepositioneerd op de coördinaten die u hebt opgegeven.

## Veelvoorkomende variaties en randgevallen

| Situatie | Wat te wijzigen | Reden |
|----------|----------------|-------|
| **Verschillende eenheden voor grootte** | Gebruik `ConvertUtil.InchToPoint(2.5)` voor inches of `ConvertUtil.MillimeterToPoint(30)` voor millimeters. | Houdt de code leesbaar wanneer u werkt met niet‑punt‑metingen. |
| **Tekst toevoegen binnen de rechthoek** | Maak een `Paragraph`‑node, stel de `Text`‑eigenschap in, en voeg deze toe aan `rectangleShape` via `AppendChild`. | Hiermee kunt u de vorm labelen zonder aparte tekstvakken. |
| **De groep roteren** | Stel `groupShape.Rotation = 45;` (graden) in. | Handig voor het maken van diagonale badges of watermerken. |
| **Opslaan als PDF** | Roep `doc.Save("GroupShape.pdf");` aan. | Aspose.Words rastert vectorvormen automatisch voor PDF‑output. |
| **Meerdere groepen** | Maak extra `GroupShape`‑instanties aan en herhaal de append/insert‑stappen. | Maakt complexe paginalay‑outs mogelijk met verschillende onafhankelijke composieten. |

### Pro‑tip

Voeg vormen altijd **voor** het groeperen toe. Als u probeert een vorm te groeperen die al deel uitmaakt van een andere groep, gooit Aspose.Words een `ArgumentException`. Het bouwen van de groep in één methode voorkomt deze runtime‑fout.

### Let op

* **Coördinatensysteem** – `Left` en `Top` worden gemeten vanaf de linkermarge en bovenmarge van de pagina, niet vanaf de documentrand. Misinterpretatie kan vormen buiten de pagina plaatsen.  
* **Licenties** – Zonder een geldige licentie bevat het opgeslagen document een watermerk met de tekst “Aspose.Words for .NET Evaluation”. Pas uw licentie vroeg in de code toe (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) om dit te voorkomen.

## Volledige broncode (uitvoerbaar)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Het uitvoeren van dit programma produceert *GroupShape.docx* met de gegroepeerde vormen precies zoals beschreven.

## Conclusie

U weet nu hoe u **een rechthoekvorm maakt**, **een ellips in Word invoegt**, en **vormen groepeert in Word** met Aspose.Words. Het volledige voorbeeld toont de volledige workflow — van het initialiseren van een document tot het opslaan van het eindbestand — zodat u vormverwerking kunt integreren in elke geautomatiseerde rapportage‑ of documentgeneratie‑oplossing.

### Wat volgt?

* Verken **aspose.words create shapes** voor complexere geometrie zoals `Polygon` of `Freeform`.  
* Combineer gegroepeerde vormen met **content controls** om dynamische sjablonen te bouwen.  
* Converteer de DOCX naar PDF of HTML om te zien hoe vectorvormen worden gerenderd in verschillende formaten.  

Voel u vrij om te experimenteren met verschillende groottes, kleuren en rotaties. Wanneer u het groeperen van vormen onder de knie heeft, kunt u geavanceerde diagrammen, badges en aangepaste UI‑elementen direct in Word‑documenten bouwen.

## Wat moet u hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om u te helpen extra API‑functies te beheersen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Groepvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vormen invoegen in Word‑documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}