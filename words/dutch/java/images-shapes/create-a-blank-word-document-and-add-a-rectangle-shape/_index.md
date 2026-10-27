---
category: general
date: 2026-10-23
description: Maak een leeg Word‑document, voeg een rechthoekvorm toe en verberg de
  vorm in Word met Aspose.Words. Stap‑voor‑stap code voor .NET‑ontwikkelaars.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: nl
lastmod: 2026-10-23
og_description: Maak een leeg Word‑document, voeg een rechthoekvorm toe en verberg
  de vorm in Word met Aspose.Words. Volg het volledige C#‑voorbeeld.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Maak een leeg Word‑document en voeg een verborgen rechthoekvorm toe
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Maak een leeg Word-document en voeg een rechthoekvorm toe
url: /nl/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en voeg een rechthoekvorm toe

Als je een **leeg Word‑document wilt maken**, laat deze gids je zien hoe je dat doet met Aspose.Words for .NET. Je leert ook **hoe je een vorm kunt invoegen**—specifiek een rechthoek—en **een vorm verbergen in Word** zodat deze de lay-out niet beïnvloedt.

De tutorial loopt door elke regel code, legt uit waarom elke stap belangrijk is, en behandelt veelvoorkomende valkuilen zoals de zichtbaarheid van verborgen vormen in verschillende weergavemodi van Word. Aan het einde heb je een volledig functioneel `.docx`‑bestand dat een verborgen rechthoekvorm bevat die je later kunt onthullen of programmatisch kunt manipuleren.

## Voorvereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
- Een ontwikkelomgeving zoals Visual Studio 2022 of VS Code met C#‑extensies
- Basiskennis van C#‑syntaxis en Word‑documentconcepten

Er is geen extra Office‑installatie vereist omdat Aspose.Words volledig in het geheugen werkt.

## Maak een leeg Word‑document

De eerste stap is om een lege `Document`‑object te instantieren. Dit object vertegenwoordigt een Word‑bestand dat nog geen secties, alinea's of inhoud bevat.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Waarom dit belangrijk is:**  
Een lege `Document` geeft je een schoon canvas. Als je begint vanuit een bestaand sjabloon, kunnen verborgen vormen ongewenste stijlen overnemen. Beginnen vanaf nul zorgt ervoor dat de rechthoekvorm die je later toevoegt de enige inhoud is die je beheert.

## Voeg een rechthoekvorm toe aan het document

Vervolgens hebben we een `DocumentBuilder` nodig om inhoud in het document te plaatsen. De `InsertShape`‑methode van de builder is de standaard manier **om vormobjecten in te voegen**, zoals rechthoeken, cirkels of aangepaste tekeningen.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Waarom dit belangrijk is:**  
`InsertShape` retourneert een `Shape`‑object dat je verder kunt configureren (kleur, lijntype, enz.). De afmetingen worden opgegeven in points (1 point = 1/72 inch), wat overeenkomt met het interne meetsysteem van Word.

### Optioneel: stijl de rechthoek (optioneel)

Als je wilt dat de rechthoek een zichtbare rand heeft wanneer je deze later zichtbaar maakt, kun je de lijndikte en kleur instellen:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Deze regels zijn optioneel omdat de vorm in de volgende stap wordt verborgen.

## Verberg de vorm in Word

Word staat toe dat vormen verborgen worden in de lay-out terwijl ze nog steeds deel uitmaken van het objectmodel van het document. Het instellen van de `Hidden`‑eigenschap op `true` maakt de vorm onzichtbaar in de normale weergave, maar nog wel selecteerbaar via de API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Waarom dit belangrijk is:**  
Een verborgen vorm is handig voor het opslaan van metadata, tijdelijke aanduidingen voor latere verwerking, of conditionele inhoud die je alleen onder bepaalde omstandigheden onthult (bijv. bij het genereren van een eindrapport). De vorm blijft in het bestand, zodat je deze later programmatisch kunt onthullen met `rectangleShape.Hidden = false;`.

