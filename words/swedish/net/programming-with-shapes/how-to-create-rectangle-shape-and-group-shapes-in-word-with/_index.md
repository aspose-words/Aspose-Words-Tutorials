---
category: general
date: 2026-09-05
description: Skapa en rektangelform i ett Word‑dokument med Aspose.Words, och lär
  dig sedan hur du infogar en ellips och grupperar former i Word för rikare layouter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: sv
lastmod: 2026-09-05
og_description: Skapa en rektangel i ett Word‑dokument med Aspose.Words, och se sedan
  hur du infogar en ellips och grupperar former i Word för komplexa layouter.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Skapa rektangelform och gruppera former i Word – Aspose.Words guide
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
title: Hur man skapar en rektangelform och grupperar former i Word med Aspose.Words
url: /sv/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar rektangelform och grupperar former i Word med Aspose.Words

Om du behöver **create rectangle shape** i ett Word‑dokument visar den här guiden de exakta stegen med Aspose.Words för .NET. Du kommer också att se hur du infogar ellipse‑ord, grupperar former i Word och sparar resultatet som en DOCX‑fil. Lösningen fungerar i alla .NET 6+‑projekt och kräver inte att Microsoft Office är installerat på servern.

Tutorialen täcker allt från projektuppsättning till hantering av vanliga layout‑fallgropar, så att du kan kopiera koden och köra den omedelbart.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6 SDK eller senare installerat  
* En NuGet‑kompatibel IDE (Visual Studio, Rider eller VS Code)  
* En Aspose.Words för .NET‑licens (eller en tillfällig evalueringsnyckel)  
* Grundläggande kunskaper i C# och Word‑dokumentstruktur  

Dessa komponenter gör att koden kan kompileras och formerna renderas korrekt.

## Steg 1: Skapa projektet och lägg till Aspose.Words

Skapa ett nytt konsolprojekt och lägg till Aspose.Words‑paketet:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Paketet tillhandahåller klasserna `Document`, `DocumentBuilder`, `Shape` och `GroupShape` som används genom hela tutorialen.

## Steg 2: Initiera ett tomt dokument och en builder

`Document`‑objektet representerar hela Word‑filen, medan `DocumentBuilder` låter dig infoga innehåll programatiskt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Att skapa dokumentet först säkerställer att alla efterföljande form‑operationer har en giltig behållare.

## Steg 3: **Create rectangle shape** och ange dess dimensioner

En rektangel är den vanligaste behållaren för text eller bilder. Du definierar dess storlek i punkter (1 pt ≈ 1/72 tum).

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

Varför detta steg är viktigt: `Shape`‑klassen kapslar geometrin, fyllning och linjeegenskaper. Att sätta `Width` och `Height` innan insättning garanterar att formen visas med förväntad storlek.

## Steg 4: **How to insert ellipse word** – lägg till en ellipsform

En ellips kan användas för ikoner, markörer eller dekorativa element. Koden speglar rektangel‑skapandet, endast `ShapeType` ändras.

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

Egenskaperna `FillColor` och `Line.Color` visar hur du anpassar utseendet utan externa bilder.

## Steg 5: **Group shapes in Word** – kombinera rektangel och ellips

Gruppering låter dig flytta, ändra storlek eller rotera flera former som en enhet. Detta är nödvändigt när du behöver en sammansatt grafik (t.ex. en märkt ikon).

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

När du anropar `AppendChild` tas de ursprungliga formerna bort från huvuddokumentflödet och blir barn till `GroupShape`. Gruppen beter sig som en enda form, vilket förenklar senare layoutjusteringar.

## Steg 6: Spara dokumentet

Skriv slutligen dokumentet till disk. Du kan välja vilket som helst av de stödjade formaten (`.docx`, `.pdf`, `.html`, osv.). För den här tutorialen behåller vi det inhemska Word‑formatet.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Efter att programmet har körts, öppna *GroupShape.docx* i Microsoft Word. Du kommer att se en rektangel och en ellips grupperade tillsammans, placerade på de koordinater du angav.

## Vanliga variationer och kantfall

| Situation | Vad som ska ändras | Orsak |
|-----------|--------------------|-------|
| **Olika storleksenheter** | Använd `ConvertUtil.InchToPoint(2.5)` för tum eller `ConvertUtil.MillimeterToPoint(30)` för millimeter. | Gör koden läsbar när du arbetar med icke‑punkt‑mått. |
| **Lägga till text i rektangeln** | Skapa en `Paragraph`‑nod, sätt dess `Text`‑egenskap och lägg till den i `rectangleShape` via `AppendChild`. | Gör det möjligt att märka formen utan separata textrutor. |
| **Rotera gruppen** | Sätt `groupShape.Rotation = 45;` (grader). | Användbart för att skapa diagonala märken eller vattenstämplar. |
| **Spara som PDF** | Anropa `doc.Save("GroupShape.pdf");`. | Aspose.Words rasteriserar automatiskt vektorformer för PDF‑utmatning. |
| **Flera grupper** | Skapa ytterligare `GroupShape`‑instanser och upprepa append/insert‑stegen. | Möjliggör komplexa sidlayouter med flera oberoende sammansättningar. |

### Proffstips

Lägg alltid till former **innan** du grupperar dem. Om du försöker gruppera en form som redan är en del av en annan grupp kastar Aspose.Words ett `ArgumentException`. Att bygga gruppen i en enda metod förhindrar detta körningsfel.

### Se upp för

* **Koordinatsystem** – `Left` och `Top` mäts från sidans vänstra och övre marginaler, inte från dokumentets kant. Missförstånd här kan placera former utanför sidan.  
* **Licensiering** – Utan en giltig licens kommer det sparade dokumentet att innehålla ett vattenmärke som säger “Aspose.Words for .NET Evaluation”. Applicera din licens tidigt i koden (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) för att undvika detta.

## Fullständig källkod (körbar)

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

När du kör detta program skapas *GroupShape.docx* med de grupperade formerna exakt som beskrivits.

## Slutsats

Du vet nu hur du **create rectangle shape**, **how to insert ellipse word** och **group shapes in Word** med Aspose.Words. Det kompletta exemplet demonstrerar hela arbetsflödet – från initiering av ett dokument till sparande av den slutliga filen – så att du kan integrera formhantering i vilken automatiserad rapport‑ eller dokumentgenereringslösning som helst.

### Vad blir nästa steg?

* Utforska **aspose.words create shapes** för mer komplex geometri såsom `Polygon` eller `Freeform`.  
* Kombinera grupperade former med **content controls** för att bygga dynamiska mallar.  
* Konvertera DOCX till PDF eller HTML för att se hur vektorformer renderas i olika format.  

Känn dig fri att experimentera med olika storlekar, färger och rotationer. När du behärskar formgruppering kan du skapa sofistikerade diagram, märken och anpassade UI‑element direkt i Word‑dokument.

## Vad bör du lära dig härnäst?

De följande tutorialerna behandlar närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}