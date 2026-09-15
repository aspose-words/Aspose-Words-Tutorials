---
category: general
date: 2026-09-14
description: Leer hoe je een vorm in Word kunt verbergen met C# — inclusief code om
  een Word‑document te maken, een rechthoekvorm in Word in te voegen en de vorm via
  code te verbergen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: nl
lastmod: 2026-09-14
og_description: Hoe een vorm verbergen in Word met C# — stapsgewijze handleiding die
  ook laat zien hoe je code voor een Word‑document maakt en een rechthoekige vorm
  in Word invoegt.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Hoe een vorm te verbergen in een Word‑document met C#‑code
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een vorm te verbergen in een Word‑document met C#‑code
url: /nl/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een vorm te verbergen in een Word‑document met C#‑code

Als je **how to hide shape** in een Word‑bestand moet verbergen, toont deze tutorial de volledige oplossing. Je ziet hoe je een Word‑document maakt, een rechthoekvorm invoegt, een ellips toevoegt, en die ellips verbergt zodat alleen de rechthoek verschijnt wanneer het bestand wordt geopend.

De gids behandelt alles wat je nodig hebt—geen externe referenties, alleen de code en uitleg. Aan het einde kun je verborgen grafische elementen in elk Word‑document embedden dat je programmatisch genereert.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET (gratis proefversie of gelicentieerde versie)  
  Installeer het via NuGet: `dotnet add package Aspose.Words`
- Basiskennis van C# en Visual Studio of een andere IDE naar keuze

## Stap 1: Het project opzetten en namespaces importeren

Start een nieuwe console‑applicatie en voeg de vereiste `using`‑statements toe. Deze imports geven je toegang tot de `Document`, `DocumentBuilder` en tekenklassen die nodig zijn om vormen te manipuleren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Waarom dit belangrijk is** – Het importeren van de juiste namespaces voorkomt compilatiefouten en maakt de API‑functionaliteit beschikbaar voor het maken van vormen en het regelen van zichtbaarheid.

## Stap 2: Een nieuw Word‑document en een builder maken

Een `Document` vertegenwoordigt het bestand, terwijl een `DocumentBuilder` een vloeiende API biedt voor het toevoegen van inhoud. Dit is de eerste plaats waar je de **how to hide shape**‑logica toepast: je hebt een documentcontext nodig voordat een vorm kan bestaan.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Uitleg** – Het `Document`‑object start leeg. De `DocumentBuilder` staat aan het begin van de eerste alinea, klaar om vormen of tekst in te voegen.

## Stap 3: Een zichtbare rechthoekvorm invoegen

De rechthoek zal de vorm zijn die zichtbaar blijft wanneer het document wordt geopend. Je kunt de grootte, positie en opmaak direct via het vormobject regelen.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Waarom deze stap** – Het toevoegen van een rechthoek toont de **insert rectangle shape word**‑vereiste. Het instellen van `FillColor` en `LineColor` maakt de vorm gemakkelijk te herkennen in het uiteindelijke document.

## Stap 4: Een ellipsvorm invoegen en verbergen

Nu voeg je de vorm toe die je wilt verbergen. De `Hidden`‑eigenschap vertelt Word de vorm niet weer te geven in de UI, hoewel deze deel blijft uitmaken van de documentstructuur.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Uitleg** – Het instellen van `Hidden = true` is de kern van **hide shape in word**. Word respecteert deze vlag tijdens normaal bekijken en afdrukken, maar de vorm kan desgewenst nog steeds programmatisch worden benaderd.

## Stap 5: Het document opslaan

Schrijf tenslotte het document naar schijf. Kies een map waarin je schrijfrechten hebt, en geef het bestand een duidelijke naam die het doel van de tutorial weergeeft.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Resultaat** – Het openen van `ShapeVisibility.docx` in Microsoft Word toont alleen de lichtblauwe rechthoek. De verborgen ellips verschijnt niet, wat bevestigt dat je succesvol **how to hide shape** in een Word‑bestand hebt beheerst.

## Volledig werkend voorbeeld

Alle fragmenten samenvoegen geeft je een enkel, uitvoerbaar programma:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Verwachte output

- **Visueel**: Wanneer je `ShapeVisibility.docx` opent, zie je een lichtblauwe rechthoek geplaatst dicht bij de linkermarge. Er is geen ellips zichtbaar.
- **Programma**: De verborgen ellips blijft aanwezig in de XML van het document (`<w:drawing>`‑element) met het `w:hidden`‑attribuut ingesteld, wat je kunt verifiëren door het bestand als zip te openen en `document.xml` te inspecteren.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Kan ik meerdere vormen verbergen?* | Ja. Stel `Hidden = true` in voor elke vorm die je wilt verbergen. |
| *Worden verborgen vormen afgedrukt?* | Standaard drukt Word verborgen objecten niet af. Als je ze wilt afdrukken, verwijder dan de `Hidden`‑vlag vóór het afdrukken. |
| *Wordt de verborgen eigenschap ondersteund in oudere Word‑versies?* | Het `Hidden`‑attribuut maakt deel uit van de Office Open XML‑standaard en werkt in Word 2007 en later. |
| *Wat als ik de zichtbaarheid tijdens runtime wil schakelen?* | Haal de vorm op via `document.GetChildNodes(NodeType.Shape, true)` en wissel de `Hidden`‑eigenschap op basis van je logica. |

## Pro‑tips

- **Prestaties**: Als je veel documenten genereert, hergebruik dan één `DocumentBuilder`‑instantie in plaats van voor elk bestand een nieuwe te maken.
- **Versiebeheer**: Sla de gegenereerde `.docx`‑bestanden op in een versie‑gecontroleerde map; verborgen vormen kunnen fungeren als metadata‑markeringen voor downstream‑verwerking.
- **Testen**: Automatiseer een snelle visuele test door de DOCX naar PDF te converteren met Aspose.Words (`document.Save("out.pdf")`). De PDF zal de ellips ook verbergen, wat bevestigt dat de verborgen vlag zich voortzet bij formaatconversies.

## Conclusie

Je weet nu **how to hide shape** in een Word‑document met C#. De tutorial heeft het maken van een document, **insert rectangle shape word**, het toevoegen van een ellips, en het toepassen van de `Hidden`‑vlag doorlopen om **hide shape in word** gedrag te bereiken. Met de volledige, uitvoerbare code kun je verborgen grafische elementen integreren in elke geautomatiseerde rapportage‑ of sjabloon‑workflow.

### Volgende stappen

- Verken andere vormeigenschappen zoals rotatie, schaduw en tekstomloop.  
- Combineer verborgen vormen met aangepaste documenteigenschappen om machine‑leesbare gegevens te embedden.  
- Bekijk **create word document code**‑patronen voor tabellen, grafieken en inhoudsbesturingselementen om je automatiseringstoolkit uit te breiden.

Voel je vrij om te experimenteren met verschillende vormtypen en zichtbaarheid‑instellingen—je volgende Word‑automatiseringsproject is slechts een paar regels code verwijderd!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Leeg Word‑document maken met schaduwrandrechthoek – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words vormschaduw‑tutorial – Voeg een schaduw toe aan een Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}