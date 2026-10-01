---
category: general
date: 2026-09-30
description: Vormen groeperen in Word met C# – leer hoe je vormen groepeert, een rechthoek
  en ellips toevoegt, en een rechthoekvorm programmatically in Word‑documenten invoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: nl
lastmod: 2026-09-30
og_description: groepeer vormen in Word met C# en Aspose.Words. Volg deze volledige
  gids om een rechthoek toe te voegen, een ellips toe te voegen, en leer hoe je vormen
  efficiënt kunt groeperen.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Vormen groeperen in Word met C# – stap‑voor‑stap gids
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe vormen te groeperen in Word met C# en Aspose.Words
url: /nl/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Word met C# en Aspose.Words

Als je **vormen in Word** programmatisch wilt **groeperen**, laat deze gids je precies zien hoe. Je ziet hoe je een rechthoek toevoegt, een ellips toevoegt en ze vervolgens combineert tot één groepsvorm met behulp van de Aspose.Words‑bibliotheek voor .NET.

Werken met vormen is een veelvoorkomende eis bij het automatisch genereren van rapporten, contracten of marketingmateriaal. Aan het einde van deze tutorial heb je een herbruikbare C#‑methode die een DOCX‑bestand laadt, een rechthoek en een ellips invoegt, ze groepeert en het resultaat opslaat — zonder Word handmatig te openen.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later geïnstalleerd  
* Een ontwikkelomgeving zoals Visual Studio 2022 (Community‑editie werkt)  
* Een Aspose.Words for .NET‑licentie of een gratis evaluatiekopie (de API werkt zonder licentie maar voegt een watermerk toe)  

Je hebt ook een bron‑Word‑document (`input.docx`) nodig in een map die je vanuit code kunt refereren. Het document kan leeg zijn; de tutorial richt zich op het omgaan met vormen.

## Stap 1: Maak een nieuw console‑project en voeg Aspose.Words toe

Open een terminal of de Visual Studio‑opdrachtprompt en voer uit:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Dit maakt een nieuw console‑applicatieproject genaamd **WordShapeDemo** en voegt het `Aspose.Words`‑NuGet‑pakket toe, dat de `Document`‑ en `DocumentBuilder`‑klassen bevat voor het manipuleren van Word‑bestanden.

## Stap 2: Laad of maak een document

De eerste handeling bij het werken met **groepsvormen in Word** is het verkrijgen van een `Document`‑object. Je kunt een bestaand DOCX‑bestand laden of beginnen met een leeg document.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

De `Document`‑klasse vertegenwoordigt het volledige Word‑bestand. Een bestand laden geeft je een klaar canvas voor het invoegen van vormen.

## Stap 3: Begin een groepsvorm