## Sla het document op

Schrijf tenslotte het document naar schijf. De bestandsextensie bepaalt het Word‑formaat; `.docx` is het moderne Open XML‑formaat.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Resultaat:**  
Het openen van `HiddenShape.docx` in Microsoft Word toont een verder lege pagina. De rechthoek is niet zichtbaar, maar als je naar **Start → Selecteren → Selectiepaneel** gaat, zie je de vorm vermeld staan en kun je de zichtbaarheid toggelen.

## Volledig werkend voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren, plakken en uitvoeren. Het bevat alle benodigde `using`‑statements en commentaren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Verwachte output:**  

- De console geeft het opslagpad weer.  
- `HiddenShape.docx` opent als een lege pagina in Word.  
- De rechthoekvorm bestaat, maar is verborgen; je kunt dit verifiëren via het *Selectiepaneel* of door programmatisch `Hidden = false` in te stellen en het bestand opnieuw te openen.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik andere vormtypen verbergen?** | Ja. Elke `Shape` (bijv. `ShapeType.Ellipse`, `ShapeType.Picture`) ondersteunt de `Hidden`‑eigenschap. |
| **Verhoogt de verborgen vorm de bestandsgrootte?** | De toename is verwaarloosbaar (enkele kilobytes) omdat de vormgegevens als XML in het `.docx`‑pakket worden opgeslagen. |
| **Wat als ik wil dat de vorm alleen in de afdrukweergave verschijnt?** | Gebruik de `Shape.IsPrint`‑eigenschap in plaats van `Hidden`. Het instellen van `IsPrint = false` verbergt de vorm in de afgedrukte output, maar houdt deze zichtbaar op het scherm. |
| **Hoe de vorm later weer zichtbaar maken?** | Laad het document, zoek de vorm (bijv. via `Shape.Name`), stel vervolgens `shape.Hidden = false;` in en sla op. |
| **Werkt dit met .doc (binair) formaat?** | Ja, Aspose.Words kan opslaan naar `.doc` met `document.Save("file.doc");`. De verborgen vlag wordt behouden. |

## Pro‑tips

- **Geef je vormen een naam**: `rectangleShape.Name = "PlaceholderRectangle";` maakt het later makkelijker om ze te vinden via `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Batchverwerking**: Als je verborgen vormen aan veel documenten moet toevoegen, verpak de code in een methode en hergebruik de `DocumentBuilder`‑instantie.
- **Prestaties**: Het maken van een vorm is goedkoop, maar het vaak opslaan van grote documenten kan I/O‑gebonden zijn. Overweeg `MemoryStream` voor tussentijdse verwerking.

## Conclusie

Je weet nu hoe je **een leeg Word‑document maakt**, **een rechthoekvorm toevoegt**, en **een vorm verbergt in Word** met Aspose.Words for .NET. Deze techniek stelt je in staat onzichtbare placeholders in te sluiten die je later kunt onthullen of manipuleren, een patroon dat nuttig is voor dynamische rapportgeneratie, conditionele inhoud en document‑templating.

Volgende stappen die je kunt verkennen:

- Vervang de rechthoek door een afbeelding of grafiek met `ShapeType.Picture`.
- Gebruik **how to insert shape** in header/footer‑secties voor watermerk‑achtige placeholders.
- Combineer verborgen vormen met **add rectangle shape**‑gebaseerde gegevensvalidatie (bijv. JSON opslaan in de `AlternativeText`‑eigenschap van een vorm).

Veel programmeerplezier, en voel je vrij om met andere vormtypen en zichtbaarheidopties te experimenteren om aan je document‑automatiseringsbehoeften te voldoen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word‑document maken – Hoe een rechthoekvorm en schaduw toe te voegen](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Groepvorm maken in Word‑document met Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeg Word‑document maken met een verborgen ellipsvorm – volledige C#‑gids](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}