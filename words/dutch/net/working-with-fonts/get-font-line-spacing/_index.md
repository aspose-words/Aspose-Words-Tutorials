---
title: Regelafstand lettertype ophalen
linktitle: Regelafstand lettertype ophalen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe je regelafstand in lettertypen krijgt met Aspose.Words voor .NET met deze stapsgewijze tutorial. Perfect voor ontwikkelaars.
weight: 10
url: /nl/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Regelafstand lettertype ophalen

## Invoering

Aspose.Words voor .NET is een krachtige bibliotheek waarmee u Word-documenten programmatisch kunt maken, bewerken en converteren. Een veelvoorkomende taak die u wellicht moet uitvoeren, is het ophalen van de regelafstand van een specifiek lettertype in een document. In deze tutorial leiden we u stap voor stap door het proces, zodat u eenvoudig regelafstand voor lettertypen kunt verkrijgen met Aspose.Words voor .NET. 

## Vereisten

Voordat we in de code duiken, moet u ervoor zorgen dat de volgende vereisten aanwezig zijn:

1.  Aspose.Words voor .NET-bibliotheek: Download en installeer de nieuwste versie van[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u een IDE zoals Visual Studio hebt ingesteld.
3. Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u basiskennis hebt van C#-programmering.

## Naamruimten importeren

Eerst moet u de benodigde namespaces importeren in uw C#-project. Deze namespaces geven u toegang tot de Aspose.Words-functionaliteiten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Laten we het proces voor het instellen van de regelafstand opsplitsen in eenvoudige, beheersbare stappen.

## Stap 1: Maak een nieuw document

De eerste stap is het maken van een nieuw Word-documentexemplaar met Aspose.Words voor .NET.

```csharp
Document doc = new Document();
```

## Stap 2: DocumentBuilder initialiseren

Vervolgens moeten we de`DocumentBuilder` object. Dit object helpt ons bij het construeren en manipuleren van de inhoud van het document.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 3: Stel de lettertype-eigenschappen in

Nu stellen we de lettertype-eigenschappen in voor de tekst die we willen invoegen. Voor dit voorbeeld gebruiken we het lettertype "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## Stap 4: Schrijf tekst naar het document

 Met behulp van de`DocumentBuilder` object, schrijf wat tekst in het document. Deze tekst zal de lettertype-eigenschappen gebruiken die we in de vorige stap hebben ingesteld.

```csharp
builder.Writeln("Sample Text");
```

## Stap 5: Het lettertype-object ophalen

Om de regelafstand te krijgen, moeten we toegang krijgen tot het lettertype-object van de tekst die we zojuist hebben toegevoegd. Dit kan worden gedaan door door de documentstructuur te navigeren naar de eerste alinea-run.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Stap 6: Regelafstand bepalen

Ten slotte halen we de regelafstand op uit het lettertypeobject en printen deze naar de console.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Conclusie

En daar heb je het! Het ophalen van de regelafstand van het lettertype met Aspose.Words voor .NET is eenvoudig wanneer je het opsplitst in deze eenvoudige stappen. Of je nu een nieuw document maakt of met een bestaand document werkt, Aspose.Words biedt alle tools die je nodig hebt om lettertype-eigenschappen efficiënt te beheren.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, bewerken en converteren met behulp van C#.

### Kan ik Aspose.Words voor .NET in andere .NET-talen gebruiken?
Ja, u kunt Aspose.Words voor .NET gebruiken met elke .NET-taal, inclusief VB.NET en F#.

### Hoe kan ik Aspose.Words voor .NET downloaden?
 U kunt de nieuwste versie van Aspose.Words voor .NET downloaden van[hier](https://releases.aspose.com/words/net/).

### Is er een gratis proefversie beschikbaar voor Aspose.Words voor .NET?
 Ja, u kunt een gratis proefversie krijgen van[hier](https://releases.aspose.com/).

### Waar kan ik de documentatie voor Aspose.Words voor .NET vinden?
 De documentatie voor Aspose.Words voor .NET is beschikbaar[hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
