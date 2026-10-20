---
category: general
date: 2026-08-04
description: Voeg een rechthoekvorm in een Word‑document in met C#. Leer hoe je vormen
  in Word groepeert, het document opslaat als docx, en DocumentBuilder gebruikt voor
  geavanceerde lay‑outs.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: nl
lastmod: 2026-08-04
og_description: Voeg een rechthoekvorm toe in een Word‑bestand met C# en groepeer
  vervolgens vormen voor geavanceerde lay‑outs. Deze tutorial behandelt ook het opslaan
  van het document als docx en het efficiënt gebruiken van DocumentBuilder.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Rechthoekvorm invoegen in Word – C# stapsgewijze handleiding
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
title: Rechthoekvorm invoegen in Word met C# – volledige gids
url: /nl/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm invoegen in Word met C# – volledige gids

Als je **een rechthoekvorm moet invoegen** in een Word‑document met C#, laat deze tutorial je precies zien hoe. Je leert ook **hoe je vormen groepeert** in Word, **een document opslaat als docx**, en **hoe je Builder gebruikt** voor nette, onderhoudbare code.

Het werken met vormen is een veelvoorkomende eis bij het programmatisch genereren van rapporten, certificaten of aangepaste lay‑outs. Aan het einde van deze gids heb je een volledig werkend voorbeeld dat een rechthoek maakt, een ellips toevoegt, ze groepeert en het resultaat opslaat als een DOCX‑bestand.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 of later geïnstalleerd  
* Visual Studio 2022 (of een IDE die C# ondersteunt)  
* De **Aspose.Words for .NET**‑bibliotheek (beschikbaar via NuGet)  

Je kunt de bibliotheek toevoegen met het volgende commando:

```bash
dotnet add package Aspose.Words
```

## Rechthoekvorm invoegen met DocumentBuilder

De eerste stap is het aanmaken van een nieuw `Document` en een `DocumentBuilder`. De builder biedt je een fluent API voor het invoegen van inhoud, inclusief vormen.

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

De `DocumentBuilder`‑instantie is het kernobject dat je gebruikt om **een rechthoekvorm in te voegen** en andere elementen. Het houdt de huidige cursorpositie in het document bij, zodat elke invoeging precies gebeurt waar je het nodig hebt.

## Hoe een rechthoekvorm in te voegen

Met de builder klaar, roep je `InsertShape` aan. Je specificeert het `ShapeType`, de breedte en de hoogte in points (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Waarom dit belangrijk is*: Het instellen van `FillColor` en `StrokeColor` maakt de rechthoek visueel onderscheidend, wat helpt wanneer je later de vorm groepeert met andere vormen.

## Hoe vormen te groeperen in Word

Vormen groeperen stelt je in staat om meerdere objecten als één entiteit te verplaatsen, roteren of op te maken. Na het invoegen van de rechthoek, voeg je een andere vorm toe (een ellips in dit voorbeeld) en maak je vervolgens een `GroupShape`.

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

De `InsertGroupShape`‑aanroep maakt een placeholder die een willekeurig aantal kindvormen kan bevatten. Door de rechthoek en ellips toe te voegen, **groepeer je vormen in Word**. De groep gedraagt zich als één vorm—je kunt hem verplaatsen, een rand toepassen of de grootte wijzigen zonder de interne lay‑out van elk kind te beïnvloeden.

### Pro tip

Na het groeperen kun je de positie van de groep ten opzichte van de pagina wijzigen:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Document opslaan als docx

Zodra de vormen zijn gerangschikt, moet je het bestand bewaren. De `Document.Save`‑methode bepaalt automatisch het formaat aan de hand van de bestandsextensie. Om **een document op te slaan als docx**, geef je een pad op dat eindigt op `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Het uitvoeren van het programma maakt `output.docx`. Open het bestand in Microsoft Word, en je ziet een lichtblauwe rechthoek en een lichtkoraalrode ellips gegroepeerd. Je kunt de groep aanklikken en als één object verplaatsen.

## DocumentBuilder effectief gebruiken

`DocumentBuilder` is meer dan een vorminvoeger; het behandelt ook tekst, tabellen, kop‑ en voetteksten. Wanneer je vormcreatie combineert met tekst, vergeet dan niet de cursor te resetten als je inhoud op een andere plek wilt invoegen:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

De expliciete staat van de builder voorkomt onbedoelde overschrijvingen en maakt de code makkelijker te onderhouden.

## Randgevallen en variaties

| Situatie | Aanbevolen aanpak |
|-----------|-------------------|
| **Meer dan twee vormen** | Voeg elke vorm in, roep daarna `AppendChild` aan voor elke vorm voordat je opslaat. |
| **Geneste groepen** | Maak een groep, voeg vormen toe, en voeg die groep vervolgens in een andere `GroupShape` in. |
| **Verschillende meeteenheden** | Gebruik `builder.ConvertPixelsToPoints` als je afmetingen in pixels hebt. |
| **Compatibiliteit met oudere Word‑versies** | Sla op als `.doc` door de extensie te wijzigen; de meeste vormfuncties werken nog steeds. |

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een nieuw console‑project. Er zijn geen extra fragmenten nodig.

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

**Verwacht resultaat**: Het openen van `output.docx` toont een lichtblauwe rechthoek en een lichtkoraalrode ellips gegroepeerd, gepositioneerd 150 pt vanaf de linkermarge en 100 pt vanaf de bovenkant. Het bijschrift verschijnt onder de groep.

## Conclusie

Je weet nu hoe je **een rechthoekvorm invoegt** in een Word‑bestand met C#, **hoe je vormen groepeert in Word**, en **hoe je een document opslaat als docx** met de Aspose.Words `DocumentBuilder`. Door deze stappen te beheersen kun je complexe lay‑-outs bouwen—certificaten, rapporten of aangepaste formulieren—volledig via code.

Verken vervolgens gerelateerde onderwerpen zoals **tekstvakken toevoegen**, **werken met tabellen**, of **exporteren naar PDF**. Elk van deze bouwt voort op dezelfde `DocumentBuilder`‑fundamenten die je zojuist hebt geoefend.

Klaar om je Word‑documenten te automatiseren? Probeer het voorbeeld uit te breiden met meer vormen, het toepassen van verlopen, of een lus over gegevens om in één run een volledig rapport te genereren. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}