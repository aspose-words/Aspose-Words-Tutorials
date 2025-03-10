---
title: Vergelijking granulariteit in Word-document
linktitle: Vergelijking granulariteit in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer de granulariteit van Word-documenten vergelijken met de Aspose.Words voor .NET-functie waarmee documenten teken voor teken kunnen worden vergeleken en de aangebrachte wijzigingen kunnen worden gerapporteerd.
weight: 10
url: /nl/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vergelijking granulariteit in Word-document

Hieronder vindt u een stapsgewijze handleiding om de onderstaande C#-broncode uit te leggen, die gebruikmaakt van de functie Vergelijk granulariteit in Word-documenten van Aspose.Words voor .NET.

## Stap 1: Inleiding

Met de Compare Granularity-functie van Aspose.Words voor .NET kunt u documenten vergelijken op tekenniveau. Dit betekent dat elk teken wordt vergeleken en dat wijzigingen dienovereenkomstig worden gerapporteerd.

## Stap 2: De omgeving instellen

Voordat u begint, moet u uw ontwikkelomgeving instellen om te werken met Aspose.Words voor .NET. Zorg ervoor dat u de Aspose.Words-bibliotheek hebt geïnstalleerd en dat u een geschikt C#-project hebt om de code in te embedden.

## Stap 3: Voeg vereiste samenstellingen toe

Om de Compare Granularity-functie van Aspose.Words voor .NET te gebruiken, moet u de benodigde assembly's aan uw project toevoegen. Zorg ervoor dat u de juiste verwijzingen naar Aspose.Words in uw project hebt.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Stap 4: Documenten maken

In deze stap maken we twee documenten met behulp van de klasse DocumentBuilder. Deze documenten worden gebruikt voor de vergelijking.

```csharp
// Maak document A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Maak document B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Stap 5: Vergelijkingsopties configureren

In deze stap configureren we de vergelijkingsopties om de vergelijkingsgranulariteit te specificeren. Hier gebruiken we granulariteit op tekenniveau.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Stap 6: Documentvergelijking

Laten we nu de documenten vergelijken met behulp van de Compare-methode van de Document-klasse. Wijzigingen worden opgeslagen in document A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 De`Compare`methode vergelijkt document A met document B en slaat de wijzigingen op in document A. U kunt de naam van de auteur en de datum van vergelijking opgeven ter referentie.

## Conclusie

In dit artikel hebben we de Compare Granularity-functie van Aspose.Words voor .NET onderzocht. Met deze functie kunt u documenten vergelijken op tekenniveau en wijzigingen rapporteren. U kunt deze kennis gebruiken om gedetailleerde documentvergelijkingen in uw projecten uit te voeren.

### Voorbeeldbroncode voor vergelijkingsgranulariteit met behulp van Aspose.Words voor .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Conclusie

In deze tutorial hebben we de Comparison Granularity-functie van Aspose.Words voor .NET onderzocht. Met deze functie kunt u het detailniveau opgeven bij het vergelijken van documenten. Door verschillende granulariteitsniveaus te kiezen, kunt u gedetailleerde vergelijkingen uitvoeren op teken-, woord- of blokniveau, afhankelijk van uw specifieke vereisten. Aspose.Words voor .NET biedt een flexibele en krachtige mogelijkheid voor het vergelijken van documenten, waardoor het eenvoudig is om verschillen te identificeren in documenten met verschillende granulariteitsniveaus.

### Veelgestelde vragen

#### V: Wat is het doel van het gebruik van Comparison Granularity in Aspose.Words voor .NET?

A: Comparison Granularity in Aspose.Words voor .NET stelt u in staat om het detailniveau te specificeren bij het vergelijken van documenten. Met deze functie kunt u documenten op verschillende niveaus vergelijken, zoals op tekenniveau, woordniveau of zelfs blokniveau. Elk granulariteitsniveau biedt een ander detailniveau in de vergelijkingsresultaten.

#### V: Hoe gebruik ik vergelijkingsgranulariteit in Aspose.Words voor .NET?

A: Volg deze stappen om Comparison Granularity in Aspose.Words voor .NET te gebruiken:
1. Stel uw ontwikkelomgeving in met de Aspose.Words-bibliotheek.
2. Voeg de benodigde assembly's toe aan uw project door te verwijzen naar Aspose.Words.
3.  Maak de documenten die u wilt vergelijken met behulp van de`DocumentBuilder` klas.
4.  Configureer de vergelijkingsopties door een`CompareOptions` object en het instellen van de`Granularity` eigenschap naar het gewenste niveau (bijv.`Granularity.CharLevel` voor vergelijking op karakterniveau).
5.  Gebruik de`Compare`methode op één document, het andere document doorgeven en de`CompareOptions` object als parameters. Deze methode vergelijkt de documenten op basis van de opgegeven granulariteit en slaat de wijzigingen op in het eerste document.

#### V: Welke niveaus van vergelijkingsgranulariteit zijn beschikbaar in Aspose.Words voor .NET?

A: Aspose.Words voor .NET biedt drie niveaus van vergelijkingsgranulariteit:
- `Granularity.CharLevel`: Vergelijkt documenten op tekenniveau.
- `Granularity.WordLevel`: Vergelijkt documenten op woordniveau.
- `Granularity.BlockLevel`: Vergelijkt documenten op blokniveau.

#### V: Hoe kan ik de vergelijkingsresultaten interpreteren met granulariteit op karakterniveau?

A: Met granulariteit op tekenniveau wordt elk teken in de vergeleken documenten geanalyseerd op verschillen. De vergelijkingsresultaten tonen veranderingen op het individuele tekenniveau, inclusief toevoegingen, verwijderingen en wijzigingen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