Een *groepsvorm* laat je meerdere onafhankelijke vormen behandelen als één eenheid — perfect om ze samen te verplaatsen of van grootte te wijzigen. Om een groep te starten, roep je `StartGroupShape()` aan op een `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Het aanroepen van `StartGroupShape` vertelt Aspose.Words dat elke daaropvolgende vorminvoeging tot dezelfde logische groep behoort totdat je `EndGroupShape` aanroept.

## Stap 4: Hoe een rechthoekvorm in Word toe te voegen

Nu de groep geopend is, voeg je een rechthoek in. De `InsertShape`‑methode neemt een `ShapeType`‑enum, gevolgd door de breedte en hoogte (in points).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

De rechthoek wordt het eerste lid van de groep. Je kunt later de vulling, omtrek of tekst aanpassen indien nodig.

## Stap 5: Hoe een ellipsvorm in Word toe te voegen

Vervolgens voeg je een ellips toe (een cirkel wanneer breedte gelijk is aan hoogte). Dit toont **hoe een ellips toe te voegen** met dezelfde builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Beide vormen delen nu dezelfde coördinatenruimte binnen de groep, waardoor ze visueel gemakkelijk uit te lijnen zijn.

## Stap 6: Sluit de definitie van de groepsvorm

Wanneer je alle gewenste leden hebt toegevoegd, sluit je de groep. Dit finaliseert de collectie vormen zodat Word ze als één object behandelt.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Op dit punt bevat het document één gegroepeerde vorm bestaande uit een rechthoek en een ellips.

## Stap 7: Sla het gewijzigde document op

Schrijf tenslotte de wijzigingen terug naar de schijf. Je kunt het originele bestand overschrijven of een nieuw bestand aanmaken.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Het uitvoeren van het programma produceert `output.docx`. Open het bestand in Microsoft Word, selecteer de vorm, en je ziet dat de rechthoek en ellips samen bewegen — bewijs dat de **groepsvormen in Word**‑operatie geslaagd is.

### Verwacht resultaat

* Het Word‑bestand bevat één gegroepeerd object.  
* Het selecteren van de groep laat je zowel de rechthoek als de ellips tegelijk slepen, van grootte wijzigen of roteren.  
* Er is geen handmatige interactie met Word vereist; alles gebeurt via C#‑code.

![Groeperende vormen in Word-document](grouped-shapes.png "Screenshot van een Word-document met een gegroepeerde rechthoek en ellipsvorm")

*Afbeeldingsalt‑tekst: “Screenshot van een Word-document met een gegroepeerde rechthoek en ellipsvorm”* (voldoet aan de vereiste voor alt‑tekst van de afbeelding).

## Waarom groeperen van vormen belangrijk is

Vormen groeperen is meer dan een visueel gemak. Het stelt je in staat om:

* **Lay‑outconsistentie behouden** – het verplaatsen van een groep houdt de relatieve posities intact.  
* **Transformaties één keer toepassen** – roteer of schaal de hele groep in plaats van elke vorm afzonderlijk.  
* **Downstream‑verwerking te vereenvoudigen** – wanneer andere tools de DOCX lezen, zien ze één samengestelde vorm, waardoor de complexiteit afneemt.

Als je later meer vormen wilt toevoegen (bijv. een lijn of een tekstvak) aan dezelfde logische eenheid, hoef je alleen `InsertShape` opnieuw aan te roepen vóór `EndGroupShape`.

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe te behandelen |
|-----------|-----------------|
| **Verschillende eenheden** – je hebt afmetingen in centimeters | Converteer centimeters naar points (`1 cm ≈ 28.35 pt`) voordat je `InsertShape` aanroept. |
| **Een tekstlabel toevoegen** – je wilt een bijschrift binnen de groep | Voeg een `ShapeType.TextBox` toe na de rechthoek en ellips, en stel vervolgens de `Text`‑eigenschap in. |
| **Een vulkleur toepassen** – je hebt een blauwe rechthoek nodig | Na `InsertShape`, haal de laatste vorm op via `builder.CurrentParagraph.Runs[0].Font` en stel `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Een ander documentformaat gebruiken** – je richt je op `.doc` in plaats van `.docx` | Dezelfde code werkt; wijzig alleen de bestandsextensie bij het aanroepen van `Save`. Aspose.Words handelt het formaat automatisch af. |

## Pro‑tips

* **Hergebruik de builder** – je kunt meerdere groepen starten en beëindigen in hetzelfde document; roep gewoon opnieuw `StartGroupShape` aan na `EndGroupShape`.  
* **Prestaties** – het batch‑invoegen van vormen binnen één `StartGroupShape/EndGroupShape`‑blok is sneller dan vormen individueel buiten een groep in te voegen.  
* **Licenties** – een evaluatielicentie voegt een watermerk toe op de eerste pagina. Installeer een juiste licentie om dit in productie‑omgevingen te verwijderen.

## Conclusie

Je weet nu hoe je **vormen in Word** kunt **groeperen** met C#, hoe je een **rechthoek** toevoegt, hoe je een **ellips** toevoegt, en hoe je **rechthoekvormen in Word‑documenten** invoegt met Aspose.Words. Het volledige, uitvoerbare voorbeeld toont elke stap van projectopzet tot het opslaan van het uiteindelijke bestand.

Vanaf hier kun je extra vormtypen verkennen, styling toepassen, of gegroepeerde vormen combineren met tabellen en afbeeldingen om geavanceerde, programmatisch gegenereerde documenten te maken.

---

**Volgende stappen**

* Leer hoe je **gegroepeerde vormen roteert**: gebruik `Shape.RotationAngle` nadat de groep is gesloten.  
* Verken **vul‑ en omtrekaanpassingen** voor rechthoeken en ellipsen.  
* Integreer deze logica in een ASP.NET Core‑API om rapporten on‑demand te genereren.  

Veel programmeerplezier!


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}