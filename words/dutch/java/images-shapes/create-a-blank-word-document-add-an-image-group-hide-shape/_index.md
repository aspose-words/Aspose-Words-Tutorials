---
category: general
date: 2026-10-10
description: Maak een leeg Word‑document, voeg een afbeelding in Word in, voeg een
  afbeeldingsgroep toe en verberg de vorm in het opgeslagen bestand. Volg deze stapsgewijze
  handleiding.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: nl
lastmod: 2026-10-10
og_description: Maak een leeg Word‑document, voeg een afbeelding toe aan Word, voeg
  een afbeeldingengroep toe en verberg de vorm. Deze gids toont de volledige C#‑code.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Maak een leeg Word‑document, voeg een afbeeldingengroep toe, verberg vorm
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Maak een leeg Word‑document, voeg een afbeeldingengroep toe, verberg de vorm
url: /nl/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document, voeg een afbeeldingsgroep toe, verberg vorm

Als je een **leeg Word‑document wilt maken** en later visuele elementen wilt verbergen, laat deze tutorial je precies zien hoe. Je leert een afbeelding in Word in te voegen, een afbeeldingsgroep toe te voegen en een vorm in een Word‑document te verbergen met een enkele, herbruikbare C#‑routine.

We gebruiken de Aspose.Words for .NET‑bibliotheek, waarmee je .docx‑bestanden kunt manipuleren zonder Microsoft Word geïnstalleerd te hebben. Aan het einde van deze gids heb je een uitvoerbaar programma dat een Word‑bestand produceert met een verborgen afbeeldingsgroep, klaar voor downstream‑verwerking of voorwaardelijke weergave.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
- Een map op schijf waar je een afbeeldingsbestand kunt lezen en het uitvoerdocument kunt wegschrijven
- Basiskennis van C# en Visual Studio (of een andere IDE naar keuze)

## Maak een leeg Word‑document met Aspose.Words

De eerste stap is om een **leeg Word‑document te maken**. Aspose.Words levert de `Document`‑klasse die een Word‑bestand in het geheugen representeert. Een instantie zonder argumenten geeft je een leeg document klaar voor inhoud.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is:* Beginnen met een leeg document zorgt ervoor dat er geen verborgen opmaak of overgebleven secties zijn die later de vorm die je toevoegt kunnen beïnvloeden.

## Afbeelding invoegen in Word met DocumentBuilder

Vervolgens **voegen we een afbeelding in Word in** door eerst een groepsvorm te maken die de afbeelding bevat. Groepsvormen laten je meerdere tekenobjecten als één eenheid behandelen, wat handig is wanneer je ze later samen wilt verbergen of verplaatsen.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

De methode `InsertGroupShape` maakt een lege container. De afmetingen zijn in points (1 point = 1/72 inch). Pas de grootte aan zodat deze overeenkomt met de resolutie van de afbeelding die je wilt insluiten.

## Voeg afbeeldingsgroep toe aan het document

Nu **voegen we de afbeeldingsgroep toe** door de cursor van de builder binnen de nieuw gemaakte groep te plaatsen en de afbeelding in te voegen. Alle volgende invoegacties maken deel uit van de groep.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Tip:* Gebruik een absoluut of correct ge‑escaped relatief pad; anders gooit `InsertImage` een `FileNotFoundException`.

## Vorm verbergen in een Word‑document

Tot slot **verbergen we de vorm in het Word‑document** door de eigenschap `Hidden` van de groep op `true` te zetten. Verborgen vormen worden niet weergegeven wanneer het document in Word wordt geopend, maar blijven wel in het bestand en kunnen later programmatisch worden onthuld.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Wanneer je *GroupHidden.docx* opent in Microsoft Word, zie je een volledig lege pagina omdat de afbeeldingsgroep verborgen is. Het bestand bevat nog steeds de afbeeldingsdata, die je later kunt onthullen met `group.Hidden = false` indien nodig.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren‑plakken in een nieuw console‑project:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Verwachte output**

- Een bestand genaamd `GroupHidden.docx` verschijnt in `YOUR_DIRECTORY`.
- Het openen van het bestand in Word toont een lege pagina.
- De verborgen afbeelding kan worden onthuld door `group.Hidden = false` te wijzigen en opnieuw op te slaan.

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe de code aan te passen |
|-----------|---------------------------|
| **Meerdere afbeeldingen** | Voeg extra `InsertImage`‑aanroepen toe na `builder.MoveTo(group)`. Alle afbeeldingen blijven binnen dezelfde groep en delen de verborgen‑vlag. |
| **Verschillende afbeeldingsformaten** | Aspose.Words ondersteunt PNG, JPEG, BMP, GIF, TIFF. Verander alleen de bestandsextensie; er is geen code‑wijziging nodig. |
| **Voorwaardelijke zichtbaarheid** | Sla een aangepaste documentvariabele op (`doc.Variables.Add("ShowImages", "true")`) en schakel `group.Hidden` op basis van de waarde tijdens runtime. |
| **Grote documenten** | Maak de groep op een specifieke pagina (`builder.InsertBreak(BreakType.PageBreak)`) voordat je de groep invoegt om lay‑outverschuivingen te voorkomen. |
| **Compatibiliteit met oudere Word‑versies** | Sla op als `doc.Save("output.doc", SaveFormat.Doc)` als je het legacy `.doc`‑formaat nodig hebt; verborgen vormen gedragen zich op dezelfde manier. |

**Pro tip:** Stel `group.Hidden = true` altijd *na* het invoegen van elk kind‑element in. Het wijzigen van de vlag vóór het toevoegen van inhoud kan ervoor zorgen dat sommige elementen onverwacht worden gerenderd in oudere Word‑versies.

## Conclusie

Je weet nu hoe je **een leeg Word‑document maakt**, **een afbeelding in Word invoegt**, **een afbeeldingsgroep toevoegt** en **een vorm in een Word‑document verbergt** met Aspose.Words for .NET. Het volledige voorbeeld toont elke stap, van het initialiseren van het document tot het opslaan van een bestand dat een verborgen afbeeldingsgroep bevat.

Vervolgens kun je verkennen:

- Tekstvakken of grafieken toevoegen aan dezelfde groep
- `DocumentBuilder.StartBookmark` / `EndBookmark` gebruiken om verborgen secties te markeren
- Programma‑matig de zichtbaarheid toggelen op basis van gebruikersinvoer of documentvariabelen

Voel je vrij om te experimenteren met verschillende vormen, groottes en zichtbaarheidsregels om ze aan jouw automatiseringsscenario aan te passen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}