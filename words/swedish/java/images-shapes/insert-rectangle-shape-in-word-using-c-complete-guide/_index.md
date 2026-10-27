---
category: general
date: 2026-08-04
description: Infoga rektangelform i ett Word‑dokument med C#. Lär dig hur du grupperar
  former i Word, sparar dokumentet som docx och använder DocumentBuilder för avancerade
  layouter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: sv
lastmod: 2026-08-04
og_description: Infoga en rektangelform i en Word‑fil med C# och gruppera sedan former
  för avancerade layouter. Denna handledning täcker också hur man sparar dokumentet
  som docx och använder DocumentBuilder effektivt.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Infoga rektangel i Word – C# steg‑för‑steg guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Infoga rektangel i Word med C# – komplett guide
url: /sv/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga rektangelform i Word med C# – komplett guide

Om du behöver **infoga rektangelform** i ett Word‑dokument med C#, visar den här handledningen exakt hur du gör. Du får också lära dig **hur du grupperar former** i Word, **spara dokument som docx**, och **hur du använder Builder** för ren, underhållbar kod.

Att arbeta med former är ett vanligt krav när man genererar rapporter, certifikat eller anpassade layouter programmässigt. I slutet av den här guiden har du ett fullt körbart exempel som skapar en rektangel, lägger till en ellips, grupperar dem och sparar resultatet som en DOCX‑fil.

## Förutsättningar

* .NET 6.0 eller senare installerat  
* Visual Studio 2022 (eller någon IDE som stödjer C#)  
* **Aspose.Words for .NET**‑biblioteket (tillgängligt via NuGet)  

Du kan lägga till biblioteket med följande kommando:

```bash
dotnet add package Aspose.Words
```

## Infoga rektangelform med DocumentBuilder

Det första steget är att skapa ett nytt `Document` och en `DocumentBuilder`. Buildern ger dig ett flytande API för att infoga innehåll, inklusive former.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder`‑instansen är kärnobjektet du kommer att använda för att **infoga rektangelform** och andra element. Den spårar den aktuella markörpositionen i dokumentet, så varje infogning sker exakt där du behöver den.

## Hur man infogar en rektangelform

När buildern är klar, anropa `InsertShape`. Du anger `ShapeType`, bredd och höjd i punkter (1 pt ≈ 1/72 tum).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Varför detta är viktigt*: Att sätta `FillColor` och `StrokeColor` gör rektangeln visuellt distinkt, vilket hjälper när du senare grupperar den med andra former.

## Hur man grupperar former i Word

Att gruppera former låter dig flytta, rotera eller formatera flera objekt som en enda enhet. Efter att ha infogat rektangeln, lägg till en annan form (en ellips i detta exempel) och skapa sedan en `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

`InsertGroupShape`‑anropet skapar en platshållare som kan hålla valfritt antal barnformer. Genom att lägga till rektangeln och ellipsen grupperar du effektivt **former i Word**. Gruppen beter sig som en enda form—du kan flytta den, applicera en kantlinje eller ändra storlek utan att påverka den interna layouten för varje barn.

### Pro tip

Efter gruppering kan du ändra gruppens position relativt sidan:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Spara dokument som docx

När formerna är placerade måste du spara filen. Metoden `Document.Save` bestämmer automatiskt formatet utifrån filändelsen. För att **spara dokument som docx**, ange en sökväg som slutar med `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

När programmet körs skapas `output.docx`. Öppna filen i Microsoft Word, så ser du en ljusblå rektangel och en ljuskorallfärgad ellips grupperade tillsammans. Du kan klicka på gruppen och flytta den som ett enda objekt.

## Hur man använder DocumentBuilder effektivt

`DocumentBuilder` är mer än en form‑infogare; den hanterar också text, tabeller, sidhuvuden och sidfötter. När du kombinerar formskapande med text, kom ihåg att återställa markören om du behöver infoga innehåll någon annanstans:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Att hålla builderns tillstånd explicit undviker oavsiktliga överskrivningar och gör koden enklare att underhålla.

## Kantfall och variationer

| Situation | Rekommenderad metod |
|-----------|----------------------|
| **Mer än två former** | Infoga varje form, anropa sedan `AppendChild` för varje form innan du sparar. |
| **Nästlade grupper** | Skapa en grupp, lägg till former, och infoga sedan den gruppen i en annan `GroupShape`. |
| **Olika måttenheter** | Använd `builder.ConvertPixelsToPoints` om du har dimensioner i pixlar. |
| **Kompatibilitet med äldre Word‑versioner** | Spara som `.doc` genom att ändra filändelsen; de flesta formfunktioner fungerar fortfarande. |

## Komplett fungerande exempel

Nedan är hela programmet som du kan kopiera‑och‑klistra in i ett nytt konsolprojekt. Inga ytterligare kodsnuttar krävs.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Förväntat resultat**: När du öppnar `output.docx` visas en ljusblå rektangel och en ljuskorallfärgad ellips grupperade tillsammans, placerade 150 pt från vänstermarginalen och 100 pt från toppen. Bildtexten visas under gruppen.

## Slutsats

Du vet nu hur du **infogar rektangelform** i en Word‑fil med C#, **grupperar former i Word**, och **sparar dokument som docx** med Aspose.Words `DocumentBuilder`. Genom att behärska dessa steg kan du bygga komplexa layouter—certifikat, rapporter eller anpassade formulär—helt via kod.

Nästa steg är att utforska relaterade ämnen som **lägga till textrutor**, **arbeta med tabeller**, eller **exportera till PDF**. Var och en av dessa bygger på samma `DocumentBuilder`‑grundprinciper som du just har övat.

Redo att automatisera dina Word‑dokument? Prova att utöka exemplet med fler former, applicera gradienter eller loopa över data för att generera en fullständig rapport i ett enda körning. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Infoga former i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Skapa rektangelform i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}