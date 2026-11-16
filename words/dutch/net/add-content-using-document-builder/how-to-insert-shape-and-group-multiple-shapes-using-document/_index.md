---
category: general
date: 2026-11-15
description: Leer hoe u een vorm in een Word‑document invoegt en meerdere vormen groepeert
  met Aspose.Words DocumentBuilder. Inclusief voorbeelden voor het invoegen van een
  rechthoekige vorm en het invoegen van meerdere vormen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: nl
lastmod: 2026-11-15
og_description: Hoe een vorm in een Word‑bestand in te voegen met Aspose.Words. Deze
  gids behandelt het groeperen van meerdere vormen, het invoegen van een rechthoekvorm
  en het efficiënt toevoegen van meerdere vormen.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Hoe een vorm in te voegen en meerdere vormen te groeperen met DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Hoe een vorm in te voegen en meerdere vormen te groeperen met DocumentBuilder
  in C#
url: /nl/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een vorm in te voegen en meerdere vormen te groeperen met DocumentBuilder in C#

Als je wilt weten **hoe je een vorm kunt invoegen** in een Word‑document met Aspose.Words, laat deze gids je de exacte stappen zien. Je leert ook hoe je **meerdere vormen kunt groeperen** zodat ze zich als één object gedragen, en hoe je **een rechthoekvorm kunt invoegen** naast andere afbeeldingen.

Documentautomatisering vereist vaak het toevoegen van verschillende grafische elementen—grafieken, logo’s, call‑outs—terwijl je ze georganiseerd houdt. Aan het einde van deze tutorial kun je **meerdere vormen invoegen**, ze in een groep plaatsen en een nette, herbruikbare lay-out opslaan.

## Voorvereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 of later geïnstalleerd  
* Visual Studio 2022 (of een andere C#‑IDE)  
* Een Aspose.Words for .NET‑licentie of een gratis evaluatiesleutel  
* Basiskennis van C# en de Aspose.Words `DocumentBuilder`‑klasse  

Je hebt **geen** andere externe bibliotheken nodig; alles wat je nodig hebt maakt deel uit van Aspose.Words.

## Stap 1: Installeer Aspose.Words via NuGet

Open je project in Visual Studio en voer het volgende commando uit in de Package Manager Console:

```powershell
Install-Package Aspose.Words
```

Het pakket bevat de klassen `DocumentBuilder`, `Shape` en `GroupShape` die door de hele tutorial heen worden gebruikt.

## Stap 2: Maak een DocumentBuilder‑instantie – de basis voor **hoe je een vorm kunt invoegen**

De eerste werkbare regel code is het aanmaken van een `DocumentBuilder`. Dit object geeft je directe toegang tot de documentboom, waardoor je vormen precies kunt plaatsen waar je ze wilt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Waarom dit belangrijk is*: `DocumentBuilder` houdt een cursor bij (het “invoegpunt”). Elke daaropvolgende `Insert...`‑aanroep gebruikt die cursor, daarom verplaatsen we deze later naar een `GroupShape` om alle vormen samen te houden.

## Stap 3: **Rechthoekvorm invoegen** – de eerste grafiek die je toevoegt

Een rechthoek is een veelvoorkomende placeholder voor tabellen, afbeeldingen of call‑outs. Gebruik `InsertShape` met `ShapeType.Rectangle` en geef breedte en hoogte op in punten (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

De rechthoek verschijnt op de huidige cursorlocatie. Je kunt later de vulling, lijnstijl of tekst aanpassen indien nodig.

## Stap 4: Een andere vorm invoegen – een ellips voor visuele variatie

Meer dan één vorm toevoegen laat **meerdere vormen invoegen** zien. De ellips wordt na de rechthoek in de documentstroom geplaatst.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Op dit moment bevat het document twee onafhankelijke vormen. Als je de cursor verplaatst of tekst toevoegt, blijven de vormen op hun oorspronkelijke positie.

## Stap 5: **Meerdere vormen groeperen** zodat ze als één eenheid functioneren

Groeperen is essentieel wanneer je verschillende grafische elementen tegelijk wilt verplaatsen, roteren of opmaken. De onderstaande code maakt een `GroupShape`, verplaatst de cursor van de builder erin, en voegt vervolgens dezelfde vormen opnieuw in – dit keer worden ze kinderen van de groep.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Waarom een groep gebruiken?

* **Transformatie vanuit één punt** – roteer of schaaf de hele groep met één aanroep.  
* **Logische organisatie** – de Word‑documentboom weerspiegelt de groepering, waardoor latere bewerkingen eenvoudiger worden.  
* **Consistente lay-out** – het verplaatsen van de groep behoudt de relatieve posities van de onderliggende vormen.

### Meer vormen toevoegen – **meerdere vormen invoegen** uitbreiden binnen de groep

Je kunt blijven `InsertShape` aanroepen terwijl de cursor zich binnen de `GroupShape` bevindt. Bijvoorbeeld, om een driehoek toe te voegen:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Elke aanroep respecteert de groepscontext, zodat de driehoek automatisch deel uitmaakt van dezelfde gegroepeerde set.

## Stap 6: Sla het document op en controleer het resultaat

Nadat alle vormen zijn geplaatst, sla je het document op als een `.docx`‑bestand. Het openen van het bestand in Microsoft Word (of een andere compatibele viewer) moet twee afzonderlijke vormen tonen, gevolgd door een gegroepeerde set met dezelfde rechthoek, ellips en driehoek.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Verwachte output

* **Eerste twee vormen** – een rechthoek en een ellips die onafhankelijk op de pagina staan.  
* **Gegroepeerd blok** – een rechthoek, een ellips en een driehoek die samen bewegen wanneer je een van hen in Word aanklikt.

Je kunt de groepering testen door een willekeurige vorm binnen de groep te selecteren; Word markeert dan de volledige collectie, wat bevestigt dat de **meerdere vormen groeperen**‑operatie geslaagd is.

## Veelvoorkomende valkuilen en pro‑tips

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| Vormen verschijnen buiten de bedoelde pagina | De cursor van de builder is niet verplaatst naar de `GroupShape` vóór het invoegen. | Roep altijd `builder.MoveTo(group)` **voordat** je `InsertShape`‑aanroepen doet die tot de groep behoren. |
| Groep verdwijnt na opslaan | De groep werd ingevoegd zonder aan de node‑collectie van het document te worden toegevoegd. | Gebruik `builder.InsertNode(group)` direct na het aanmaken van de `GroupShape`. |
| Onverwachte grootte door document‑DPI | Aspose.Words werkt met punten; als je in pixels denkt, krijg je mismatches. | Converteer pixels naar punten (`points = pixels * 72 / 96`) of werk direct in punten. |
| Vormen overlappen onbedoeld | Er is geen expliciete positionering ingesteld; Word plaatst ze opeenvolgend. | Stel `Shape.Left` en `Shape.Top` in na het invoegen om exacte plaatsing te bepalen. |

**Pro tip:** Na het groeperen kun je de `Shapes`‑collectie van de groep (`group.Shapes`) ophalen om te itereren, hernoemen of bulk‑opmaak toe te passen.

## Stap 7: Het voorbeeld uitbreiden – wat nu?

Nu je **hoe je een vorm kunt invoegen**, **rechthoekvorm kunt invoegen** en **meerdere vormen kunt groeperen** kent, kun je het volgende verkennen:

* **Geanimeerde gegroepeerde vormen** – stel rotatie‑ of spiegel‑eigenschappen in op de groep.  
* **Stijlen toepassen** – gebruik `Shape.FillColor`, `Shape.LineFormat` of `Shape.TextBox` om labels toe te voegen.  
* **Exporteren naar PDF** – dezelfde gegroepeerde lay-out wordt correct gerenderd wanneer je `doc.Save("output.pdf")` aanroept.  

Al deze uitbreidingen maken gebruik van dezelfde `DocumentBuilder`‑workflow, waardoor je code schoon en onderhoudbaar blijft.

## Conclusie

Deze tutorial heeft laten zien **hoe je een vorm kunt invoegen** in een Word‑document met Aspose.Words, **hoe je een rechthoekvorm kunt invoegen**, en **hoe je meerdere vormen kunt groeperen** zodat ze zich als één object gedragen. Door de stap‑voor‑stap code te volgen, kun je betrouwbaar **meerdere vormen invoegen**, ze in groepen organiseren en professioneel ogende documenten programmatically genereren.

Voel je vrij om te experimenteren met verschillende vormtypen, kleuren en groeps‑transformaties. Wanneer je er klaar voor bent, integreer je dit patroon in grotere rapportage‑ of templating‑oplossingen om complexe documentlay-outs te automatiseren. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Vormen invoegen in Word‑documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Hoe ellips‑ en rechthoekvormen te maken en in te voegen binnen een groepsvorm in een Word‑document met Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Hoe vormen te groeperen in een Word‑document met Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}