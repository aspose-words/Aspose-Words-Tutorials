---
category: general
date: 2026-08-04
description: Hoe een vorm in Word te verbergen met C# aan de hand van een volledig
  voorbeeld. Leer een Word‑document te laden, een vorm te verbergen en het bestand
  efficiënt op te slaan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- load word document c#
- Aspose.Words hide shape
- C# document manipulation
language: nl
lastmod: 2026-08-04
og_description: Hoe je een vorm in Word verbergt met C# wordt uitgelegd met een volledig
  codevoorbeeld. Volg de gids om een document te laden, een vorm te verbergen en het
  resultaat op te slaan.
og_image_alt: Screenshot of C# code that hides a shape in a Word document
og_title: hoe een vorm te verbergen in Word met C# – volledige programmeergids
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: how to hide shape in Word using C# with a complete example. Learn to
    load a Word document, hide a shape, and save the file efficiently.
  headline: how to hide shape in Word using C# – step-by-step guide
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Hoe een vorm verbergen in Word met C# – stapsgewijze handleiding
url: /nl/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hoe vorm te verbergen in Word met C# – volledige programmeergids

Als je **hoe een vorm te verbergen** in een Microsoft Word‑bestand moet, toont deze gids je de exacte stappen in C#. Je ziet hoe je een Word‑document laadt, de eerste vorm vindt, de eigenschap Hidden instelt en het bijgewerkte bestand opslaat — allemaal met één enkel, uitvoerbaar voorbeeld.

Het verbergen van een vorm is gebruikelijk wanneer je rapporten genereert die decoratieve elementen bevatten die je voor bepaalde doelgroepen wilt onderdrukken. De tutorial behandelt ook hoe je **load Word document c#** veilig kunt doen en bespreekt variaties zoals het verbergen van meerdere vormen of het verwerken van documenten zonder vormen.

## Vereisten

