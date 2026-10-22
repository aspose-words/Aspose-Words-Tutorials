---
category: general
date: 2026-09-18
description: Maak een leeg Word‑document en verberg een ellipsvorm met Aspose.Words.
  Leer hoe je een vorm in Word verbergt, hoe je een ellips invoegt en hoe je snel
  een verborgen vorm maakt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: nl
lastmod: 2026-09-18
og_description: Maak een leeg Word‑document en verberg een ellipsvorm in Word. Deze
  gids laat je stap voor stap zien hoe je een ellips invoegt, een vorm verbergt in
  Word en een verborgen vorm maakt met Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Maak een leeg Word‑document met een verborgen ellipsvorm
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Maak een leeg Word‑document met een verborgen ellipsvorm
url: /nl/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word-document met een verborgen ellipsvorm

Als je een **leeg Word-document** moet maken dat een vorm bevat die je niet in de lay-out wilt laten verschijnen, laat deze gids je precies zien hoe je dat doet. Door Aspose.Words for .NET te gebruiken kun je programmatisch een ellips invoegen en vervolgens de vorm verbergen zodat het document visueel leeg blijft, terwijl de vormgegevens behouden blijven.

In deze tutorial leer je:

* hoe je **blank Word document** objecten maakt,
* hoe je **insert ellipse** gebruikt met `DocumentBuilder`,
* hoe je **hide shape in Word** gebruikt zodat het de pagina niet beïnvloedt,
* hoe je **create hidden shape** objecten maakt voor latere verwerking.

De stappen werken met .NET 6+ en de nieuwste Aspose.Words versie (23.9 op het moment van schrijven). Er is geen extra Office‑installatie vereist.

## Vereisten

* Visual Studio 2022 (of een andere C# IDE)
* .NET 6 SDK of later
* Aspose.Words for .NET NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* Basiskennis van C# en Word‑documentconcepten

## Stap 1: Maak een leeg Word-document

Het eerste wat je moet doen is een `Document`‑object instantieren. Dit object vertegenwoordigt een leeg `.docx`‑bestand en vormt de basis voor alle verdere bewerkingen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Het maken van een **blank Word document** geeft je een schoon canvas – geen alinea's, geen secties, alleen de onderliggende pakketsstructuur. Dit is het ideale startpunt wanneer je alleen een verborgen vorm nodig hebt en niets anders.

## Stap 2: Initialiseer een DocumentBuilder

`DocumentBuilder` biedt een handige API om inhoud toe te voegen aan een `Document`. Het werkt als een cursor die je door het document beweegt.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder maakt automatisch een standaard eerste sectie en alinea aan, zodat je vormen kunt invoegen zonder handmatig secties toe te voegen.

## Stap 3: Voeg een ellipsvorm in

Nu **insert ellipse** we met de `InsertShape`‑methode. Deze methode neemt een `ShapeType`‑enumeratie, de breedte en de hoogte (in points).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Waarom een ellips? Een ellips is een vectorvorm die verborgen kan worden zonder de omliggende tekststroom te beïnvloeden. De breedte van 100 pt en de hoogte van 50 pt zijn willekeurig; je kunt ze aanpassen aan je latere verwerkingsbehoeften.

## Stap 4: Verberg de vorm zodat deze niet in de lay-out verschijnt

Om **hide shape in Word** te doen, stel je de `Hidden`‑eigenschap van het `Shape`‑object in op `true`. Wanneer het document wordt geopend in Microsoft Word, is de vorm onzichtbaar en neemt ze geen ruimte in de lay-out in.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

De `Hidden`‑vlag wordt opgeslagen in de XML van de vorm (`<w:hidden/>`). Word respecteert dit attribuut tijdens het renderen, waardoor het document er volledig leeg uitziet, hoewel de vorm aanwezig is.

### Pro‑tip

Als je later de vorm weer zichtbaar wilt maken, stel je eenvoudig `ellipse.Hidden = false;` in en sla je het document op.

## Stap 5: Sla het document op met de verborgen vorm

Sla tenslotte het document op op schijf. Het bestand zal een regulier `.docx` zijn dat elke Word‑processor kan openen.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Het opgeslagen bestand, `HiddenEllipse.docx`, is een **create blank word document** dat een verborgen ellips bevat. Het openen in Microsoft Word toont een lege pagina, maar de vorm is nog steeds aanwezig in de Open XML‑structuur.

## Volledig werkend voorbeeld

Hieronder staat het volledige, zelfstandige programma dat je kunt kopiëren, plakken en uitvoeren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwachte output**

* Een bestand genaamd `HiddenEllipse.docx` verschijnt in `C:\Temp`.
* Het openen van het bestand in Microsoft Word toont een volledig lege pagina.
* Als je het document inspecteert met de Open XML SDK of een zip‑viewer, vind je het `<w:shape>`‑element met `<w:hidden/>` binnen het documentdeel.

## Veelgestelde vragen en randgevallen

### Wat als de vorm nog steeds verschijnt?

* Zorg ervoor dat je Aspose.Words 23.9 of later gebruikt – oudere versies hadden een bug waarbij `Hidden` werd genegeerd voor sommige vormtypes.
* Controleer of je geen extra opmaak toepast (bijv. `WrapType`) die de vorm dwingt ruimte in de lay-out in te nemen.

### Kan ik andere vormtypes verbergen?

Ja. Dezelfde `Hidden`‑eigenschap werkt voor `ShapeType.Rectangle`, `ShapeType.Picture`, enz. Vervang gewoon `ShapeType.Ellipse` door het gewenste type.

### Hoe lijst je later verborgen vormen op?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Dit fragment doorloopt alle vormen en print diegene die verborgen zijn, wat nuttig is voor **create hidden shape**‑workflows waarin je later de vormen moet verwerken of zichtbaar maken.

## Conclusie

Je weet nu hoe je een **blank Word document** maakt, een **ellipse invoegt**, en een **hide shape in Word** toepast om een **create hidden shape** te produceren die onzichtbaar blijft voor de lezer. Deze techniek is handig voor het opslaan van metadata, bladwijzers of aangepaste XML binnen een document zonder de visuele weergave te wijzigen.

### Volgende stappen

* Verken **how to hide shape** conditioneel op basis van documentinhoud.
* Leer **how to unhide shape** bij het genereren van een definitieve versie van het document.
* Combineer verborgen vormen met **custom document properties** om machine‑leesbare gegevens in te sluiten.

Voel je vrij om te experimenteren met verschillende vormtypes, groottes en verborgen‑statuslogica om aan je automatiseringsscenario te voldoen. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}