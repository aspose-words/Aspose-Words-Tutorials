---
category: general
date: 2026-09-08
description: Lär dig hur du grupperar former i Word med en DocumentBuilder, skapar
  ett tomt Word‑dokument och infogar en rektangelform med bara några rader C#‑kod.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: sv
lastmod: 2026-09-08
og_description: Gruppera former i Word med DocumentBuilder. Den här handledningen
  visar hur du skapar ett tomt Word‑dokument, infogar en rektangel och kombinerar
  former till en GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Gruppera former i Word med DocumentBuilder – komplett C#‑exempel
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man grupperar former i Word med DocumentBuilder – steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i Word med DocumentBuilder – steg‑för‑steg‑guide

Om du behöver **gruppera former i Word** programatiskt, visar den här handledningen en komplett lösning i C#. Du kommer att se hur du **skapar ett tomt Word‑dokument**, använder **DocumentBuilder**, och **infogar en rektangel‑form** innan du grupperar den med en ellips. Resultatet är en enda `GroupShape` som du kan flytta, ändra storlek eller formatera som ett objekt.

Denna guide täcker allt du behöver veta för att generera ett Word‑dokument med grupperade grafikobjekt med hjälp av Aspose.Words för .NET‑biblioteket. I slutet av artikeln har du ett körbart projekt som producerar `GroupedShapes.docx` som innehåller en rektangel och en ellips kombinerade till en enda form.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7.2+)
- Aspose.Words for .NET NuGet‑paket (`Aspose.Words`) – version 23.12 eller nyare
- En C#‑IDE såsom Visual Studio 2022 eller Visual Studio Code
- Grundläggande kunskap om C#‑syntax och objekt‑orienterad programmering

> **Proffstips:** Installera NuGet‑paketet från kommandoraden för att hålla ditt projekt snyggt:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Steg 1: Skapa ett tomt Word‑dokument

Den första operationen är att instansiera ett `Document`‑objekt, som representerar en tom Word‑fil, och en `DocumentBuilder` som låter dig lägga till innehåll.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Varför detta är viktigt:** `Document` tillhandahåller filbehållaren, medan `DocumentBuilder` erbjuder ett flytande API för att infoga text, bilder och former. Utan en `DocumentBuilder` skulle du behöva manipulera dokumentets nodträd manuellt, vilket är felbenäget.

## Steg 2: Infoga en rektangel‑form

En rektangel är ett vanligt byggblock för diagram. Använd `InsertShape` med `ShapeType.Rectangle` och specificera bredd och höjd i punkter (1 pt ≈ 1/72 tum).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Varför detta är viktigt:** Genom att sätta `Left` och `Top` positioneras rektangeln exakt på sidan, vilket är avgörande när du senare grupperar den med andra former. Metoden `InsertShape` lägger automatiskt till formen i det aktuella stycket.

## Steg 3: Infoga en ellips‑form

Lägg sedan till en ellips som kommer att ligga bredvid rektangeln.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Varför detta är viktigt:** Att använda en annan `ShapeType` visar hur samma `DocumentBuilder`‑API kan skapa varierad grafik. Genom att placera ellipsen så att den överlappar rektangeln blir grupperingseffekten tydlig.

## Steg 4: Gruppera de två formerna

En `GroupShape` fungerar som en behållare. Genom att lägga till rektangeln och ellipsen som barn, beter de sig som ett enda objekt.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Varför detta är viktigt:** `Bounds`‑egenskapen talar om för Word var gruppen sitter på sidan. Genom att lägga till barnformerna bevarar du deras individuella formatering samtidigt som du möjliggör gemensamma transformationer (flytta, rotera, ändra storlek).

## Steg 5: Spara dokumentet

Slutligen skriv dokumentet till disk. Du kan ändra sökvägen till vilken mapp du föredrar.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

När du öppnar `GroupedShapes.docx` i Microsoft Word kommer du att se en rektangel och en ellips grupperade tillsammans. Att markera gruppen markerar båda formerna, så att du kan dra eller ändra storlek på dem som en enhet.

### Förväntat resultat

- En Word‑fil med namnet **GroupedShapes.docx**
- Första sidan innehåller en **rektangel** (100 pt × 50 pt) på position (50, 50)
- En **ellips** (80 pt × 80 pt) på position (200, 70)
- Båda formerna är en del av en **GroupShape** med en omgivningsruta på 300 pt × 200 pt

## Vanliga variationer och kantfall

| Scenario | Adjustment |
|----------|------------|
| **Olika sidstorlek** | Använd `document.Sections[0].PageSetup.PageWidth` och `PageHeight` innan du infogar former. |
| **Fler än två former** | Skapa ytterligare `Shape`‑objekt och anropa `groupShape.AppendChild(newShape)` för varje. |
| **Applicera fyllningsfärg** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Rotera gruppen** | `groupShape.Rotation = 45;` (degrees) |
| **Exportera till PDF** | After saving the DOCX, call `document.Save("GroupedShapes.pdf");` |

## Fullständig källkod (klar att köra)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kopiera koden till ett nytt konsolprojekt, återställ Aspose.Words‑NuGet‑paketet och kör. Konsolen kommer att bekräfta filens plats, och när du öppnar filen visas den grupperade grafiken.

## Slutsats

Du vet nu **hur man grupperar former i Word** med Aspose.Words `DocumentBuilder`. Handledningen gick igenom att skapa ett **tomt Word‑dokument**, **infoga en rektangel‑form**, lägga till en ellips och kombinera dem till en `GroupShape`. Med detta fundament kan du bygga rikare diagram, flödesscheman eller anpassad grafik direkt från C#.

### Vad blir nästa?

- Utforska **how to use DocumentBuilder** för tabeller, sidhuvuden och sidfötter.
- Kombinera **insert rectangle shape Word**‑tekniker med textrutor för annoterade diagram.
- Använd **create blank word doc** som en mall för automatiserad rapportgenerering.

Känn dig fri att experimentera med färger, gradienter och ytterligare former. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Infoga former i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Skapa rektangel‑form i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}