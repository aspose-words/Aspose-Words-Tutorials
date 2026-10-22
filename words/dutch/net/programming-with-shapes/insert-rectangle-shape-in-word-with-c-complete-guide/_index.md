---
category: general
date: 2026-08-10
description: Voeg een rechthoekvorm in Word in met C#. Leer hoe je een vorm verbergt,
  een vorm in Word verbergt, en een verborgen vorm maakt met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: nl
lastmod: 2026-08-10
og_description: Invoegen van een rechthoekvorm in Word met C#. Deze tutorial legt
  uit hoe je een vorm verbergt, een vorm in Word verbergt, en een verborgen vorm maakt
  met volledige codevoorbeelden.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Rechthoekvorm invoegen in Word met C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Rechthoekvorm invoegen in Word met C# – volledige gids
url: /nl/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm invoegen in Word met C# – volledige gids

Als je een **rectangle shape** in een Word‑document wilt **invoegen** met C#, laat deze gids je de exacte stappen zien. Je leert ook **hoe je een shape verbergt** zodat deze niet verschijnt in het uiteindelijke bestand, wat antwoord geeft op de veelgestelde vraag **hide shape in Word** en laat zien hoe je programmatically een **create hidden shape** kunt maken.

De tutorial behandelt alles, van het opzetten van de Aspose.Words SDK tot het verifiëren dat de shape verborgen is. Aan het einde van het artikel heb je een herbruikbaar code‑fragment dat je in elk .NET‑project kunt gebruiken.

## Vereisten

Voordat je begint, zorg ervoor dat je het volgende hebt:

