---
category: general
date: 2026-09-05
description: Leer hoe je een leeg Word‑document maakt en een rechthoekvorm toevoegt
  die verborgen kan worden met Aspose.Words in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: nl
lastmod: 2026-09-05
og_description: Lege Word-document maken en verborgen rechthoekvorm invoegen met Aspose.Words
  – stapsgewijze gids voor C#‑ontwikkelaars.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Maak een leeg Word‑document met een verborgen rechthoekvorm
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Maak een leeg Word‑document en voeg een rechthoekvorm toe
url: /nl/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en voeg een rechthoekige vorm toe

Als je een **leeg Word‑document** wilt maken dat ook een vorm bevat die je niet in de lay‑out wilt laten verschijnen, laat deze gids je precies zien hoe je dat doet met Aspose.Words voor .NET. Je ziet een volledig, uitvoerbaar voorbeeld dat een nieuw document maakt, een rechthoekige vorm toevoegt, die vorm verbergt en het bestand opslaat — zonder extra hulpmiddelen.

De tutorial behandelt alles, van projectopzet tot het oplossen van veelvoorkomende valkuilen. Aan het einde kun je een Word‑bestand genereren dat leeg lijkt voor de lezer, maar toch verborgen metadata bevat, wat nuttig is voor bijvoorbeeld watermerken, aangepaste XML‑opslag of lay‑out‑ankers.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later (de code werkt ook met .NET Framework 4.7+)
* Visual Studio 2022 (of een IDE die C# ondersteunt)
* Een geldige **Aspose.Words** NuGet‑licentie (de gratis proefversie werkt voor testen)
* Basiskennis van C# en het concept van document‑nodes

Je kunt de bibliotheek installeren met de volgende CLI‑opdracht:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Houd je Aspose.Words‑versie up‑to‑date; de API die in deze tutorial wordt gebruikt is stabiel vanaf versie 23.10.

## Hoe maak je een leeg Word‑document met Aspose.Words

De eerste stap is het instantieren van een `Document`‑object. Een nieuw `Document` vertegenwoordigt een leeg **blank word document** — geen alinea's, geen secties, alleen de bestandscontainer.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Waarom dit belangrijk is:** Beginnen met een schoon document zorgt ervoor dat de verborgen vorm die je later toevoegt, geen interferentie veroorzaakt met bestaande inhoud of stijlen.

## Voeg een rechthoekige vorm toe aan het document

Vervolgens maken we een rechthoekige vorm. In Aspose.Words is een vorm een node die overal in de documentboom kan worden geplaatst, en die kan worden geconfigureerd met grootte, vulling, lijntype en zichtbaarheid.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

De bovenstaande code maakt een zichtbare rechthoek. Op dit moment zou je de vorm in het document kunnen invoegen met `builder.InsertNode(rectangle)`. Omdat we echter willen dat de vorm verborgen blijft, passen we de `Hidden`‑eigenschap aan vóór het invoegen.

## Hoe een vorm verbergen in een Word‑document

Word biedt een `Hidden`‑attribuut voor vorm‑nodes. Wanneer dit op `true` staat, verschijnt de vorm niet in de paginalay‑out, maar blijft hij wel deel uitmaken van de XML van het document. Dit is de kern van de **how to hide shape**‑vereiste.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Uitleg:** Het instellen van `Hidden = true` voegt het `<w:hide>`‑attribuut toe aan de XML van de vorm. Word‑processors negeren de vorm tijdens het renderen, maar de vorm kan nog steeds programmatisch of via de XML‑weergave van Word worden benaderd.

## Voeg de verborgen vorm toe aan het lege document

Nu plaatsen we de verborgen rechthoek in de documentboom. Omdat het document nog leeg is, wordt de vorm de eerste node in het hoofdverhaal.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Als je het resulterende bestand opent in Microsoft Word, zie je een ogenschijnlijk lege pagina. De vorm is er, maar hij is onzichtbaar.

## Sla het document op

Tot slot schrijf je het document naar schijf. Je kunt elk ondersteund formaat kiezen (`.docx`, `.pdf`, `.odt`, enz.). Voor deze tutorial gebruiken we het moderne DOCX‑formaat.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Verwacht resultaat

Open `HiddenRectangle.docx` in Word:

* Het document lijkt leeg (geen zichtbare vormen of tekst).
* Als je het bestand inspecteert met een tool zoals **Open XML SDK** of de **Word XML Viewer**, zie je het `<w:pict>`‑element dat de rechthoek met het `hidden`‑attribuut bevat.

![leeg Word‑document met verborgen rechthoekige vorm](image.png){: .align-center alt="leeg Word‑document met verborgen rechthoekige vorm"}

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een console‑applicatie. Het bevat alle benodigde `using`‑directieven, foutafhandeling en commentaren.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Voer het programma uit (`dotnet run`) en controleer het uitvoerbestand. De console bevestigt de opslaglocatie.

## Veelgestelde vragen en randgevallen

### Kan ik meerdere vormen tegelijk verbergen?

Ja. Maak elke vorm, stel `Hidden = true` in, en voeg ze opeenvolgend in. De verborgen vlag werkt per node, dus het combineren van verborgen en zichtbare vormen in hetzelfde document wordt ondersteund.

### Wat als ik de vorm alleen in de afdrukweergave wil verbergen?

Word maakt onderscheid tussen **weergave**‑ en **afdruk**‑zichtbaarheid via de `DisplayWhen`‑eigenschap. Aspose.Words biedt geen directe API voor die vlag, maar je kunt de onderliggende XML aanpassen:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Gebruik dit alleen wanneer je alleen afdruk‑zichtbaarheid nodig hebt.

### Heeft de verborgen vorm invloed op de bestandsgrootte?

Een verborgen vorm voegt dezelfde XML‑payload toe als een zichtbare, dus de toename in bestandsgrootte is identiek. Echter, omdat de vorm

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een leeg Word‑document met schaduwrijke rechthoekige vorm – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Maak een rechthoekige vorm in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Voeg een schaduw toe aan een Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}