---
category: general
date: 2026-09-18
description: Skapa en rektangelform i ett Word‑dokument med C#. Lär dig hur du lägger
  till flera former, lägger till former i en grupp och infogar en gruppform med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: sv
lastmod: 2026-09-18
og_description: Skapa rektangelform i en Word‑fil med C#. Den här guiden visar hur
  du lägger till flera former, lägger till former i en grupp och infogar gruppform
  med hjälp av Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Skapa rektangelform och gruppera former i C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Skapa rektangelform och gruppera flera former i C#
url: /sv/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform och gruppera flera former i C#

Om du behöver **create rectangle shape** i ett Word‑dokument visar den här handledningen en komplett lösning. Du kommer att se hur du **add multiple shapes**, **add shapes to a group** och **insert group shape** med Aspose.Words API för .NET.

Att arbeta med former är ett vanligt krav när man genererar rapporter, kontrakt eller marknadsföringsmaterial programatiskt. I slutet av den här guiden har du en körbar C#‑konsolapplikation som skapar en `.docx`‑fil som innehåller en rektangel, en ellips och en grupp som innehåller båda formerna.

Det enda förutsättningen är ett aktuellt .NET‑SDK (6.0 eller senare) och en licensierad kopia av Aspose.Words för .NET. Inga ytterligare verktyg krävs.

## Förutsättningar

- .NET 6.0 SDK eller nyare  
- Aspose.Words for .NET (NuGet‑paket `Aspose.Words`)  
- Grundläggande kunskap om C#‑syntax  

Du kan installera paketet med följande kommando:

```bash
dotnet add package Aspose.Words
```

## Steg 1: Skapa rektangelform med Aspose.Words

Det första steget är att skapa ett `Shape`‑objekt av typen `Rectangle`. Detta objekt representerar den visuella rektangeln som kommer att visas i dokumentet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Varför detta är viktigt:** `ShapeType.Rectangle` talar om för Aspose.Words att rendera en geometrisk rektangel. Att sätta `Width` och `Height` definierar dess storlek i punkter (1 punkt = 1/72 tum). Att lägga till fyllnings‑ och linjefärger gör formen synlig utan att behöva ytterligare styling.

## Steg 2: Lägg till flera former i dokumentet

Efter rektangeln kan du skapa ett godtyckligt antal ytterligare former. I det här exemplet lägger vi till en ellips för att demonstrera hur **add multiple shapes** fungerar.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Varför detta är viktigt:** Varje anrop till `new Shape` skapar ett självständigt ritobjekt. Genom att infoga dem sekventiellt bygger du upp en samling av former som senare kan grupperas eller placeras individuellt.

## Steg 3: Lägg till former i en grupp

Att gruppera former förenklar layout‑hantering eftersom gruppen beter sig som en enda nod. Detta steg visar hur man **add shapes to group** med `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Varför detta är viktigt:** `GroupShape` fungerar som en behållare. När du flyttar, roterar eller ändrar storlek på gruppen följer alla underliggande former automatiskt. Begränsningsrutan (200 × 200 punkter) definierar koordinatrymden för de underordnade formerna.

## Steg 4: Infoga gruppform i dokumentet

Nu när gruppen innehåller rektangeln och ellipsen måste du **insert group shape** på önskad plats. Buildern har redan placerat den tomma gruppen, men du kan också infoga den någon annanstans om så behövs.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Varför detta är viktigt:** Genom att justera `Left` och `Top` flyttas hela gruppen inom sidan. När du sparar dokumentet skrivs formhierarkin till en `.docx`‑fil som kan öppnas i Microsoft Word, LibreOffice eller någon kompatibel visare.

## Komplett körbart exempel

Nedan är hela programmet som kombinerar alla steg. Kopiera koden till ett nytt konsolprojekt och kör det för att generera `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Förväntat resultat:**  
När du öppnar `GroupShapeExample.docx` visas en enda grupp som innehåller en ljusblå rektangel och en ljuskorall‑ellips, båda placerade i en 200 × 200‑punktsbehållare. Gruppen kan väljas som ett enda objekt i Word, vilket bekräftar att **add shapes to group** lyckades.

## Vanliga variationer och kantfall

| Situation | Rekommenderad justering |
|-----------|------------------------|
| Olika formtyper (t.ex. `ShapeType.Line`) | Skapa formen med önskad `ShapeType` och ställ in dess geometri därefter. |
| Behöver rotera en form | Använd `shape.Rotation = 45;` (grader) innan du lägger till den i gruppen. |
| Större dokument med många grupper | Återanvänd en enda `DocumentBuilder`‑instans; undvik att skapa en ny builder för varje grupp för att minska minnesbelastningen. |
| Spara till PDF istället för DOCX | Anropa `doc.Save("output.pdf", SaveFormat.Pdf);` efter att gruppen har infogats. |

**Pro tip:** Ange alltid explicita `Left`‑ och `Top`‑värden för gruppen när du behöver exakt placering. Om du utelämnar dem ärver gruppen builderns aktuella markörposition, vilket kan leda till oväntade layoutresultat.

## Slutsats

Du vet nu hur du **create rectangle shape**, **add multiple shapes**, **add shapes to group** och **insert group shape** i ett Word‑dokument med C#. Det kompletta exemplet demonstrerar hela arbetsflödet från dokumentskapande till sparande av den slutgiltiga filen.  

Nästa steg är att utforska relaterade ämnen som **positioning shapes relative to text**, **applying text wrapping** och **exporting grouped shapes to PDF**. Dessa tillägg låter dig bygga sofistikerade, programatiska dokumentlayouter med Aspose.Words.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}