- .NET 6.0 of later geïnstalleerd (de code werkt ook met .NET Framework 4.6+)
- Een geldige Aspose.Words for .NET‑licentie of een tijdelijke evaluatiesleutel
- Visual Studio 2022 (of een andere IDE die C# ondersteunt)
- Basiskennis van C#‑syntaxis en het Document Object Model (DOM) van Word‑bestanden

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Stap 1: Maak een nieuw leeg document en een DocumentBuilder

De eerste handeling is het instantieren van een `Document`‑object. De `DocumentBuilder` biedt een handige API voor het invoegen van inhoud zoals shapes, alinea’s en tabellen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Waarom dit belangrijk is:** `Document` vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` een cursor bijhoudt die aangeeft waar het volgende element wordt geplaatst. Het initialiseren van beide objecten vormt de basis voor elke Word‑automatiseringstaak.

## Stap 2: Rechthoekvorm invoegen

Nu voeg je de rechthoek in. De `InsertShape`‑methode vereist het shape‑type en de afmetingen in points (1 point ≈ 1/72 inch). Een grootte van **200 × 100 points** levert een rechthoek op van ongeveer 2,78 × 1,39 inch.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Waarom dit belangrijk is:** Het `Shape`‑object dat je ontvangt is volledig configureerbaar—kleur, rand, tekst en zichtbaarheid kunnen allemaal worden aangepast voordat het document wordt opgeslagen.

## Stap 3: De shape verbergen

Om te voorkomen dat de rechthoek wordt weergegeven of afgedrukt, stel je de eigenschap `Hidden` in op `true`. Deze eigenschap correspondeert direct met het Word‑attribuut “Hidden”, dat Word respecteert in zowel weergave‑ als afdrukmodus.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Waarom dit belangrijk is:** Het instellen van `Hidden` is de standaardmethode om **hide shape in Word** te realiseren zonder de shape uit de documentstructuur te verwijderen. De shape blijft toegankelijk voor code, waardoor latere manipulaties zoals conditionele opmaak of data‑gedreven zichtbaarheidstoetsen mogelijk zijn.

## Stap 4: Het document opslaan

Sla tenslotte het document op schijf op. Kies elke map die je wilt; het voorbeeld gebruikt een tijdelijke pad dat je moet vervangen door een echt pad.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Waarom dit belangrijk is:** Opslaan finaliseert het bestand en schrijft de verborgen‑vlag naar de onderliggende Open XML. Wanneer je het document opent in Microsoft Word, zal de rechthoek onzichtbaar zijn, wat bevestigt dat je succesvol een **create hidden shape** hebt gemaakt.

## Stap 5: Controleer de verborgen shape

Open het gegenereerde `HiddenShape.docx` in Microsoft Word:

1. Ga naar **Bestand → Opties → Weergave** en zorg dat *“Verborgen tekst weergeven”* **uitgeschakeld** is.  
2. De rechthoek mag op geen enkele pagina zichtbaar zijn.  
3. Om dubbel te controleren, schakel *“Verborgen tekst weergeven”* in; de rechthoek verschijnt met een zwakke gestippelde omtrek, wat bewijst dat de shape bestaat maar verborgen is.

Als de rechthoek nog steeds zichtbaar is, controleer dan of je het bestand hebt opgeslagen nadat je `Hidden = true` hebt ingesteld en of je het juiste bestand opent.

## Volledig uitvoerbaar voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren, plakken en direct kunt uitvoeren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Verwachte output:** De console drukt het bestandspad en een korte herinnering af. Wanneer het bestand in Word wordt geopend, is de rechthoek onzichtbaar tenzij verborgen tekst is ingeschakeld.

## Veelgestelde vragen en randgevallen

### Kan ik alleen de omtrek verbergen maar de vulling zichtbaar houden?

Ja. In plaats van `Hidden = true` kun je `rectangle.LineFormat.Visible = false` instellen om de rand te verbergen terwijl de vulkleur behouden blijft. Dit is een variant van **how to hide shape** die een deel van de visuele weergave behoudt.

### Werkt de verborgen‑vlag in oudere Word‑versies (2003, 2007)?

Het verborgen‑attribuut maakt deel uit van de Open XML‑specificatie die werd geïntroduceerd met Word 2007. Documenten die worden opgeslagen in het oudere binaire `.doc`‑formaat behouden de vlag niet. Om legacy‑formaten te ondersteunen, sla je het document op als `.docx` en, indien nodig, converteer je het later met Aspose.Words’ `SaveFormat.Doc`.

### Wat als ik meerdere shapes tegelijk moet verbergen?

Itereer over de collectie `Document.GetChildNodes(NodeType.Shape, true)` en stel `Hidden = true` in voor elke shape die aan je criteria voldoet (bijv. een specifiek `ShapeType` of een aangepaste `AlternativeText`‑waarde).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Heeft het verbergen van shapes invloed op de prestaties?

De verborgen‑vlag voegt een klein XML‑attribuut toe; het heeft geen merkbare impact op de weergavesnelheid. Een zeer groot aantal verborgen objecten kan echter de bestandsgrootte marginale verhogen. Verwijder shapes die je nooit nodig hebt om het document slank te houden.

## Tips en best practices

- **Geef de shape een betekenisvolle naam** met `rectangle.Name = "MyHiddenRectangle"`; dit helpt bij later zoeken naar de shape in het DOM.  
- **Stel `AlternativeText` in** op een aangepast label (bijv. `"HiddenShape"`). Hiermee kun je de shape vinden zonder te vertrouwen op de index.  
- **Omring de code met een try‑catch‑blok** om licentie‑fouten of I/O‑exceptions netjes af te handelen.  
- **Dispose het Document** na het opslaan als je veel bestanden in een lus verwerkt, om onbeheerste resources vrij te geven: `document.Dispose();`.

## Conclusie

Je weet nu hoe je een **rectangle shape** in een Word‑document kunt **invoegen** met C#, hoe je een **hide shape in Word** kunt toepassen, en hoe je een **create hidden shape** kunt maken die deel blijft uitmaken van de documentstructuur maar onzichtbaar is voor eindgebruikers. Het volledige, uitvoerbare voorbeeld toont de volledige workflow, van documentcreatie tot verificatie.

Vervolgens kun je **how to hide shape** verkennen op basis van gebruikersinvoer, of verborgen shapes combineren met content controls voor dynamische documentgeneratie. Je kunt dezelfde techniek ook toepassen op andere shape‑typen zoals ellipsen, pijlen of aangepaste tekeningen.

Voel je vrij om te experimenteren met verschillende afmetingen, kleuren en zichtbaarheid‑instellingen. Als je tegen problemen aanloopt, bekijk dan de bovenstaande stappen opnieuw of raadpleeg de Aspose.Words‑documentatie voor diepere API‑details. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}