- .NET 6.0 of later geïnstalleerd  
- Visual Studio 2022 (of een IDE die C# ondersteunt)  
- Het **Aspose.Words for .NET** NuGet‑pakket (versie 23.9 of nieuwer)  

Je kunt het pakket toevoegen met het volgende commando:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Gebruik de gratis evaluatieversie van Aspose.Words om de code te testen voordat je een licentie aanschaft.

## Stap 1: Laad het Word‑document in C#

De eerste handeling is het laden van het bestaande `.docx`‑bestand. Aspose.Words leest het bestand in een `Document`‑object, dat een rijk objectmodel biedt voor het navigeren en manipuleren van het bestand.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the Word document from disk
Document doc = new Document(@"C:\Docs\Shape.docx");
```

*Waarom dit belangrijk is:* Het laden van het document creëert een in‑memory‑representatie waarmee je knooppunten (alinea's, tabellen, vormen, enz.) kunt opvragen zonder opnieuw het bestandssysteem aan te raken. Deze aanpak is snel en thread‑veilig.

## Stap 2: Haal de vorm op die je wilt verbergen

Een vorm wordt weergegeven door de `Shape`‑klasse. Je kunt deze vinden met `GetChild`, dat de documentboom doorzoekt naar het eerste knooppunt van het opgegeven type.

```csharp
// Retrieve the first shape in the document (index 0)
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

Als het document geen vormen bevat, retourneert `GetChild` `null`. Bescherm tegen dat geval:

```csharp
if (shape == null)
{
    Console.WriteLine("No shapes were found in the document.");
    return;
}
```

*Waarom dit belangrijk is:* Het controleren op `null` voorkomt een `NullReferenceException` wanneer het document geen vormen bevat, waardoor de code robuust is voor elk invoerbestand.

## Stap 3: Verberg de vorm

De eigenschap `Shape.Hidden` bepaalt of Word de vorm weergeeft in de UI en bij het afdrukken. Deze op `true` zetten verbergt de vorm effectief zonder deze te verwijderen.

```csharp
// Hide the shape by setting its Hidden property
shape.Hidden = true;
```

> **Opmerking:** Verborgen vormen blijven deel uitmaken van de documentstructuur, dus je kunt ze later weer zichtbaar maken door `Hidden = false` in te stellen.

## Stap 4: Sla het gewijzigde document op

Na het wijzigen van de zichtbaarheid van de vorm, sla je de wijzigingen op naar schijf. Je kunt het oorspronkelijke bestand overschrijven of naar een nieuwe locatie schrijven.

```csharp
// Save the modified document
doc.Save(@"C:\Docs\ShapeHidden.docx");
Console.WriteLine("Document saved with the shape hidden.");
```

*Waarom dit belangrijk is:* Opslaan maakt een nieuw `.docx`‑bestand aan dat de verborgen‑vorm‑status weerspiegelt. Word opent het bestand zonder de vorm te tonen, terwijl de vorm in de XML blijft voor eventueel later gebruik.

## Stap 5: (Optioneel) Verberg meerdere vormen of filter op naam

De meeste praktijkscenario's omvatten meer dan één vorm. Je kunt door alle vormen itereren en die verbergen die aan een voorwaarde voldoen, zoals een specifieke naam of vormtype.

```csharp
// Hide every shape whose name starts with "Chart"
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.Name != null && s.Name.StartsWith("Chart"))
    {
        s.Hidden = true;
    }
}
doc.Save(@"C:\Docs\AllChartsHidden.docx");
```

*Waarom dit belangrijk is:* Dit patroon stelt je in staat om gedetailleerde controle toe te passen — verberg alleen grafieken, logo's of watermerken — terwijl andere afbeeldingen onaangeroerd blijven.

## Volledig, uitvoerbaar voorbeeld

Alles samengevoegd, hier is een zelfstandige programma dat je kunt kopiëren, plakken en uitvoeren:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document(@"C:\Docs\Shape.docx");

        // 2. Retrieve the first shape
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shapes were found in the document.");
            return;
        }

        // 3. Hide the shape
        shape.Hidden = true;

        // 4. Save the modified document
        doc.Save(@"C:\Docs\ShapeHidden.docx");
        Console.WriteLine("Document saved with the shape hidden.");
    }
}
```

**Verwachte output** wanneer je het programma uitvoert:

```
Document saved with the shape hidden.
```

Open `ShapeHidden.docx` in Microsoft Word; de vorm die oorspronkelijk zichtbaar was, zal nu onzichtbaar zijn.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Wat als het document geen vormen heeft?* | De null‑check in Stap 2 voorkomt een uitzondering en informeert je dat er niets te verbergen is. |
| *Kan ik een vorm verbergen zonder Aspose.Words te gebruiken?* | Ja, je zou de Open XML SDK direct kunnen manipuleren, maar Aspose.Words biedt een hoger‑niveau, minder fout‑gevoelige API. |
| *Heeft het verbergen van een vorm invloed op PDF‑export?* | Wanneer je het gewijzigde document naar PDF exporteert, worden verborgen vormen standaard weggelaten, overeenkomstig de weergave in Word. |
| *Hoe maak ik later een vorm weer zichtbaar?* | Stel `shape.Hidden = false;` in en sla het document opnieuw op. |

## Tips voor productiegebruik

- **License de bibliotheek**: Een niet-gelicentieerde Aspose.Words‑instantie voegt een watermerk toe aan de output. Registreer vroeg in je applicatie een licentie om dit te voorkomen.
- **Prestaties**: Het laden van grote documenten (honderden MB) kan veel geheugen verbruiken. Gebruik `LoadOptions` om alleen de benodigde delen te streamen als je geheugenproblemen ondervindt.
- **Thread‑veiligheid**: `Document`‑objecten zijn niet thread‑veilig. Maak een aparte instantie per thread aan bij het gelijktijdig verwerken van meerdere bestanden.

## Conclusie

Je weet nu **hoe een vorm te verbergen** in een Word‑bestand met C#. De gids behandelde het laden van een document, het vinden van een vorm, het instellen van de `Hidden`‑eigenschap en het opslaan van het resultaat. Je zag ook hoe je de oplossing kunt uitbreiden om meerdere vormen te verbergen en documenten zonder vormen te verwerken.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **hide shape in word** met voorwaardelijke opmaak, of leren hoe je **load Word document c#** vanuit een stream (bijvoorbeeld wanneer het bestand zich in een database of een cloud‑opslagbucket bevindt). Beide concepten bouwen voort op dezelfde Aspose.Words‑API die hier wordt gedemonstreerd.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Voeg een schaduw toe aan Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Groepvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}