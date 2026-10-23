---
category: general
date: 2026-10-23
description: Leer hoe je een ellips invoegt en hoe je een rechthoekvorm toevoegt in
  Word met Aspose.Words. Inclusief het verplaatsen van de cursor naar de vorm en hoe
  je een groepsvorm maakt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: nl
lastmod: 2026-10-23
og_description: Hoe een ellips in te voegen en hoe een rechthoekvorm toe te voegen
  in Word met Aspose.Words. Volg de stapsgewijze handleiding om de cursor naar de
  vorm te verplaatsen en een groepsvorm te maken.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Hoe ellips- en rechthoekvormen in een Word‑groepsvorm invoegen
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe ellips- en rechthoekvormen binnen een groepsvorm in te voegen met Aspose.Words
url: /nl/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe ellips- en rechthoekvormen in een groepsvorm in te voegen met Aspose.Words

Als je wilt weten **hoe je een ellips kunt invoegen** in een Word‑document via code, laat deze gids het volledige proces zien. Je ziet ook **hoe je een rechthoekvorm kunt toevoegen**, leert **de cursor naar een vorm te verplaatsen**, en ontdekt **hoe je een groepsvorm kunt maken** die meerdere tekenobjecten bevat.

Word‑automatisering vereist vaak een precieze positionering van tekenobjecten. Aan het einde van deze tutorial kun je een `.docx`‑bestand genereren dat een gegroepeerde rechthoek en ellips bevat, klaar voor verdere styling of export. Er zijn geen externe tools nodig, behalve de Aspose.Words for .NET‑bibliotheek en een .NET‑ontwikkelomgeving.

## Vereisten

* .NET 6.0 of later geïnstalleerd.
* Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`) toegevoegd aan je project.
* Basiskennis van C#‑syntaxis en Visual Studio (of een andere IDE).

Deze vereisten zorgen ervoor dat de code compileert zonder extra configuratie.

## Hoe een groepsvorm in Word te maken

Een groepsvorm fungeert als een container waarmee je meerdere vormen als één geheel kunt verplaatsen, roteren of opmaken. De volgende code maakt een groep met een specifieke grootte (300 × 200 punten) en bereidt het document voor op verdere tekenbewerkingen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Waarom deze stap belangrijk is*: De groepsvorm definieert een lokaal coördinatensysteem. Alle vormen die worden toegevoegd nadat de cursor naar de groep is verplaatst, worden gepositioneerd ten opzichte van de oorsprong van de groep, waardoor lay‑outberekeningen eenvoudig zijn.

## Hoe een rechthoekvorm toe te voegen in Word

Nu de groep bestaat, kun je **een rechthoekvorm invoegen** erin. De rechthoek dient als achtergrond of als visuele placeholder voor andere inhoud.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Uitleg*: `MoveTo(group)` vertelt de builder dat het actieve invoegpunt de groepsvorm is. Zonder de cursor te verplaatsen, zou `InsertShape` de rechthoek aan de hoofd‑documentbody toevoegen in plaats van aan de groep.

## Hoe een ellips in te voegen

Met de rechthoek op zijn plaats kun je nu laten zien **hoe je een ellips kunt invoegen**. De ellips wordt gecentreerd binnen dezelfde groep en overlapt de rechthoek indien gewenst.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Waarom de cursor verplaatst moet worden*: Elke aanroep van `InsertShape` houdt rekening met de huidige cursorlocatie. Het opnieuw aanroepen van `MoveTo(group)` garandeert dat de ellips ook een kind van de groep is, waardoor de beoogde hiërarchie behouden blijft.

## Cursor naar vorm verplaatsen vóór het invoegen van extra objecten

Als je later meer vormen wilt toevoegen, **verplaats dan altijd de cursor naar de vorm** vóór elke invoeging. Dit patroon voorkomt per ongeluk plaatsen buiten de groep.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tip*: Het hergebruiken van `MoveTo(group)` is goedkoop en verbetert de leesbaarheid van de code. Het maakt ook toekomstig onderhoud eenvoudiger omdat de invoegcontext expliciet is.

## Document opslaan

Sla tot slot het document op schijf op. Het voorbeeld slaat het bestand op als `GroupShape.docx` in een map die je opgeeft.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Wanneer je het opgeslagen bestand opent in Microsoft Word, zie je één groep die een rechthoek en een ellips bevat, beide correct gepositioneerd.

### Verwachte output

* Een `.docx`‑bestand met de naam `GroupShape.docx`.
* In het document een gegroepeerd tekenobject met de afmeting 300 × 200 punten.
* Binnen de groep:
  * Een rechthoek (100 × 50 punten) geplaatst op de oorsprong van de groep.
  * Een ellips (80 × 80 punten) die de rechthoek overlapt.
  * Eventuele extra vormen die je na het verplaatsen van de cursor hebt toegevoegd.

## Veelvoorkomende variaties en randgevallen

| Situatie | Aanbevolen aanpak |
|----------|-------------------|
| **Verschillende eenheidsgroottes** | Aspose.Words gebruikt punten (1 pt = 1/72 in). Converteer centimeters of inches naar punten voordat je `InsertShape` aanroept. |
| **Vormen roteren binnen de groep** | Na het invoegen van een vorm, haal je het `ShapeBase`‑object op en stel je `ShapeBase.RotationAngle` in. |
| **Tekst toevoegen binnen een vorm** | Gebruik `ShapeBase.AppendChild(new Paragraph(document))` en voeg vervolgens een `Run` toe met de gewenste tekst. |
| **Opslaan als PDF in plaats van DOCX** | Roep `document.Save("GroupShape.pdf", SaveFormat.Pdf);` aan – de groepshiërarchie blijft behouden in de PDF‑output. |

Deze variaties tonen aan dat dezelfde **hoe je een ellips kunt invoegen**‑logica kan worden aangepast voor veel praktijksituaties.

## Pro‑tips

* **Herbruik dezelfde `DocumentBuilder`‑instantie** – dit vermindert het geheugenverbruik en houdt de documentstatus consistent.
* **Valideer vormafmetingen** – extreem grote breedtes of hoogtes kunnen weergaveproblemen veroorzaken in oudere Word‑versies.
* **Groeperen vóór styling** – het toepassen van vulkleuren of lijntypen op de groep nadat alle kinderen zijn toegevoegd, zorgt voor een uniforme uitstraling.

## Conclusie

Je begrijpt nu **hoe je een ellips kunt invoegen** en **hoe je een rechthoekvorm kunt toevoegen** binnen een gegroepeerde container in een Word‑document met Aspose.Words. Door consequent **de cursor naar de vorm te verplaatsen** vóór elke invoeging, behoud je een nette hiërarchie en voorkom je onbedoelde plaatsing. Het volledige voorbeeld compileert, draait en produceert een gegroepeerde vorm die verder kan worden aangepast of geëxporteerd.

Klaar om meer te ontdekken? Probeer deze techniek te combineren met **hoe je een groepsvorm maakt** voor complexe diagrammen, of experimenteer met **rechthoekvorm invoegen in Word** naast tekstvakken voor rijke rapportgeneratie. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [How to create blank Word document and add a hidden ellipse shape in C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [How to create group shape docx and add interactive controls in C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}