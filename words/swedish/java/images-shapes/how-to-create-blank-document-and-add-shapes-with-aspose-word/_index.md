---
category: general
date: 2026-09-30
description: Skapa ett tomt dokument och infoga en rektangel, en ellips och gruppera
  flera former i C# med Aspose.Words. Lär dig hur du infogar former och hur du skapar
  en grupp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: sv
lastmod: 2026-09-30
og_description: Skapa ett tomt dokument i C# och lär dig hur du infogar former och
  grupperar flera former med Aspose.Words. Följ steg‑för‑steg‑handledningen.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Skapa ett tomt dokument och gruppera former i C# – Aspose.Words‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Hur man skapar ett tomt dokument och lägger till former med Aspose.Words i
  C#
url: /sv/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt dokument och lägger till former med Aspose.Words i C#

Om du behöver **skapa ett tomt dokument** och fylla det med grafik visar den här guiden exakt hur du gör. Du får se hur du **infogar en rektangel**, lägger till andra ritobjekt och sedan **grupperar flera former** så att de beter sig som en enhet.

Att arbeta med former är ett vanligt krav när man genererar kontrakt, certifikat eller anpassade rapporter. I den här handledningen lär du dig hela arbetsflödet, från att initiera dokumentet till att spara den slutliga filen, med hjälp av Aspose.Words‑API:t för .NET.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 (eller senare) SDK installerat  
* En giltig Aspose.Words för .NET‑licens (gratisprovversionen fungerar för detta exempel)  
* En IDE såsom Visual Studio 2022 eller Visual Studio Code  

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Hur man skapar ett tomt dokument och arbetar med former

Det första steget är att instansiera ett `Document`‑objekt. Detta objekt representerar Word‑filen i minnet och ger dig åtkomst till `DocumentBuilder`, som är det primära verktyget för att infoga innehåll.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Varför detta är viktigt:** Ett tomt dokument ger dig en ren canvas. `DocumentBuilder` behåller den aktuella infogningspunkten, så varje form du lägger till placeras automatiskt på rätt sida.

## Infoga rektangel och andra former

Nästa steg är att lägga till en rektangel och en ellips. Båda anropen använder samma `InsertShape`‑metod, vilket är det rekommenderade sättet **hur man infogar former** i Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Metoden `InsertShape` placerar automatiskt formen vid den aktuella markörpositionen.* Om du behöver exakt placering kan du justera `Shape.Left` och `Shape.Top` efter infogning.

## Gruppera flera former till ett enda objekt

Nu kombinerar vi rektangeln och ellipsen till en logisk enhet. Gruppering är användbart när du vill flytta eller ändra storlek på flera former samtidigt.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Hur detta fungerar:** `InsertGroupShape` skapar en behållare som beter sig som vilken annan `Shape` som helst. Genom att anropa `AppendChild` flyttar du de befintliga formerna in i behållaren, vilket automatiskt uppdaterar deras relativa koordinater.

### Praktiskt tips

Om du senare behöver **hur man skapar en grupp** programatiskt för fler än två former, upprepa helt enkelt `AppendChild` för varje ytterligare `Shape`‑instans. Gruppen kan innehålla vilket antal ritobjekt som helst, inklusive bilder, textrutor eller till och med andra grupper.

## Fullständigt exempel – hur man infogar former och sparar dokumentet

Nedan finns det kompletta, körbara programmet som demonstrerar varje steg som diskuterats hittills. När koden körs skapas en fil `ShapesDemo.docx` som innehåller en rektangel, en ellips och en grupperad form.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Förväntat resultat:** När du öppnar `ShapesDemo.docx` i Microsoft Word visas en enda sida med en blå rektangel, en grön ellips och en omgivande grå ram som representerar gruppen. När du flyttar gruppen flyttas båda formerna tillsammans, vilket bekräftar att **gruppera flera former**‑operationen lyckades.

## Vanliga frågor och hantering av kantfall

| Fråga | Svar |
|----------|--------|
| *Vad händer om jag behöver formerna på en specifik sida?* | Anropa `builder.MoveToDocumentEnd();` innan du infogar formerna, eller använd `builder.MoveToSection(sectionIndex);` för att rikta in dig på ett visst avsnitt. |
| *Kan jag lägga till text i en grupperad form?* | Ja. Skapa en `Shape` av typen `ShapeType.TextBox`, konfigurera dess text och `AppendChild` den sedan till `GroupShape`. |
| *Används punkter eller pixlar för formens dimensioner?* | Aspose.Words använder **punkter** (1 pt = 1/72 tum). Detta säkerställer konsekvent storlek över skrivare och skärmar. |
| *Hur ändrar man gruppens rotation?* | Sätt `groupShape.RotationAngle = 45;` (grader). Alla underordnade former roterar kring gruppens ursprung. |

## Slutsats

Du vet nu hur du **skapar ett tomt dokument**, **infogar en rektangel**, **hur man infogar former** som ellipser, och **grupperar flera former** till ett enda objekt med Aspose.Words för .NET. Det fullständiga kodexemplet visar den rekommenderade metoden, och tipsen ovan hjälper dig att anpassa lösningen till mer komplexa scenarier, såsom att lägga till textrutor eller rotera grupper.

Redo att utforska mer? Prova att lägga till en bildform i gruppen, experimentera med olika fyllningsfärger, eller generera en flersidig rapport där varje sida innehåller sitt eget grupperade diagram. Samma principer gäller, så du kan skala detta mönster till vilket dokument‑automatiseringsprojekt som helst.

## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}