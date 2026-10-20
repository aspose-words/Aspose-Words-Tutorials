---
category: general
date: 2026-08-20
description: Leer hoe u de verborgen‑eigenschap van een vorm instelt in Aspose.Words
  voor C#. Deze gids toont het invoegen van een afbeelding en het verbergen van de
  vorm zodat deze nooit verschijnt in de UI of bij afdrukoutput.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: nl
lastmod: 2026-08-20
og_description: Stel de verborgen eigenschap van een vorm in Aspose.Words in met C#.
  Voeg een afbeelding toe, verberg de vorm en zorg ervoor dat deze nooit wordt weergegeven
  in de UI of bij afdrukoutput.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Stel de verborgen eigenschap van een vorm in Aspose.Words – volledige C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Hoe de verborgen eigenschap van een shape instellen in Aspose.Words voor C#
url: /nl/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe de shape hidden property in te stellen in Aspose.Words voor C#

Als je de **shape hidden property** in een Word‑document moet **instellen**, laat deze tutorial je de exacte stappen zien met Aspose.Words voor .NET. Of je nu een template‑engine bouwt, rapporten genereert, of een logo invoegt dat onzichtbaar moet blijven, je leert hoe je een afbeelding invoegt en de vorm verbergt zodat deze nooit verschijnt in de UI of afdrukoutput.

In deze gids behandelen we ook **insert image into document**, leggen we uit waarom het verbergen van een vorm belangrijk is voor afdrukken, en lopen we de volledige, uitvoerbare code door. Er zijn geen externe referenties nodig—kopieer, plak en voer uit.

## Vereisten

* .NET 6.0 of later (de nieuwste Aspose.Words‑versie richt zich op .NET 6+)
* Een geldige Aspose.Words for .NET‑licentie (of gebruik de gratis evaluatiemodus)
* Visual Studio 2022 of een andere C#‑IDE naar keuze
* Een afbeeldingsbestand (bijv. `logo.png`) geplaatst in een map die je vanuit code kunt refereren

## Stap 1: Maak een nieuw Document en DocumentBuilder

De `DocumentBuilder`‑klasse is het toegangspunt voor het programmatisch bouwen van Word‑inhoud. Hiermee kun je alinea's, tabellen en vormen zoals afbeeldingen invoegen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom deze stap?*  
Het maken van een `Document` geeft je een in‑memory representatie van een .docx‑bestand, terwijl de `DocumentBuilder` de fluente API levert die objecten invoegt. Zonder deze objecten kun je geen vorm in het document plaatsen.

## Stap 2: Voeg de afbeelding in als een vorm

Aspose.Words behandelt elke afbeelding als een `Shape`. De `InsertImage`‑methode retourneert die `Shape`‑instantie, die je later kunt manipuleren.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Waarom deze stap?*  
Het gebruik van `InsertImage` voegt niet alleen de afbeelding toe aan de tekststroom, maar geeft je ook een referentie (`picture`) die je kunt configureren. Dit is essentieel voor de **C# shape hidden property** die we hierna zullen instellen.

## Stap 3: Stel de verborgen eigenschap van de vorm in

De `Hidden`‑eigenschap bepaalt of de vorm deelneemt aan de UI en afdrukken. Als je deze op `true` zet, wordt de vorm onzichtbaar in de Word‑UI en wordt gegarandeerd dat deze niet wordt afgedrukt.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Waarom deze stap?*  
Wanneer een vorm als verborgen is gemarkeerd, behandelt Word deze als een commentaar—aanwezig in de documentstructuur maar nooit gerenderd. Dit is de kern van **set shape hidden property**.

## Stap 4: Sla het document op

