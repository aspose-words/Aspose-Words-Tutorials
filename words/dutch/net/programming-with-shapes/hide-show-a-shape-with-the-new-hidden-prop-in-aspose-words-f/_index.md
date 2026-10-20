---
category: general
date: 2026-10-20
description: Verberg/Toon een vorm met de nieuwe `Hidden`‑eigenschap in Aspose.Words
  voor C#. Leer hoe je de zichtbaarheid van een vorm kunt schakelen, randgevallen
  kunt afhandelen en het resultaat kunt opslaan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: nl
lastmod: 2026-10-20
og_description: Verberg/Toon een vorm met de nieuwe `Hidden`‑eigenschap met Aspose.Words
  voor C#. Beheers het schakelen van de zichtbaarheid van vormen en vermijd veelvoorkomende
  valkuilen.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Verberg/Toon een vorm met de nieuwe `Hidden`‑eigenschap in Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Verberg/Toon een vorm met de nieuwe `Hidden`‑eigenschap in Aspose.Words voor
  C#
url: /nl/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verberg/Toon een Vorm met de nieuwe `Hidden` eigenschap in Aspose.Words voor C#

Als je een **Verberg/Toon een Vorm met de nieuwe `Hidden` eigenschap** in een Word‑document nodig hebt, laat deze gids je precies zien hoe je dit doet met Aspose.Words voor .NET. Of je nu rapporten genereert, sjablonen maakt of geïmporteerde documenten opschoont, het programmatisch regelen van de zichtbaarheid van vormen bespaart je handmatig bewerken.

In deze tutorial leer je hoe je een document laadt, een vorm vindt, de `Hidden` eigenschap wisselt, en het gewijzigde bestand opslaat. De stappen behandelen ook veelvoorkomende variaties, zoals het verwerken van meerdere vormen en omgaan met inline versus zwevende afbeeldingen.

## Vereisten

* .NET 6.0 (of later) geïnstalleerd – Aspose.Words ondersteunt .NET Standard 2.0 en .NET Core.
* Een gelicentieerde kopie van **Aspose.Words for .NET** (de gratis proefversie werkt voor verkenning).
* Een IDE zoals Visual Studio 2022 of Visual Studio Code.
* Een Word‑document (`input.docx`) dat minstens één vorm bevat (bijv. een afbeelding, SmartArt of een tekencanvas).

## Stap 1: Laad het Word‑document

De eerste handeling is het aanmaken van een `Document`‑object dat het .docx‑bestand op schijf vertegenwoordigt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Waarom deze stap belangrijk is*: `Document` is het toegangspunt voor alle Aspose.Words‑bewerkingen. Het laden van het bestand in het geheugen geeft je volledige toegang tot de knoopboom, inclusief vormen.

## Stap 2: Haal de doelvorm op

Om de zichtbaarheid te wisselen moet je een referentie naar de vormknoop verkrijgen. Het voorbeeld hieronder haalt de eerste vorm in het document op, maar je kunt de logica aanpassen om vormen te vinden op naam, type of index.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Waarom deze stap belangrijk is*: `GetChild` met `true` voert een diepte‑zoekopdracht uit, waardoor je vormen vindt zelfs als ze genest zijn in tabellen of kopteksten. Controleren op `null` voorkomt een `NullReferenceException` wanneer het document geen vormen bevat.

## Stap 3: Verberg de vorm met de `Hidden` eigenschap

Aspose.Words heeft de `Hidden` eigenschap geïntroduceerd om te bepalen of een vorm wordt weergegeven of afgedrukt. Instellen op `true` verbergt de vorm; instellen op `false` maakt de vorm weer zichtbaar.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Als je een eerder verborgen vorm moet **tonen**, wijs dan simpelweg `false` toe:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Waarom deze stap belangrijk is*: De `Hidden` eigenschap werkt voor zowel zwevende als inline vormen, en integreert met Word’s native “Hidden” opmaak. Deze aanpak is betrouwbaarder dan het verwijderen van de vorm omdat de knoop in de documentboom blijft, waardoor lay‑out en verwijzingen behouden blijven.

## Stap 4: Sla het gewijzigde document op

