---
category: general
date: 2026-10-07
description: Skapa ett tomt Word-dokument i C# och lär dig att lägga till en rektangel,
  infoga en bildform och gruppera flera former för dynamiska rapporter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: sv
lastmod: 2026-10-07
og_description: Skapa ett tomt Word‑dokument i C# med Aspose.Words. Lär dig hur du
  lägger till en rektangel, infogar en bildform och grupperar flera former för professionella
  dokument.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Skapa ett tomt Word-dokument och gruppera former i C# – steg-för-steg guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man skapar ett tomt Word‑dokument och grupperar former i C#
url: /sv/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt Word-dokument och grupperar former i C#

Om du behöver **create blank Word document** programatiskt, visar den här guiden exakt hur. Du kommer att se hur du **add rectangle shape**, **insert image shape**, och **group multiple shapes** så att de beter sig som ett enda objekt när du senare **add image to Word**.

Att arbeta med Word-filer från kod kan kännas skrämmande, men Aspose.Words gör processen enkel. I slutet av den här handledningen har du ett återanvändbart C#‑snutt som genererar en ren, tom Word‑fil som innehåller en grupperad rektangel och en logotyp. Du kan bädda in resultatet i fakturor, rapporter eller någon automatiserad dokumentarbetsflöde.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+).  
* En giltig Aspose.Words för .NET-licens eller en gratis utvärderingsnyckel.  
* En bildfil (t.ex. `logo.png`) placerad i en mapp som du kan referera till från koden.  
* Visual Studio 2022 eller någon C#‑kompatibel IDE.

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Hur man skapar ett tomt Word-dokument med Aspose.Words

Det första steget är alltid att **create blank Word document**. Detta objekt kommer att hysa alla efterföljande former.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representerar hela `.docx`‑filen. Vid detta tillfälle är filen tom, vilket uppfyller kravet *create blank Word document*.

## Skapa en behållare för att gruppera flera former

Att gruppera former låter dig flytta, rotera eller ändra storlek på dem tillsammans. Aspose.Words tillhandahåller `GroupShape`‑klassen för detta ändamål.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

`Bounds`‑rektangeln bestämmer var gruppen visas på sidan. Genom att placera gruppen i det första stycket garanterar du att **create blank Word document** omedelbart innehåller en visuell behållare.

## Hur man lägger till en rektangel‑form i gruppen

Ett vanligt krav är att **add rectangle shape** som bakgrund eller ram. Följande kod skapar en rektangel och lägger till den i den tidigare definierade gruppen.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Eftersom rektangeln lever inuti `GroupShape` kommer den att röra sig tillsammans med alla andra former du lägger till senare. Detta är kärnan i **group multiple shapes**‑funktionaliteten.

## Hur man infogar en bild‑form i gruppen

Nästa steg är att du **insert image shape** (logotypen) och placerar den bredvid rektangeln. Detta demonstrerar **add image to Word**‑arbetsflödet.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

`SetImage`‑metoden läser filen och bäddar in den direkt i Word‑dokumentet, vilket säkerställer att bilden kvarstår även när källfilen flyttas. Detta slutför steget **insert image shape** och fullbordar kravet **add image to Word**.

## Spara dokumentet

Slutligen sparas filen till disk. Den sparade filen innehåller det tomma dokumentet, den grupperade rektangeln och den inbäddade logotypen.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

När du öppnar `GroupShape.docx` i Microsoft Word ser du en enda grupp som inkluderar en ljusgrå rektangel och logotypen placerad sida‑vid‑sida. Att markera någon del av gruppen låter dig flytta eller ändra storlek på hela samlingen, vilket bevisar att formerna faktiskt **group multiple shapes**.

## Komplett, körbart exempel

Nedan är hela programmet som du kan kopiera, klistra in och köra. Ersätt `YOUR_DIRECTORY` med en absolut eller relativ sökväg som finns på din maskin.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Förväntat resultat

* En fil med namnet `GroupShape.docx` placerad i `YOUR_DIRECTORY`.  
* När du öppnar filen i Word visas en enda visuell grupp som innehåller en grå rektangel till vänster och `logo.png` till höger.  
* Att markera någon del av den visuella gruppen låter dig flytta eller ändra storlek på hela samlingen, vilket bekräftar att formerna korrekt **group multiple shapes**.

## Vanliga frågor och hantering av kantfall

| Fråga | Svar |
|---|---|
| **Kan jag lägga till fler än två former i samma grupp?** | Ja. Anropa `group.AppendChild(yourShape)` för varje ytterligare `Shape`. Gruppen kan innehålla ett godtyckligt antal ritobjekt. |
| **Vad händer om bildfilen saknas?** | `SetImage` kommer att kasta ett `FileNotFoundException`. Omslut anropet i ett try‑catch‑block och tillhandahåll en reserv (t.ex. en platshållarform). |
| **Behöver jag sätta `WrapType` för formerna?** | Som standard är former inline. Om du behöver flytande beteende, sätt `picture.WrapType = WrapType.Inline;` eller ett annat wrap‑läge innan du lägger till i gruppen. |
| **Hur påverkar dokumentstorleken gruppens gränser?** | `Bounds`‑rektangeln definieras i punkter (1 pt ≈ 1/72 tum). Justera storleken om du placerar gruppen på en annan sidlayout (t.ex. A4 vs. Letter). |
| **Kan jag återanvända samma grupp i ett annat dokument?** | Ja. Klona gruppen med `GroupShape cloned = (GroupShape)group.Clone(true);` och infoga den i ett annat `Document`. |

## Pro‑tips

* **Återanvänd `DocumentBuilder`** för att lägga till text före eller efter gruppen. Den respekterar automatiskt den aktuella markörpositionen.  
* **Sätt `Shape.StrokeColor`** om du behöver en synlig kant runt rektangeln.  
* **Använd högupplösta PNG‑filer** för logotypen för att undvika pixling när  

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa rektangel‑form i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Infoga inline‑bild i Word-dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}