Schrijf tenslotte het document naar schijf. Je kunt elk formaat kiezen dat door Aspose.Words wordt ondersteund (`.docx`, `.pdf`, `.html`, enz.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Waarom deze stap?*  
Opslaan maakt de in‑memory wijzigingen definitief. Het openen van de resulterende `.docx` in Microsoft Word toont geen zichtbare afbeelding, en de PDF‑export bevestigt dat de vorm nooit verschijnt in de afdrukoutput.

## Volledig, uitvoerbaar voorbeeld

Alles samenvoegend, hier is het volledige programma dat je kunt compileren en uitvoeren:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Verwachte output**

- Het openen van `HiddenImageDocument.docx` in Microsoft Word toont geen zichtbare afbeelding.
- Het exporteren of afdrukken van het document (of het openen van de PDF) toont ook geen afbeelding.
- De verborgen vorm bestaat nog steeds in de document‑XML, wat je kunt verifiëren door de `.docx` als zip te openen en `word/document.xml` te inspecteren – je ziet een `<w:pict>`‑element met `w:hidden="true"`.

## Veelvoorkomende variaties en randgevallen

| Situatie | Wat te doen | Waarom het belangrijk is |
|----------|-------------|--------------------------|
| **Afbeeldingsbestand ontbreekt** | Plaats `InsertImage` in een `try/catch` en verwerk `FileNotFoundException`. | Voorkomt dat de applicatie crasht en stelt je in staat een duidelijke fout te loggen. |
| **Meerdere verborgen vormen** | Roep `picture.Hidden = true` aan voor elke `Shape` die je invoegt, of iterate over `doc.GetChildNodes(NodeType.Shape, true)`. | Garandeert dat elk ongewenst visueel element onzichtbaar blijft. |
| **Vorm alleen zichtbaar in bewerkingsmodus nodig** | Stel `picture.Hidden = false` in na bewerken, en schakel terug vóór het opslaan. | Staat je toe met de vorm te werken in de UI terwijl de uiteindelijke output schoon blijft. |
| **Afdrukken op oudere Word‑versies** | Controleer het document met Word 2010 of later; de verborgen vlag wordt ondersteund in alle moderne versies. | Zorgt voor compatibiliteit voor je gebruikersbasis. |
| **Een ander bestandsformaat gebruiken (bijv. direct PDF)** | De `Hidden`‑vlag werkt hetzelfde; Aspose.Words respecteert deze tijdens PDF‑conversie. | Bevestigt dat **prevent shape from printing** werkt voor alle exportdoelen. |

## Pro tip: Verifieer de verborgen vlag programmatisch

Als je moet bevestigen dat een vorm verborgen is vóór het opslaan, kun je de eigenschap inspecteren:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Deze eenvoudige controle is nuttig in geautomatiseerde pipelines waar je moet garanderen dat wordt voldaan aan document‑generatiebeleid.

## Conclusie

Je weet nu hoe je de **shape hidden property** in Aspose.Words voor C# kunt **instellen**. Door een afbeelding in te voegen, `picture.Hidden = true` toe te passen en het document op te slaan, blijft de vorm buiten de UI en verschijnt deze nooit in de afdrukoutput. Deze techniek is essentieel wanneer je placeholders, watermerken of branding‑elementen nodig hebt die onzichtbaar moeten blijven voor eindgebruikers.

### Wat nu?

* Verken andere vorm‑eigenschappen zoals `picture.WrapType`, `picture.Rotation` en `picture.RelativeHorizontalPosition`.
* Leer hoe je **hide shape in Aspose.Words** conditioneel kunt toepassen op basis van gebruikersinvoer of configuratie.
* Combineer verborgen vormen met **insert image into document**‑lussen om dynamische, onzichtbare markers te genereren voor latere verwerking (bijv. mail‑merge‑velden).

Voel je vrij om te experimenteren met verschillende afbeeldingsformaten, documentlay-outs en exportdoelen. Het verbergen van vormen geeft je fijnmazige controle over wat je lezers daadwerkelijk zien—en wat achter de schermen blijft. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekige vorm maken in Word met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Groepvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inline‑afbeelding invoegen in Word‑document met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}