Na het aanpassen van de zichtbaarheid, schrijf je de wijzigingen terug naar een nieuw bestand (of overschrijf het origineel indien gewenst).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Waarom deze stap belangrijk is*: `Save` serialiseert de in‑memory knoopboom naar een .docx‑pakket dat Word kan openen. De verborgen‑vlag wordt bewaard, zodat het openen van het bestand in Microsoft Word de vorm weergeeft volgens de `Hidden` instelling.

## Volledig, uitvoerbaar voorbeeld

Alle stappen samenvoegen levert een zelfstandige applicatie op die je kunt kopiëren, compileren en uitvoeren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Verwachte output** wanneer je het programma uitvoert:

```
Document saved. Shape hidden = True
```

Het openen van `ShapeHidden.docx` in Microsoft Word toont het document zonder de doelvorm. Als je `shape.Hidden = false;` instelt vóór het opslaan, verschijnt de vorm opnieuw.

## Meerdere vormen verwerken

Het voorbeeld hierboven werkt voor één vorm. Praktijkdocumenten bevatten vaak veel afbeeldingen. Gebruik een lus om alle vormen die aan een voorwaarde voldoen te verbergen of te tonen (bijv. een specifieke naam of type).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tip*: Filteren op `ShapeType` voorkomt dat decoratieve elementen zoals tekstvakken of SmartArt per ongeluk worden verborgen.

## Randgevallen en best practices

| Situatie | Aanbevolen aanpak |
|-----------|----------------------|
| **Vorm bevindt zich in een kop‑/voettekst** | Haal eerst de kop‑/voettekstknoop op, en roep vervolgens `GetChild(NodeType.Shape, …)` aan op dat sub‑document. |
| **Document bevat geen vormen** | Controleer altijd op `null` na `GetChild` of controleer `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Je moet de verborgen‑vlag behouden over verschillende Word‑versies** | De `Hidden` eigenschap wordt opgeslagen in de XML van de vorm als `<w:hidden/>`, wat wordt ondersteund door Word 2007 en later. |
| **Prestaties bij grote documenten** | Gebruik `doc.GetChildNodes(NodeType.Shape, true)` één keer en hergebruik de collectie in plaats van herhaaldelijk `GetChild` aan te roepen. |

## Pro‑tip: Combineer `Hidden` met `WrapType`

Wanneer een vorm verborgen is, reserveert Word nog steeds de ruimte die de vorm zou innemen, tenzij je ook het omloopgedrag wijzigt. Instellen van `WrapType = WrapType.None` verwijdert het placeholder‑gebied.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Dit zorgt ervoor dat de lay‑out inklapt alsof de vorm nooit heeft bestaan, wat nuttig is voor het genereren van nette rapporten.

## Conclusie

Je weet nu hoe je een **Vorm kunt Verbergen/Toon met de nieuwe `Hidden` eigenschap** kunt gebruiken met Aspose.Words voor C#. De oplossing omvat het laden van een document, het vinden van een vorm, het wisselen van de `Hidden` eigenschap en het bewaren van de wijziging. Door de best‑practice‑tips te volgen — controleren op null, meerdere vormen verwerken en de omloopinstellingen aanpassen — kun je betrouwbaar de zichtbaarheid van vormen regelen in elke Word‑automatiseringsscenario.

Klaar om meer te verkennen? Overweeg de volgende stappen:

* **Verberg/Toon meerdere vormen** op basis van aangepaste metadata (maakt gebruik van de “programmatically hide shape” techniek).
* **Combineer `Hidden` met conditionele inhoud** met behulp van Aspose.Words‑velden voor dynamische rapportgeneratie.
* **Verken andere knoop‑eigenschappen**, zoals `Visible` voor grafiekobjecten of `IsDeleted` voor alinea‑niveau controle.

Veel programmeerplezier, en geniet van de fijnmazige controle die Aspose.Words biedt voor de zichtbaarheid van vormen in Word‑documenten!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [vorm verbergen in Word met C# – stapsgewijze gids](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [Hoe een vorm te verbergen in Word met C# – stapsgewijze gids](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Maak een leeg Word‑document met een verborgen ellipsvorm – volledige C#‑gids](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}